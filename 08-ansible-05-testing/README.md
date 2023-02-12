# Домашнее задание к занятию "5. Тестирование roles"

## Подготовка к выполнению
1. Установите molecule: `pip3 install "molecule==3.5.2"`
```bash
root@bhdevops:/home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse# pip3 install "molecule==3.5.2"
Collecting molecule==3.5.2
  Using cached molecule-3.5.2-py3-none-any.whl (240 kB)
Requirement already satisfied: rich>=9.5.1 in /usr/lib/python3/dist-packages (from molecule==3.5.2) (11.2.0)
Requirement already satisfied: paramiko<3,>=2.5.0 in /usr/local/lib/python3.10/dist-packages (from molecule==3.5.2) (2.12.0)
Requirement already satisfied: packaging in /usr/lib/python3/dist-packages (from molecule==3.5.2) (21.3)
Requirement already satisfied: cookiecutter>=1.7.3 in /usr/local/lib/python3.10/dist-packages (from molecule==3.5.2) (2.1.1)
Requirement already satisfied: ansible-compat>=0.5.0 in /usr/local/lib/python3.10/dist-packages (from molecule==3.5.2) (2.2.6)
Requirement already satisfied: click<9,>=8.0 in /usr/lib/python3/dist-packages (from molecule==3.5.2) (8.0.3)
Requirement already satisfied: enrich>=1.2.5 in /usr/local/lib/python3.10/dist-packages (from molecule==3.5.2) (1.2.7)
Requirement already satisfied: Jinja2>=2.11.3 in /usr/lib/python3/dist-packages (from molecule==3.5.2) (3.0.3)
Requirement already satisfied: cerberus!=1.3.3,!=1.3.4,>=1.3.1 in /usr/local/lib/python3.10/dist-packages (from molecule==3.5.2) (1.3.2)
Requirement already satisfied: pluggy<2.0,>=0.7.1 in /usr/local/lib/python3.10/dist-packages (from molecule==3.5.2) (1.0.0)
Requirement already satisfied: subprocess-tee>=0.3.5 in /usr/local/lib/python3.10/dist-packages (from molecule==3.5.2) (0.4.0)
Requirement already satisfied: selinux in /usr/lib/python3/dist-packages (from molecule==3.5.2) (3.3)
Requirement already satisfied: click-help-colors>=0.9 in /usr/local/lib/python3.10/dist-packages (from molecule==3.5.2) (0.9.1)
Requirement already satisfied: PyYAML<6,>=5.1 in /usr/lib/python3/dist-packages (from molecule==3.5.2) (5.4.1)
Requirement already satisfied: jsonschema>=4.6.0 in /usr/local/lib/python3.10/dist-packages (from ansible-compat>=0.5.0->molecule==3.5.2) (4.17.3)
Requirement already satisfied: setuptools in /usr/lib/python3/dist-packages (from cerberus!=1.3.3,!=1.3.4,>=1.3.1->molecule==3.5.2) (59.6.0)
Requirement already satisfied: requests>=2.23.0 in /usr/lib/python3/dist-packages (from cookiecutter>=1.7.3->molecule==3.5.2) (2.25.1)
Requirement already satisfied: python-slugify>=4.0.0 in /usr/local/lib/python3.10/dist-packages (from cookiecutter>=1.7.3->molecule==3.5.2) (7.0.0)
Requirement already satisfied: jinja2-time>=0.2.0 in /usr/local/lib/python3.10/dist-packages (from cookiecutter>=1.7.3->molecule==3.5.2) (0.2.0)
Requirement already satisfied: binaryornot>=0.4.4 in /usr/local/lib/python3.10/dist-packages (from cookiecutter>=1.7.3->molecule==3.5.2) (0.4.4)
Requirement already satisfied: bcrypt>=3.1.3 in /usr/lib/python3/dist-packages (from paramiko<3,>=2.5.0->molecule==3.5.2) (3.2.0)
Requirement already satisfied: six in /usr/lib/python3/dist-packages (from paramiko<3,>=2.5.0->molecule==3.5.2) (1.16.0)
Requirement already satisfied: cryptography>=2.5 in /usr/lib/python3/dist-packages (from paramiko<3,>=2.5.0->molecule==3.5.2) (3.4.8)
Requirement already satisfied: pynacl>=1.0.1 in /usr/local/lib/python3.10/dist-packages (from paramiko<3,>=2.5.0->molecule==3.5.2) (1.5.0)
Requirement already satisfied: pygments<3.0.0,>=2.6.0 in /usr/lib/python3/dist-packages (from rich>=9.5.1->molecule==3.5.2) (2.11.2)
Requirement already satisfied: commonmark<0.10.0,>=0.9.0 in /usr/lib/python3/dist-packages (from rich>=9.5.1->molecule==3.5.2) (0.9.1)
Requirement already satisfied: colorama<0.5.0,>=0.4.0 in /usr/lib/python3/dist-packages (from rich>=9.5.1->molecule==3.5.2) (0.4.4)
Requirement already satisfied: chardet>=3.0.2 in /usr/lib/python3/dist-packages (from binaryornot>=0.4.4->cookiecutter>=1.7.3->molecule==3.5.2) (4.0.0)
Requirement already satisfied: arrow in /usr/local/lib/python3.10/dist-packages (from jinja2-time>=0.2.0->cookiecutter>=1.7.3->molecule==3.5.2) (1.2.3)
Requirement already satisfied: pyrsistent!=0.17.0,!=0.17.1,!=0.17.2,>=0.14.0 in /usr/lib/python3/dist-packages (from jsonschema>=4.6.0->ansible-compat>=0.5.0->molecule==3.5.2) (0.18.1)
Requirement already satisfied: attrs>=17.4.0 in /usr/lib/python3/dist-packages (from jsonschema>=4.6.0->ansible-compat>=0.5.0->molecule==3.5.2) (21.2.0)
Requirement already satisfied: cffi>=1.4.1 in /usr/local/lib/python3.10/dist-packages (from pynacl>=1.0.1->paramiko<3,>=2.5.0->molecule==3.5.2) (1.15.1)
Requirement already satisfied: text-unidecode>=1.3 in /usr/local/lib/python3.10/dist-packages (from python-slugify>=4.0.0->cookiecutter>=1.7.3->molecule==3.5.2) (1.3)
Requirement already satisfied: pycparser in /usr/local/lib/python3.10/dist-packages (from cffi>=1.4.1->pynacl>=1.0.1->paramiko<3,>=2.5.0->molecule==3.5.2) (2.21)
Requirement already satisfied: python-dateutil>=2.7.0 in /usr/local/lib/python3.10/dist-packages (from arrow->jinja2-time>=0.2.0->cookiecutter>=1.7.3->molecule==3.5.2) (2.8.2)
Installing collected packages: molecule
Successfully installed molecule-3.5.2
```
3. Выполните `docker pull aragast/netology:latest` -  это образ с podman, tox и несколькими пайтонами (3.7 и 3.9) внутри
```bash
root@bhdevops:/home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse# docker pull aragast/netology:latest
latest: Pulling from aragast/netology
Digest: sha256:e44f93d3d9880123ac8170d01bd38ea1cd6c5174832b1782ce8f97f13e695ad5
Status: Image is up to date for aragast/n
```

