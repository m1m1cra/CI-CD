# Домашнее задание к занятию "3. Использование Yandex Cloud"

## Подготовка к выполнению

1. Подготовьте в Yandex Cloud три хоста: для `clickhouse`, для `vector` и для `lighthouse`.

Ссылка на репозиторий LightHouse: https://github.com/VKCOM/lighthouse

## Основная часть

1. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает lighthouse.
```ansible
---
- name: Install Nginx
  hosts: lighthouse
  handlers:
    - name: start-nginx
      become: true
      command: nginx
    - name: reload-nginx
      become: true
      command: nginx -s reload
  tasks:
    - name: NGINX | Install epel-release
      become: true
      yum:
        name: epel-release
        state: present
    - name: NGINX | Install NGINX
      become: true
      yum:
        name: nginx
        state: present
      notify: start-nginx
    - name: NGINX | Create general config
      become: true
      template:
        src: templates/nginx.conf.j2
        dest: /etc/nginx/nginx.conf
        mode: 0644
      notify: reload-nginx
- name: Install Lighthouse
  hosts: lighthouse
  handlers:
    - name: reload-nginx
      become: true
      command: nginx -s reload
  pre_tasks:
    - name: Lighthouse | install dependencies
      become: true
      yum:
        name: git
        state: present
  tasks:
    - name: Lighthouse | Copy from git
      git:
        repo: "{{ lighthouse_vcs }}"
        version: master
        dest: "{{ lighthouse_location_dir }}"
    - name: lightouse | Create lighthouse config
      become: true
      template:
        src: templates/lighthouse.conf.j2
        dest: /etc/nginx/conf.d/default.conf
        mode: 0644
        notify: reload-nginx
- name: Install Clickhouse
  hosts: clickhouse
  handlers:
    - name: Start clickhouse service
      become: true
      become_method: su
      ansible.builtin.service:
        name: clickhouse-server
        state: restarted
  tasks:
    - block:
        - name: Get clickhouse distrib
          ansible.builtin.get_url:
            url: "https://packages.clickhouse.com/deb/pool/main/c/{{ item }}/{{ item }}_{{ clickhouse_version }}_all.deb"
            dest: "/tmp/{{ item }}_{{ clickhouse_version }}_all_deb"
          with_items: "{{ clickhouse_packages }}"
      rescue:
        - name: Try to get clickhouse distrib
          ansible.builtin.get_url:
            url: "https://packages.clickhouse.com/deb/pool/main/c/clickhouse-common-static/clickhouse-common-static_{{ clickhouse_version }}_amd64.deb"
            dest: "/tmp/clickhouse-common-static_{{ clickhouse_version }}_amd64.deb"
    - name: Install clickhouse packages
      become: true
      apt:
        deb: "{{ item }}"
      with_items:
        - /tmp/clickhouse-common-static_{{ clickhouse_version }}_amd64.deb
        - /tmp/clickhouse-client_{{ clickhouse_version }}_all_deb
        - /tmp/clickhouse-server_{{ clickhouse_version }}_all_deb
      notify: Start clickhouse service
    - name: Create database
      ansible.builtin.command: "clickhouse-client -q 'create database logs;'"
      register: create_db
      failed_when: create_db.rc != 0 and create_db.rc !=82
      changed_when: create_db.rc == 0
- name: Install Vector
```
2. При создании tasks рекомендую использовать модули: `get_url`, `template`, `yum`, `apt`.
#### Ответ
- Использовано
3. Tasks должны: скачать статику lighthouse, установить nginx или любой другой webserver, настроить его конфиг для открытия lighthouse, запустить webserver.