## Основная часть

Наша основная цель - настроить тестирование наших ролей. Задача: сделать сценарии тестирования для vector. Ожидаемый результат: все сценарии успешно проходят тестирование ролей.

### Molecule

1. Запустите  `molecule test -s centos7` внутри корневой директории clickhouse-role, посмотрите на вывод команды.
```bash
root@bhdevops:/home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse# molecule test -s centos_7
INFO     centos_7 scenario test matrix: dependency, lint, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     Performing prerun...
INFO     Set ANSIBLE_LIBRARY=/root/.cache/ansible-compat/7e099f/modules:/root/.ansible/plugins/modules:/usr/share/ansible/plugins/modules
INFO     Set ANSIBLE_COLLECTIONS_PATH=/root/.cache/ansible-compat/7e099f/collections:/root/.ansible/collections:/usr/share/ansible/collections
INFO     Set ANSIBLE_ROLES_PATH=/root/.cache/ansible-compat/7e099f/roles:/root/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/hosts.yml linked to /root/.cache/molecule/clickhouse/centos_7/inventory/hosts
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/group_vars/ linked to /root/.cache/molecule/clickhouse/centos_7/inventory/group_vars
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/host_vars/ linked to /root/.cache/molecule/clickhouse/centos_7/inventory/host_vars
INFO     Running centos_7 > dependency
WARNING  Skipping, missing the requirements file.
WARNING  Skipping, missing the requirements file.
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/hosts.yml linked to /root/.cache/molecule/clickhouse/centos_7/inventory/hosts
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/group_vars/ linked to /root/.cache/molecule/clickhouse/centos_7/inventory/group_vars
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/host_vars/ linked to /root/.cache/molecule/clickhouse/centos_7/inventory/host_vars
INFO     Running centos_7 > lint
COMMAND: yamllint .
ansible-lint
flake8

WARNING  Loading custom .yamllint config file, this extends our internal yamllint config.
WARNING  Listing 1 violation(s) that are fatal
risky-file-permissions: File permissions unset or incorrect
tasks/install/apt.yml:45 Task/Handler: Hold specified version during APT upgrade | Package installation

You can skip specific rules or tags by adding them to your configuration file:
# .ansible-lint
warn_list:  # or 'skip_list' to silence them completely
  - experimental  # all rules tagged as experimental

Finished with 0 failure(s), 1 warning(s) on 57 files.
/bin/bash: line 3: flake8: command not found
CRITICAL Lint failed with error code 127
WARNING  An error occurred during the test sequence action: 'lint'. Cleaning up.
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/hosts.yml linked to /root/.cache/molecule/clickhouse/centos_7/inventory/hosts
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/group_vars/ linked to /root/.cache/molecule/clickhouse/centos_7/inventory/group_vars
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/host_vars/ linked to /root/.cache/molecule/clickhouse/centos_7/inventory/host_vars
INFO     Running centos_7 > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/hosts.yml linked to /root/.cache/molecule/clickhouse/centos_7/inventory/hosts
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/group_vars/ linked to /root/.cache/molecule/clickhouse/centos_7/inventory/group_vars
INFO     Inventory /home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse/molecule/centos_7/../resources/inventory/host_vars/ linked to /root/.cache/molecule/clickhouse/centos_7/inventory/host_vars
INFO     Running centos_7 > destroy
INFO     Sanity checks: 'docker'

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
changed: [localhost] => (item=centos_7)

TASK [Wait for instance(s) deletion to complete] *******************************
FAILED - RETRYING: Wait for instance(s) deletion to complete (300 retries left).
ok: [localhost] => (item=centos_7)

TASK [Delete docker networks(s)] ***********************************************

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     Pruning extra files from scenario ephemeral directory
root@bhdevops:/home/avdeevan/MNT/mnt-homeworks/08-ansible-03-yandex/playbook/roles/clickhouse# 
```
3. Перейдите в каталог с ролью vector-role и создайте сценарий тестирования по умолчанию при помощи `molecule init scenario --driver-name docker`.
```bash
avdeevan@bhdevops:~/MNT/mnt-homeworks/08-ansible-05-testing/playbook/roles/vector-role$ molecule init scenario --driver-name docker
INFO     Initializing new scenario default...
INFO     Initialized scenario in /home/avdeevan/MNT/mnt-homeworks/08-ansible-05-testing/playbook/roles/vector-role/molecule/default successfully.
avdeevan@bhdevops:~/MNT/mnt-homeworks/08-ansible-05-testing/playbook/roles/vector-role$ 
```
4. Добавьте несколько разных дистрибутивов (centos:8, ubuntu:latest) для инстансов и протестируйте роль, исправьте найденные ошибки, если они есть.
```bash
---
dependency:
  name: galaxy
driver:
  name: docker
platforms:
  - name: instance
    image: docker.io/pycontribs/centos:8
    pre_build_image: true
  - name: host_centos7
    image: docker.io/pycontribs/centos:7
    pre_build_image: false
  - name: host_debian
    image: docker.io/pycontribs/debian:latest
    pre_build_image: false  
provisioner:
  name: ansible
verifier:
  name: ansible
```
```bash
root@bhdevops:/home/avdeevan/MNT/mnt-homeworks/08-ansible-05-testing/playbook/roles/vector-role# molecule test --destroy=never
INFO     default scenario test matrix: dependency, lint, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     Performing prerun...
INFO     Set ANSIBLE_LIBRARY=/root/.cache/ansible-compat/f5bcd7/modules:/root/.ansible/plugins/modules:/usr/share/ansible/plugins/modules
INFO     Set ANSIBLE_COLLECTIONS_PATH=/root/.cache/ansible-compat/f5bcd7/collections:/root/.ansible/collections:/usr/share/ansible/collections
INFO     Set ANSIBLE_ROLES_PATH=/root/.cache/ansible-compat/f5bcd7/roles:/root/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles
INFO     Running default > dependency
WARNING  Skipping, missing the requirements file.
WARNING  Skipping, missing the requirements file.
INFO     Running default > lint
INFO     Lint is disabled.
INFO     Running default > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running default > destroy
WARNING  Skipping, '--destroy=never' requested.
INFO     Running default > syntax
INFO     Sanity checks: 'docker'

playbook: /home/avdeevan/MNT/mnt-homeworks/08-ansible-05-testing/playbook/roles/vector-role/molecule/default/converge.yml
INFO     Running default > create
WARNING  Skipping, instances already created.
INFO     Running default > prepare
WARNING  Skipping, prepare playbook not configured.
INFO     Running default > converge

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
ok: [host_ubuntu]
ok: [instance]

TASK [Include vector-role] *****************************************************

TASK [vector-role : Get vector src] ********************************************
ok: [instance]
ok: [host_ubuntu]

TASK [vector-role : unarchive vector src] **************************************
ok: [instance]
ok: [host_ubuntu]

TASK [vector-role : copy vector to bin] ****************************************
ok: [host_ubuntu]
ok: [instance]

TASK [vector-role : Creates directory] *****************************************
ok: [host_ubuntu]
ok: [instance]

TASK [vector-role : create vector dir] *****************************************
ok: [instance]
ok: [host_ubuntu]

TASK [vector-role : copy vector_cfg from local to remote_src] ******************
ok: [host_ubuntu]
ok: [instance]

TASK [vector-role : install as a service and start] ****************************
ok: [host_ubuntu]
ok: [instance]

PLAY RECAP *********************************************************************
host_ubuntu                : ok=8    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance                   : ok=8    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Running default > idempotence

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
ok: [instance]
ok: [host_ubuntu]

TASK [Include vector-role] *****************************************************

TASK [vector-role : Get vector src] ********************************************
ok: [instance]
ok: [host_ubuntu]

TASK [vector-role : unarchive vector src] **************************************
ok: [host_ubuntu]
ok: [instance]

TASK [vector-role : copy vector to bin] ****************************************
ok: [instance]
ok: [host_ubuntu]

TASK [vector-role : Creates directory] *****************************************
ok: [host_ubuntu]
ok: [instance]

TASK [vector-role : create vector dir] *****************************************
ok: [host_ubuntu]
ok: [instance]

TASK [vector-role : copy vector_cfg from local to remote_src] ******************
ok: [host_ubuntu]
ok: [instance]

TASK [vector-role : install as a service and start] ****************************
ok: [host_ubuntu]
ok: [instance]

PLAY RECAP *********************************************************************
host_ubuntu                : ok=8    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance                   : ok=8    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Idempotence completed successfully.
INFO     Running default > side_effect
WARNING  Skipping, side effect playbook not configured.
INFO     Running default > verify
INFO     Running Ansible Verifier

PLAY [Verify] ******************************************************************

TASK [Example assertion] *******************************************************
ok: [host_ubuntu] => {
    "changed": false,
    "msg": "All assertions passed"
}
ok: [instance] => {
    "changed": false,
    "msg": "All assertions passed"
}

PLAY RECAP *********************************************************************
host_ubuntu                : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance                   : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Verifier completed successfully.
INFO     Running default > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running default > destroy
WARNING  Skipping, '--destroy=never' requested.
root@bhdevops:/home/avdeevan/MNT/mnt-homeworks/08-ansible-05-testing/playbook/roles/vector-role# 
```

5. Добавьте несколько assert'ов в verify.yml файл для  проверки работоспособности vector-role (проверка, что конфиг валидный, проверка успешности запуска, etc). Запустите тестирование роли повторно и проверьте, что оно прошло успешно.
```bash
---
# This is an example playbook to execute Ansible tests.

- name: Verify
  hosts: all
  gather_facts: false
  tasks:
  - name: Example assertion
    assert:
      that: true

  - name: Get Vector version
    ansible.builtin.command: "vector --version"
    changed_when: false
    register: vector_version
  - name: Assert Vector instalation
    assert:
      that: "'{{ vector_version.rc }}' == '0'"
  - name: Validation Vector configuration
    ansible.builtin.command: "vector validate --no-environment --config-yaml /etc/vector/vector.toml"
    changed_when: false
    register: vector_validate
  - name: Assert Vector validate config
    assert:
      that: "'{{ vector_validate.rc }}' == '0'"
```

```bash
PLAY [Verify] ******************************************************************

TASK [Example assertion] *******************************************************
ok: [host_ubuntu] => {
    "changed": false,
    "msg": "All assertions passed"
}
ok: [instance] => {
    "changed": false,
    "msg": "All assertions passed"
}

TASK [Get Vector version] ******************************************************
ok: [host_ubuntu]
ok: [instance]

TASK [Assert Vector instalation] ***********************************************
ok: [host_ubuntu] => {
    "changed": false,
    "msg": "All assertions passed"
}
ok: [instance] => {
    "changed": false,
    "msg": "All assertions passed"
}

TASK [Validation Vector configuration] *****************************************
ok: [host_ubuntu]
ok: [instance]

TASK [Assert Vector validate config] *******************************************
ok: [host_ubuntu] => {
    "changed": false,
    "msg": "All assertions passed"
}
ok: [instance] => {
    "changed": false,
    "msg": "All assertions passed"
}

PLAY RECAP *********************************************************************
host_ubuntu                : ok=5    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance                   : ok=5    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Verifier completed successfully.
INFO     Running default > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running default > destroy
WARNING  Skipping, '--destroy=never' requested.
root@bhdevops:/home/avdeevan/MNT/mnt-homeworks/08-ansible-05-testing/playbook/roles/vector-role# 
```
6. Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.