4. Приготовьте свой собственный inventory файл `prod.yml`.
```yaml
---
clickhouse:
  hosts:
    clickhouse-01:
      ansible_host: 51.250.4.150
vector:
  hosts:
    vector-01:
      ansible_host: 51.250.65.104
lighthouse:
  hosts:
    lighthouse-01:
      ansible_host: 62.84.114.237
```
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.
```bash
avdeevan@bhdevops:~/MNT/mnt-homeworks/08-ansible-03-yandex/playbook$ ansible-lint site_tar.yml 
WARNING  Overriding detected file kind 'yaml' with 'playbook' for given positional argument: site_tar.yml
avdeevan@bhdevops:~/MNT/mnt-homeworks/08-ansible-03-yandex/playbook$ 
```
6. Попробуйте запустить playbook на этом окружении с флагом `--check`.
```bash
avdeevan@bhdevops:~/MNT/mnt-homeworks/08-ansible-03-yandex/playbook$ ansible-playbook -i inventory/prod.yml site_tar.yml --check

PLAY [Install Nginx] *******************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

TASK [NGINX | Install epel-release] ****************************************************************************************************************************************************************************************************************************************************************************************
changed: [lighthouse-01]

TASK [NGINX | Install NGINX] ***********************************************************************************************************************************************************************************************************************************************************************************************
fatal: [lighthouse-01]: FAILED! => {"changed": false, "msg": "No package matching 'nginx' found available, installed or updated", "rc": 126, "results": ["No package matching 'nginx' found available, installed or updated"]}

PLAY RECAP *****************************************************************************************************************************************************************************************************************************************************************************************************************
lighthouse-01              : ok=2    changed=1    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0   
```
7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены.
```bash
avdeevan@bhdevops:~/MNT/mnt-homeworks/08-ansible-03-yandex/playbook$ ansible-playbook -i inventory/prod.yml site_tar.yml --diff

PLAY [Install Nginx] *******************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

TASK [NGINX | Install epel-release] ****************************************************************************************************************************************************************************************************************************************************************************************
changed: [lighthouse-01]

TASK [NGINX | Install NGINX] ***********************************************************************************************************************************************************************************************************************************************************************************************
changed: [lighthouse-01]

TASK [NGINX | Create general config] ***************************************************************************************************************************************************************************************************************************************************************************************
--- before: /etc/nginx/nginx.conf
+++ after: /home/avdeevan/.ansible/tmp/ansible-local-1841206c877b2d_/tmpp80niqx6/nginx.conf.j2
@@ -1,84 +1,116 @@
-# For more information on configuration, see:
-#   * Official English Documentation: http://nginx.org/en/docs/
-#   * Official Russian Documentation: http://nginx.org/ru/docs/
+#user  nobody;
+worker_processes  1;
 
-user nginx;
-worker_processes auto;
-error_log /var/log/nginx/error.log;
-pid /run/nginx.pid;
+#error_log  logs/error.log;
+#error_log  logs/error.log  notice;
+#error_log  logs/error.log  info;
 
-# Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
-include /usr/share/nginx/modules/*.conf;
+#pid        logs/nginx.pid;
+
 
 events {
-    worker_connections 1024;
+    worker_connections  1024;
 }
 
+
 http {
-    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
-                      '$status $body_bytes_sent "$http_referer" '
-                      '"$http_user_agent" "$http_x_forwarded_for"';
+    include       mime.types;
+    default_type  application/octet-stream;
 
-    access_log  /var/log/nginx/access.log  main;
+    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
+    #                  '$status $body_bytes_sent "$http_referer" '
+    #                  '"$http_user_agent" "$http_x_forwarded_for"';
 
-    sendfile            on;
-    tcp_nopush          on;
-    tcp_nodelay         on;
-    keepalive_timeout   65;
-    types_hash_max_size 4096;
+    #access_log  logs/access.log  main;
 
-    include             /etc/nginx/mime.types;
-    default_type        application/octet-stream;
+    sendfile        on;
+    #tcp_nopush     on;
 
-    # Load modular configuration files from the /etc/nginx/conf.d directory.
-    # See http://nginx.org/en/docs/ngx_core_module.html#include
-    # for more information.
-    include /etc/nginx/conf.d/*.conf;
+    #keepalive_timeout  0;
+    keepalive_timeout  65;
+
+    #gzip  on;
 
     server {
         listen       80;
-        listen       [::]:80;
-        server_name  _;
-        root         /usr/share/nginx/html;
+        server_name  localhost;
 
-        # Load configuration files for the default server block.
-        include /etc/nginx/default.d/*.conf;
+        #charset koi8-r;
 
-        error_page 404 /404.html;
-        location = /404.html {
+        #access_log  logs/host.access.log  main;
+
+        location / {
+            root   /tmp/lighthouse_src;
+            index  index.html index.htm;
         }
 
-        error_page 500 502 503 504 /50x.html;
+        #error_page  404              /404.html;
+
+        # redirect server error pages to the static page /50x.html
+        #
+        error_page   500 502 503 504  /50x.html;
         location = /50x.html {
+            root   html;
         }
+
+        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
+        #
+        #location ~ \.php$ {
+        #    proxy_pass   http://127.0.0.1;
+        #}
+
+        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
+        #
+        #location ~ \.php$ {
+        #    root           html;
+        #    fastcgi_pass   127.0.0.1:9000;
+        #    fastcgi_index  index.php;
+        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
+        #    include        fastcgi_params;
+        #}
+
+        # deny access to .htaccess files, if Apache's document root
+        # concurs with nginx's one
+        #
+        #location ~ /\.ht {
+        #    deny  all;
+        #}
     }
 
-# Settings for a TLS enabled server.
-#
-#    server {
-#        listen       443 ssl http2;
-#        listen       [::]:443 ssl http2;
-#        server_name  _;
-#        root         /usr/share/nginx/html;
-#
-#        ssl_certificate "/etc/pki/nginx/server.crt";
-#        ssl_certificate_key "/etc/pki/nginx/private/server.key";
-#        ssl_session_cache shared:SSL:1m;
-#        ssl_session_timeout  10m;
-#        ssl_ciphers HIGH:!aNULL:!MD5;
-#        ssl_prefer_server_ciphers on;
-#
-#        # Load configuration files for the default server block.
-#        include /etc/nginx/default.d/*.conf;
-#
-#        error_page 404 /404.html;
-#            location = /40x.html {
-#        }
-#
-#        error_page 500 502 503 504 /50x.html;
-#            location = /50x.html {
-#        }
-#    }
+
+    # another virtual host using mix of IP-, name-, and port-based configuration
+    #
+    #server {
+    #    listen       8000;
+    #    listen       somename:8080;
+    #    server_name  somename  alias  another.alias;
+
+    #    location / {
+    #        root   html;
+    #        index  index.html index.htm;
+    #    }
+    #}
+
+
+    # HTTPS server
+    #
+    #server {
+    #    listen       443 ssl;
+    #    server_name  localhost;
+
+    #    ssl_certificate      cert.pem;
+    #    ssl_certificate_key  cert.key;
+
+    #    ssl_session_cache    shared:SSL:1m;
+    #    ssl_session_timeout  5m;
+
+    #    ssl_ciphers  HIGH:!aNULL:!MD5;
+    #    ssl_prefer_server_ciphers  on;
+
+    #    location / {
+    #        root   html;
+    #        index  index.html index.htm;
+    #    }
+    #}
 
 }
-

changed: [lighthouse-01]

RUNNING HANDLER [start-nginx] **********************************************************************************************************************************************************************************************************************************************************************************************
changed: [lighthouse-01]

RUNNING HANDLER [reload-nginx] *********************************************************************************************************************************************************************************************************************************************************************************************
changed: [lighthouse-01]

PLAY [Install Lighthouse] **************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

TASK [Lighthouse | install dependencies] ***********************************************************************************************************************************************************************************************************************************************************************************
changed: [lighthouse-01]

TASK [Lighthouse | Copy from git] ******************************************************************************************************************************************************************************************************************************************************************************************
>> Newly checked out d701335c25cd1bb9b5155711190bad8ab852c2ce
changed: [lighthouse-01]

TASK [lightouse | Create lighthouse config] ********************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

PLAY [Install Clickhouse] **************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************
The authenticity of host '51.250.0.138 (51.250.0.138)' can't be established.
ED25519 key fingerprint is SHA256:UV5EDnkaO/Ji+3UqP8Dl/vLvTfD2uDPqwWDu2svD15w.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
ok: [clickhouse-01]

TASK [Get clickhouse distrib] **********************************************************************************************************************************************************************************************************************************************************************************************
changed: [clickhouse-01] => (item=clickhouse-client)
changed: [clickhouse-01] => (item=clickhouse-server)
failed: [clickhouse-01] (item=clickhouse-common-static) => {"ansible_loop_var": "item", "changed": false, "dest": "/tmp/clickhouse-common-static_22.3.3.44_all_deb", "elapsed": 0, "item": "clickhouse-common-static", "msg": "Request failed", "response": "HTTP Error 404: Not Found", "status_code": 404, "url": "https://packages.clickhouse.com/deb/pool/main/c/clickhouse-common-static/clickhouse-common-static_22.3.3.44_all.deb"}

TASK [Try to get clickhouse distrib] ***************************************************************************************************************************************************************************************************************************************************************************************
changed: [clickhouse-01]

TASK [Install clickhouse packages] *****************************************************************************************************************************************************************************************************************************************************************************************
Selecting previously unselected package clickhouse-common-static.
(Reading database ... 29591 files and directories currently installed.)
Preparing to unpack .../clickhouse-common-static_22.3.3.44_amd64.deb ...
Unpacking clickhouse-common-static (22.3.3.44) ...
Setting up clickhouse-common-static (22.3.3.44) ...
changed: [clickhouse-01] => (item=/tmp/clickhouse-common-static_22.3.3.44_amd64.deb)
Selecting previously unselected package clickhouse-client.
(Reading database ... 29605 files and directories currently installed.)
Preparing to unpack .../clickhouse-client_22.3.3.44_all_deb ...
Unpacking clickhouse-client (22.3.3.44) ...
Setting up clickhouse-client (22.3.3.44) ...
changed: [clickhouse-01] => (item=/tmp/clickhouse-client_22.3.3.44_all_deb)
Selecting previously unselected package clickhouse-server.
(Reading database ... 29618 files and directories currently installed.)
Preparing to unpack .../clickhouse-server_22.3.3.44_all_deb ...
Unpacking clickhouse-server (22.3.3.44) ...
Setting up clickhouse-server (22.3.3.44) ...
changed: [clickhouse-01] => (item=/tmp/clickhouse-server_22.3.3.44_all_deb)

TASK [Start_clickhouse_svc] ************************************************************************************************************************************************************************************************************************************************************************************************
changed: [clickhouse-01]

TASK [Create database] *****************************************************************************************************************************************************************************************************************************************************************************************************
changed: [clickhouse-01]

PLAY [Install Vector] ******************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************
The authenticity of host '84.201.132.241 (84.201.132.241)' can't be established.
ED25519 key fingerprint is SHA256:0fvm0ikxVp/H7iRysQaXJwjLAB65awzIz9oJ73xCf/A.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
ok: [vector-01]

TASK [Get vector src] ******************************************************************************************************************************************************************************************************************************************************************************************************
changed: [vector-01]

TASK [unarchive vector src] ************************************************************************************************************************************************************************************************************************************************************************************************
changed: [vector-01]

TASK [copy vector to bin] **************************************************************************************************************************************************************************************************************************************************************************************************
changed: [vector-01]

TASK [create vector dir] ***************************************************************************************************************************************************************************************************************************************************************************************************
--- before
+++ after
@@ -1,5 +1,5 @@
 {
-    "mode": "0755",
+    "mode": "0644",
     "path": "/etc/vector",
-    "state": "absent"
+    "state": "directory"
 }

changed: [vector-01]

TASK [copy vector_cfg from local to remote_src] ****************************************************************************************************************************************************************************************************************************************************************************
--- before
+++ after: /home/avdeevan/.ansible/tmp/ansible-local-1841206c877b2d_/tmpyzzqe50b/vector.toml.j2
@@ -0,0 +1,44 @@
+#                                    __   __  __
+#                                    \ \ / / / /
+#                                     \ V / / /
+#                                      \_/  \/
+#
+#                                    V E C T O R
+#                                   Configuration
+#
+# ------------------------------------------------------------------------------
+# Website: https://vector.dev
+# Docs: https://vector.dev/docs
+# Chat: https://chat.vector.dev
+# ------------------------------------------------------------------------------
+
+# Change this to use a non-default directory for Vector data storage:
+data_dir = "/var/lib/vector"
+
+# Random Syslog-formatted logs
+[sources.dummy_logs]
+type = "demo_logs"
+format = "syslog"
+interval = 1
+
+# Parse Syslog logs
+# See the Vector Remap Language reference for more info: https://vrl.dev
+[transforms.parse_logs]
+type = "remap"
+inputs = ["dummy_logs"]
+source = '''
+. = parse_syslog!(string!(.message))
+'''
+
+# Print parsed logs to stdout
+[sinks.print]
+type = "console"
+inputs = ["parse_logs"]
+encoding.codec = "json"
+
+# Vector's GraphQL API (disabled by default)
+# Uncomment to try it out with the `vector top` command or
+# in your browser at http://localhost:8686
+#[api]
+#enabled = true
+#address = "127.0.0.1:8686"

changed: [vector-01]

TASK [install as a service and restart] ************************************************************************************************************************************************************************************************************************************************************************************
changed: [vector-01]

RUNNING HANDLER [Restart vector service] ***********************************************************************************************************************************************************************************************************************************************************************************
fatal: [vector-01]: FAILED! => {"changed": false, "msg": "Unable to start service vector: Job for vector.service failed because the control process exited with error code. See \"systemctl status vector.service\" and \"journalctl -xe\" for details.\n"}

NO MORE HOSTS LEFT *********************************************************************************************************************************************************************************************************************************************************************************************************

PLAY RECAP *****************************************************************************************************************************************************************************************************************************************************************************************************************
clickhouse-01              : ok=5    changed=4    unreachable=0    failed=0    skipped=0    rescued=1    ignored=0   
lighthouse-01              : ok=10   changed=7    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
vector-01                  : ok=7    changed=6    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0   

avdeevan@bhdevops:~/MNT/mnt-homeworks/08-ansible-03-yandex/playbook$ 
```
8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен.
```bash
avdeevan@bhdevops:~/MNT/mnt-homeworks/08-ansible-03-yandex/playbook$ ansible-playbook -i inventory/prod.yml site_tar.yml --diff

PLAY [Install Nginx] *******************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

TASK [NGINX | Install epel-release] ****************************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

TASK [NGINX | Install NGINX] ***********************************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

TASK [NGINX | Create general config] ***************************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

PLAY [Install Lighthouse] **************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

TASK [Lighthouse | install dependencies] ***********************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

TASK [Lighthouse | Copy from git] ******************************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

TASK [lightouse | Create lighthouse config] ********************************************************************************************************************************************************************************************************************************************************************************
ok: [lighthouse-01]

PLAY [Install Clickhouse] **************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************
ok: [clickhouse-01]

TASK [Get clickhouse distrib] **********************************************************************************************************************************************************************************************************************************************************************************************
ok: [clickhouse-01] => (item=clickhouse-client)
ok: [clickhouse-01] => (item=clickhouse-server)
failed: [clickhouse-01] (item=clickhouse-common-static) => {"ansible_loop_var": "item", "changed": false, "dest": "/tmp/clickhouse-common-static_22.3.3.44_all_deb", "elapsed": 0, "item": "clickhouse-common-static", "msg": "Request failed", "response": "HTTP Error 404: Not Found", "status_code": 404, "url": "https://packages.clickhouse.com/deb/pool/main/c/clickhouse-common-static/clickhouse-common-static_22.3.3.44_all.deb"}

TASK [Try to get clickhouse distrib] ***************************************************************************************************************************************************************************************************************************************************************************************
ok: [clickhouse-01]

TASK [Install clickhouse packages] *****************************************************************************************************************************************************************************************************************************************************************************************
ok: [clickhouse-01] => (item=/tmp/clickhouse-common-static_22.3.3.44_amd64.deb)
ok: [clickhouse-01] => (item=/tmp/clickhouse-client_22.3.3.44_all_deb)
ok: [clickhouse-01] => (item=/tmp/clickhouse-server_22.3.3.44_all_deb)

TASK [Create database] *****************************************************************************************************************************************************************************************************************************************************************************************************
ok: [clickhouse-01]

PLAY [Install Vector] ******************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************
ok: [vector-01]

TASK [Get vector src] ******************************************************************************************************************************************************************************************************************************************************************************************************
ok: [vector-01]

TASK [unarchive vector src] ************************************************************************************************************************************************************************************************************************************************************************************************
ok: [vector-01]

TASK [copy vector to bin] **************************************************************************************************************************************************************************************************************************************************************************************************
ok: [vector-01]

TASK [create vector dir] ***************************************************************************************************************************************************************************************************************************************************************************************************
ok: [vector-01]

TASK [copy vector_cfg from local to remote_src] ****************************************************************************************************************************************************************************************************************************************************************************
ok: [vector-01]

TASK [install as a service and restart] ************************************************************************************************************************************************************************************************************************************************************************************
ok: [vector-01]

PLAY RECAP *****************************************************************************************************************************************************************************************************************************************************************************************************************
clickhouse-01              : ok=4    changed=0    unreachable=0    failed=0    skipped=0    rescued=1    ignored=0   
lighthouse-01              : ok=8    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
vector-01                  : ok=7    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

avdeevan@bhdevops:~/MNT/mnt-homeworks/08-ansible-03-yandex/playbook$ 
```
9. Подготовьте README.md файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги.
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-03-yandex` на фиксирующий коммит, в ответ предоставьте ссылку на него.

---

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