### Tox

1. Добавьте в директорию с vector-role файлы из [директории](./example)
2. Запустите `docker run --privileged=True -v <path_to_repo>:/opt/vector-role -w /opt/vector-role -it aragast/netology:latest /bin/bash`, где path_to_repo - путь до корня репозитория с vector-role на вашей файловой системе.
3. Внутри контейнера выполните команду `tox`, посмотрите на вывод.
5. Создайте облегчённый сценарий для `molecule` с драйвером `molecule_podman`. Проверьте его на исполнимость.
6. Пропишите правильную команду в `tox.ini` для того чтобы запускался облегчённый сценарий.
8. Запустите команду `tox`. Убедитесь, что всё отработало успешно.
9. Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.

После выполнения у вас должно получится два сценария molecule и один tox.ini файл в репозитории. Ссылка на репозиторий являются ответами на домашнее задание. Не забудьте указать в ответе теги решений Tox и Molecule заданий.

## Необязательная часть

1. Проделайте схожие манипуляции для создания роли lighthouse.
2. Создайте сценарий внутри любой из своих ролей, который умеет поднимать весь стек при помощи всех ролей.
3. Убедитесь в работоспособности своего стека. Создайте отдельный verify.yml, который будет проверять работоспособность интеграции всех инструментов между ними.
4. Выложите свои roles в репозитории. В ответ приведите ссылки.

---

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
