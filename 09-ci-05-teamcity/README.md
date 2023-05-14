# Домашнее задание к занятию "11.Teamcity"

## Подготовка к выполнению

1. В Ya.Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`
2. Дождитесь запуска teamcity, выполните первоначальную настройку
3. Создайте ещё один инстанс(2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`
4. Авторизуйте агент
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity)
6. Создать VM (2CPU4RAM) и запустить [playbook](./infrastructure)

## Основная часть

1. Создайте новый проект в teamcity на основе fork
2. Сделайте autodetect конфигурации
3. Сохраните необходимые шаги, запустите первую сборку master'a
![screen](tmp/builds.png)

<details>
   
<summary>Build log</summary>
  
  ```bash
  Build 'netology / Build' #1, default branch 'master'
Triggered 2023-05-13 12:36:13 by 'admin'
Started 2023-05-13 12:36:15 on agent 'ip_51.250.84.148'
Finished 2023-05-13 12:36:46 with status NORMAL 'Tests passed: 5'
VCS revisions: 'Netology_HttpsGithubComM1m1craExampleTeamcityGitRefsHeadsMaster' (Git, instance id 1): 'db1c910a3f0442d9a9b9c3411db8c9c298019bf1' (branch: 'refs/heads/master')
TeamCity URL http://localhost:8111/viewLog.html?buildId=1&buildTypeId=Netology_Build 
TeamCity server version is 2022.10.3 (build 117072), server timezone: GMT (UTC)

[12:36:13]W: bt1 (33s)
[12:36:13]i: TeamCity server version is 2022.10.3 (build 117072)
[12:36:13] : The build is removed from the queue to be prepared for the start
[12:36:13] : Collecting changes in 1 VCS root
[12:36:13] :	 [Collecting changes in 1 VCS root] VCS Root details
[12:36:13] :		 [VCS Root details] "https://github.com/m1m1cra/example-teamcity.git#refs/heads/master" {instance id=1, parent internal id=1, parent id=Netology_HttpsGithubComM1m1craExampleTeamcityGitRefsHeadsMaster, description: "https://github.com/m1m1cra/example-teamcity.git#refs/heads/master"}
[12:36:14]i:	 [Collecting changes in 1 VCS root] Loading current repository state for VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'
[12:36:14]i:		 [Loading current repository state for VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': git -c core.askpass=/opt/teamcity/temp/pass9262256014903860034 -c credential.helper= ls-remote origin
[12:36:14]i:	 [Collecting changes in 1 VCS root] Detecting changes in VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master' (used in 'Build')
[12:36:14]i:	 [Collecting changes in 1 VCS root] Will collect changes for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master' starting from revision db1c910a3f0442d9a9b9c3411db8c9c298019bf1
[12:36:14] :	 [Collecting changes in 1 VCS root] Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'
[12:36:14] :		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] Upper limit revision: db1c910a3f0442d9a9b9c3411db8c9c298019bf1
[12:36:14]i:		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] MaxModId = null
[12:36:14] :		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] The first revision that was detected in the branch refs/heads/master: db1c910a3f0442d9a9b9c3411db8c9c298019bf1
[12:36:14] :		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] Cannot find modification in TeamCity database with revision db1c910a3f0442d9a9b9c3411db8c9c298019bf1
[12:36:14] :		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] Computed revision: db1c910a3f0442d9a9b9c3411db8c9c298019bf1
[12:36:14] : Starting the build on the agent "ip_51.250.84.148"
[12:36:15]i: Agent time zone: Europe/London
[12:36:15]i: Agent is running under JRE: 11.0.16.1+9-LTS
[12:36:15] : Updating tools for build
[12:36:15] :	 [Updating tools for build] Found 1 tool used by the build: maven3_6
[12:36:16] :	 [Updating tools for build] Tool maven3_6 updated successfully
[12:36:16]i: Preparing performance monitoring data directory: /opt/buildagent/system/perfmon
[12:36:16]i: Performance monitor is using command line: [perl, /opt/buildagent/system/perfmon/scripts/vmstatlinux.pl, /opt/buildagent/system/perfmon/temp/1/perfmon.csv, 1000]
[12:36:16]i: Starting performance monitoring process
[12:36:16]i: Performance monitoring process started
[12:36:16] : Clearing temporary directory: /opt/buildagent/temp/buildTmp
[12:36:16] : Publishing internal artifacts
[12:36:16] :	 [Publishing internal artifacts] Publishing 1 file using [WebPublisher]
[12:36:16] :	 [Publishing internal artifacts] Publishing 1 file using [ArtifactsCachePublisherImpl]
[12:36:16]i:	 [Publishing internal artifacts] Will publish 1 artifact(s) to TeamCity node with id MAIN_SERVER
[12:36:16] : Full checkout enforced. Reason: [Checkout directory is empty or doesn't exist]
[12:36:16] : Will perform clean checkout. Reason: Checkout directory is empty or doesn't exist
[12:36:16] : Checkout directory: /opt/buildagent/work/74efd952ef63049f
[12:36:16] : Updating sources: auto checkout (on agent) (6s)
[12:36:16] :	 [Updating sources] Will use agent side checkout
[12:36:16] :	 [Updating sources] VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master (6s)
[12:36:16] :		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] revision: db1c910a3f0442d9a9b9c3411db8c9c298019bf1
[12:36:16]i:		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] Mirrors automatically enabled
[12:36:16] :		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] Git version: 2.40.0.0
[12:36:16] :		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git) (4s)
[12:36:16] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git init --bare --initial-branch=main
[12:36:19] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git config http.sslCAInfo
[12:36:19] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] Local clone state requires 'git fetch'.
[12:36:19] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Enumerating objects: 343, done.        
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Counting objects: 100% (1/1)        
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Counting objects: 100% (1/1), done.        
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   0% (1/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   1% (4/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   2% (7/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   3% (11/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   4% (14/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   5% (18/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   6% (21/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   7% (25/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   8% (28/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:   9% (31/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  10% (35/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  11% (38/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  12% (42/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  13% (45/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  14% (49/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  15% (52/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  16% (55/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  17% (59/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  18% (62/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  19% (66/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  20% (69/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  21% (73/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  22% (76/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  23% (79/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  24% (83/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  25% (86/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  26% (90/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  27% (93/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  28% (97/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  29% (100/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  30% (103/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  31% (107/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  32% (110/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  33% (114/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  34% (117/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  35% (121/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  36% (124/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  37% (127/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  38% (131/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  39% (134/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  40% (138/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  41% (141/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  42% (145/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  43% (148/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  44% (151/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  45% (155/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  46% (158/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  47% (162/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  48% (165/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  49% (169/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  50% (172/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  51% (175/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  52% (179/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  53% (182/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  54% (186/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  55% (189/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  56% (193/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  57% (196/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  58% (199/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  59% (203/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  60% (206/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  61% (210/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  62% (213/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  63% (217/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  64% (220/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  65% (223/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  66% (227/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  67% (230/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  68% (234/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  69% (237/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  70% (241/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  71% (244/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  72% (247/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  73% (251/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  74% (254/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  75% (258/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  76% (261/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  77% (265/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  78% (268/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  79% (271/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Total 343 (delta 0), reused 1 (delta 0), pack-reused 342        
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  80% (275/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  81% (278/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  82% (282/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  83% (285/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  84% (289/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  85% (292/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  86% (295/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  87% (299/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  88% (302/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  89% (306/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  90% (309/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  91% (313/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  92% (316/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  93% (319/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  94% (323/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  95% (326/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  96% (330/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  97% (333/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  98% (337/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects:  99% (340/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects: 100% (343/343)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Receiving objects: 100% (343/343), 49.71 KiB | 598.00 KiB/s, done.
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   0% (0/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   1% (2/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   2% (3/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   3% (4/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   4% (5/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   5% (6/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   6% (7/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   7% (8/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   8% (9/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:   9% (11/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  10% (12/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  11% (13/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  12% (14/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  13% (15/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  14% (16/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  15% (17/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  16% (18/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  17% (20/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  18% (21/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  19% (22/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  20% (23/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  21% (24/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  22% (25/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  23% (26/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  24% (27/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  25% (28/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  26% (30/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  27% (31/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  28% (32/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  29% (33/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  30% (34/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  31% (35/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  32% (36/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  33% (37/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  34% (39/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  35% (40/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  36% (41/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  37% (42/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  38% (43/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  39% (44/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  40% (45/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  41% (46/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  42% (48/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  43% (49/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  44% (50/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  45% (51/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  46% (52/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  47% (53/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  48% (54/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  49% (55/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  50% (56/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  51% (58/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  52% (59/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  53% (60/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  54% (61/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  55% (62/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  56% (63/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  57% (64/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  58% (65/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  59% (67/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  60% (68/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  61% (69/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  62% (70/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  63% (71/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  64% (72/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  65% (73/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  66% (74/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  67% (76/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  69% (78/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  70% (79/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  71% (80/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  72% (81/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  73% (82/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  74% (83/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  75% (84/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  76% (86/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  77% (87/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  78% (88/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  79% (89/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  80% (90/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  81% (91/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  82% (92/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  83% (93/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  84% (95/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  85% (96/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  86% (97/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  87% (98/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  88% (99/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  89% (100/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  90% (101/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  91% (102/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  92% (104/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  93% (105/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  94% (106/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  95% (107/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  96% (108/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  97% (109/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  98% (110/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas:  99% (111/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas: 100% (112/112)
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] Resolving deltas: 100% (112/112), done.
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] From https://github.com/m1m1cra/example-teamcity
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master]  * [new branch]      master     -> master
[12:36:20]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass10862328650951246780 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master]  * [new branch]      master     -> origin/master
[12:36:20] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git log -n1 --pretty=format:%H%x20%s db1c910a3f0442d9a9b9c3411db8c9c298019bf1 --
[12:36:20] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git pack-refs --all
[12:36:20] :		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] Update checkout directory (/opt/buildagent/work/74efd952ef63049f) (2s)
[12:36:20] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] The .git directory is missing in '/opt/buildagent/work/74efd952ef63049f'. Running 'git init'...
[12:36:20] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git init --initial-branch=main
[12:36:22] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git config lfs.storage /opt/buildagent/system/git/git-BA3EC828.git/lfs
[12:36:22] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git config core.sparseCheckout true
[12:36:22] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git config http.sslCAInfo
[12:36:22] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git show-ref
[12:36:22] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass144224950281853271 -c credential.helper= ls-remote origin
[12:36:23] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git show-ref refs/remotes/origin/master
[12:36:23] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git log -n1 --pretty=format:%H%x20%s db1c910a3f0442d9a9b9c3411db8c9c298019bf1 --
[12:36:23] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] No 'git fetch' required: commit 'db1c910a3f0442d9a9b9c3411db8c9c298019bf1' is in the local repository clone pointed by 'refs/remotes/origin/master'.
[12:36:23] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git branch
[12:36:23] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git update-ref refs/heads/master db1c910a3f0442d9a9b9c3411db8c9c298019bf1
[12:36:23] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass2715766882911106117 -c credential.helper= -c credential.helper=/opt/buildagent/temp/buildTmp/credHelper6473161251368999829.sh checkout -q -f master
[12:36:23] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git branch --set-upstream-to=refs/remotes/origin/master
[12:36:23] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] Cleaning https://github.com/m1m1cra/example-teamcity.git#refs/heads/master in /opt/buildagent/work/74efd952ef63049f the file set ALL_UNTRACKED
[12:36:23] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git clean -f -d -x
[12:36:23] : Build preparation done
[12:36:23]W: Step 1/1: Maven (18s)
[12:36:23] :	 [Step 1/1] Initial M2_HOME not set
[12:36:23] :	 [Step 1/1] Current M2_HOME = /opt/buildagent/tools/maven3_6
[12:36:23] :	 [Step 1/1] PATH = /opt/buildagent/tools/maven3_6/bin:/opt/java/openjdk/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
[12:36:23] :	 [Step 1/1] Using watcher: /opt/buildagent/plugins/mavenPlugin/maven-watcher-jdk17/maven-watcher-agent.jar
[12:36:23] :	 [Step 1/1] Using agent local repository at /opt/buildagent/system/jetbrains.maven.runner/maven.repo.local
[12:36:23] :	 [Step 1/1] *** Start reading the project structure ***
[12:36:23]i:	 [Step 1/1] Initial MAVEN_OPTS not set
[12:36:23]i:	 [Step 1/1] Current MAVEN_OPTS not set
[12:36:24]i:	 [Step 1/1] [INFO] Scanning for projects...
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/info-maven3-plugin/1.0.3/info-maven3-plugin-1.0.3.pom
[12:36:25]i:	 [Step 1/1] [INFO] Downloaded from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/info-maven3-plugin/1.0.3/info-maven3-plugin-1.0.3.pom (367 B at 20 kB/s)
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/info-maven3-plugin/1.0.3/info-maven3-plugin-1.0.3.jar
[12:36:25]i:	 [Step 1/1] [INFO] Downloaded from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/info-maven3-plugin/1.0.3/info-maven3-plugin-1.0.3.jar (9.9 kB at 2.0 MB/s)
[12:36:25]i:	 [Step 1/1] [INFO] 
[12:36:25]i:	 [Step 1/1] [INFO] -----------------------< org.netology:plaindoll >-----------------------
[12:36:25]i:	 [Step 1/1] [INFO] Building plaindoll 0.0.2
[12:36:25]i:	 [Step 1/1] [INFO] --------------------------------[ jar ]---------------------------------
[12:36:25]i:	 [Step 1/1] [INFO] 
[12:36:25]i:	 [Step 1/1] [INFO] --- info-maven3-plugin:1.0.3:info (default-cli) @ plaindoll ---
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/maven-embedder-api/1.2.4/maven-embedder-api-1.2.4.pom
[12:36:25]i:	 [Step 1/1] [INFO] Downloaded from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/maven-embedder-api/1.2.4/maven-embedder-api-1.2.4.pom (488 B at 244 kB/s)
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xerces/xercesImpl/2.12.2/xercesImpl-2.12.2.pom
[12:36:25]i:	 [Step 1/1] [INFO] Downloaded from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xerces/xercesImpl/2.12.2/xercesImpl-2.12.2.pom (170 B at 85 kB/s)
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xml-apis/xml-apis/1.4.01/xml-apis-1.4.01.pom
[12:36:25]i:	 [Step 1/1] [INFO] Downloaded from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xml-apis/xml-apis/1.4.01/xml-apis-1.4.01.pom (170 B at 85 kB/s)
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/maven-embedder-api/1.2.4/maven-embedder-api-1.2.4.jar
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xerces/xercesImpl/2.12.2/xercesImpl-2.12.2.jar
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/codehaus/plexus/plexus-utils/1.1/plexus-utils-1.1.jar
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xml-apis/xml-apis/1.4.01/xml-apis-1.4.01.jar
[12:36:25]i:	 [Step 1/1] [INFO] Downloaded from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/maven-embedder-api/1.2.4/maven-embedder-api-1.2.4.jar (33 kB at 2.3 MB/s)
[12:36:25]i:	 [Step 1/1] [INFO] Downloaded from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xml-apis/xml-apis/1.4.01/xml-apis-1.4.01.jar (221 kB at 5.3 MB/s)
[12:36:25]i:	 [Step 1/1] [INFO] Downloaded from teamcity_local_32a8877d-e011-45a3-85dd-77638234f8fd: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xerces/xercesImpl/2.12.2/xercesImpl-2.12.2.jar (1.4 MB at 27 MB/s)
[12:36:25]i:	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.1/plexus-utils-1.1.jar
[12:36:25]i:	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.1/plexus-utils-1.1.jar (169 kB at 372 kB/s)
[12:36:26]i:	 [Step 1/1] [INFO] ------------------------------------------------------------------------
[12:36:26]i:	 [Step 1/1] [INFO] BUILD SUCCESS
[12:36:26]i:	 [Step 1/1] [INFO] ------------------------------------------------------------------------
[12:36:26]i:	 [Step 1/1] [INFO] Total time:  1.126 s
[12:36:26]i:	 [Step 1/1] [INFO] Finished at: 2023-05-13T13:36:26+01:00
[12:36:26]i:	 [Step 1/1] [INFO] ------------------------------------------------------------------------
[12:36:26]i:	 [Step 1/1] Process exited with code 0
[12:36:26] :	 [Step 1/1] Initial MAVEN_OPTS not set
[12:36:26] :	 [Step 1/1] Current MAVEN_OPTS not set
[12:36:26] :	 [Step 1/1] Starting: /opt/java/openjdk/bin/java -Dagent.home.dir=/opt/buildagent -Dagent.name=ip_51.250.84.148 -Dagent.ownPort=9090 -Dagent.work.dir=/opt/buildagent/work -Dbuild.number=1 -Dbuild.vcs.number=db1c910a3f0442d9a9b9c3411db8c9c298019bf1 -Dbuild.vcs.number.1=db1c910a3f0442d9a9b9c3411db8c9c298019bf1 -Dbuild.vcs.number.Netology_HttpsGithubComM1m1craExampleTeamcityGitRefsHeadsMaster=db1c910a3f0442d9a9b9c3411db8c9c298019bf1 -Dclassworlds.conf=/opt/buildagent/temp/buildTmp/teamcity.m2.conf -Dcom.jetbrains.maven.watcher.report.file=/opt/buildagent/temp/buildTmp/maven-build-info.xml -Dec2.instance-id=fhmvgsh7ajdb2sca9lg8 -Dec2.local-hostname=teamcity-agent.ru-central1.internal -Dec2.local-ipv4=10.128.0.3 -Dec2.public-hostname=51.250.84.148 -Dec2.public-ipv4=51.250.84.148 -Djava.io.tmpdir=/opt/buildagent/temp/buildTmp -Dmaven.home=/opt/buildagent/tools/maven3_6 -Dmaven.multiModuleProjectDirectory=/opt/buildagent/work/74efd952ef63049f -Dteamcity.agent.cpuBenchmark=527 -Dteamcity.agent.dotnet.agent_url=http://localhost:9090/RPC2 -Dteamcity.agent.dotnet.build_id=1 -Dteamcity.auth.password=******* -Dteamcity.auth.userId=TeamCityBuildId=1 -Dteamcity.build.changedFiles.file=/opt/buildagent/temp/buildTmp/teamcity.changedFiles.txt -Dteamcity.build.checkoutDir=/opt/buildagent/work/74efd952ef63049f -Dteamcity.build.id=1 -Dteamcity.build.properties.file=/opt/buildagent/temp/buildTmp/teamcity.build.parameters -Dteamcity.build.tempDir=/opt/buildagent/temp/buildTmp -Dteamcity.build.workingDir=/opt/buildagent/work/74efd952ef63049f -Dteamcity.buildConfName=Build -Dteamcity.buildType.id=Netology_Build -Dteamcity.configuration.properties.file=/opt/buildagent/temp/buildTmp/teamcity.config.parameters -Dteamcity.maven.watcher.home=/opt/buildagent/plugins/mavenPlugin/maven-watcher-jdk17 -Dteamcity.projectName=netology -Dteamcity.runner.properties.file=/opt/buildagent/temp/buildTmp/teamcity.runner.parameters -Dteamcity.tests.recentlyFailedTests.file=/opt/buildagent/temp/buildTmp/teamcity.testsToRunFirst.txt -Dteamcity.version=2022.10.3 (build 117072) -Dmaven.repo.local=/opt/buildagent/system/jetbrains.maven.runner/maven.repo.local -classpath /opt/buildagent/tools/maven3_6/boot/plexus-classworlds-2.6.0.jar: org.codehaus.plexus.classworlds.launcher.Launcher -f /opt/buildagent/work/74efd952ef63049f/pom.xml -B -Dmaven.test.failure.ignore=true clean test
[12:36:26] :	 [Step 1/1] in directory: /opt/buildagent/work/74efd952ef63049f
[12:36:27] :	 [Step 1/1] [INFO] Scanning for projects...
[12:36:27] :	 [Step 1/1] [INFO] 
[12:36:27] :	 [Step 1/1] [INFO] -----------------------< org.netology:plaindoll >-----------------------
[12:36:27] :	 [Step 1/1] [INFO] Building plaindoll 0.0.2
[12:36:27] :	 [Step 1/1] [INFO] --------------------------------[ jar ]---------------------------------
[12:36:27] :	 [Step 1/1] [Maven Watcher] project started: org.netology:plaindoll:jar:0.0.2
[12:36:27] :	 [Step 1/1] org.netology:plaindoll (13s)
[12:36:27]i:		 [org.netology:plaindoll] ##teamcity[importData tc:tags='tc:internal' type='surefire' path='/opt/buildagent/work/74efd952ef63049f/target/surefire-reports/TEST-*.xml' whenNoDataPublished='nothing' logAsInternal='true']
[12:36:27] :	 [Step 1/1] Importing data from '/opt/buildagent/work/74efd952ef63049f/target/surefire-reports/TEST-*.xml' (not existing file) with 'surefire' processor
[12:36:27]i:		 [org.netology:plaindoll] ##teamcity[importData tc:tags='tc:internal' type='surefire' path='/opt/buildagent/work/74efd952ef63049f/target/failsafe-reports/TEST-*.xml' whenNoDataPublished='nothing' logAsInternal='true']
[12:36:27] :	 [Step 1/1] [Maven Watcher] 
[12:36:27]i:	 [Step 1/1] ##teamcity[projectStarted tc:tags='tc:internal' projectId='org.netology:plaindoll:jar:0.0.2' groupId='org.netology' artifactId='plaindoll' testReportsDir0='/opt/buildagent/work/74efd952ef63049f/target/surefire-reports' testReportsDir1='/opt/buildagent/work/74efd952ef63049f/target/failsafe-reports']
[12:36:27] :	 [Step 1/1] Importing data from '/opt/buildagent/work/74efd952ef63049f/target/failsafe-reports/TEST-*.xml' (not existing file) with 'surefire' processor
[12:36:27] :	 [Step 1/1] Surefire report watcher
[12:36:27] :		 [Surefire report watcher] Watching paths:
[12:36:27] :		 [Surefire report watcher] /opt/buildagent/work/74efd952ef63049f/target/surefire-reports/TEST-*.xml
[12:36:27] :	 [Step 1/1] Surefire report watcher
[12:36:27] :		 [Surefire report watcher] Watching paths:
[12:36:27] :		 [Surefire report watcher] /opt/buildagent/work/74efd952ef63049f/target/failsafe-reports/TEST-*.xml
[12:36:27] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-clean-plugin/2.5/maven-clean-plugin-2.5.pom
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-clean-plugin/2.5/maven-clean-plugin-2.5.pom (3.9 kB at 9.3 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-plugins/22/maven-plugins-22.pom
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-plugins/22/maven-plugins-22.pom (13 kB at 184 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/21/maven-parent-21.pom
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/21/maven-parent-21.pom (26 kB at 366 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/apache/10/apache-10.pom
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/apache/10/apache-10.pom (15 kB at 228 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-clean-plugin/2.5/maven-clean-plugin-2.5.jar
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-clean-plugin/2.5/maven-clean-plugin-2.5.jar (25 kB at 347 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-resources-plugin/2.6/maven-resources-plugin-2.6.pom
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-resources-plugin/2.6/maven-resources-plugin-2.6.pom (8.1 kB at 121 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-plugins/23/maven-plugins-23.pom
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-plugins/23/maven-plugins-23.pom (9.2 kB at 151 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/22/maven-parent-22.pom
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/22/maven-parent-22.pom (30 kB at 425 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/apache/11/apache-11.pom
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/apache/11/apache-11.pom (15 kB at 239 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-resources-plugin/2.6/maven-resources-plugin-2.6.jar
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-resources-plugin/2.6/maven-resources-plugin-2.6.jar (30 kB at 441 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-compiler-plugin/3.1/maven-compiler-plugin-3.1.pom
[12:36:28] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-compiler-plugin/3.1/maven-compiler-plugin-3.1.pom (10 kB at 162 kB/s)
[12:36:28] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-plugins/24/maven-plugins-24.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-plugins/24/maven-plugins-24.pom (11 kB at 177 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/23/maven-parent-23.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/23/maven-parent-23.pom (33 kB at 494 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/apache/13/apache-13.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/apache/13/apache-13.pom (14 kB at 222 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-compiler-plugin/3.1/maven-compiler-plugin-3.1.jar
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-compiler-plugin/3.1/maven-compiler-plugin-3.1.jar (43 kB at 597 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-surefire-plugin/2.12.4/maven-surefire-plugin-2.12.4.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-surefire-plugin/2.12.4/maven-surefire-plugin-2.12.4.pom (10 kB at 169 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire/2.12.4/surefire-2.12.4.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire/2.12.4/surefire-2.12.4.pom (14 kB at 219 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-surefire-plugin/2.12.4/maven-surefire-plugin-2.12.4.jar
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-surefire-plugin/2.12.4/maven-surefire-plugin-2.12.4.jar (30 kB at 476 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/junit/junit/4.12/junit-4.12.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/junit/junit/4.12/junit-4.12.pom (24 kB at 382 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.pom (766 B at 13 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/hamcrest/hamcrest-parent/1.3/hamcrest-parent-1.3.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/hamcrest/hamcrest-parent/1.3/hamcrest-parent-1.3.pom (2.0 kB at 34 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/junit/junit/4.12/junit-4.12.jar
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.jar
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.jar (45 kB at 600 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/junit/junit/4.12/junit-4.12.jar (315 kB at 1.9 MB/s)
[12:36:29] :	 [Step 1/1] [INFO] 
[12:36:29] :	 [Step 1/1] [INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ plaindoll ---
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.0.6/maven-plugin-api-2.0.6.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.0.6/maven-plugin-api-2.0.6.pom (1.5 kB at 30 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven/2.0.6/maven-2.0.6.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven/2.0.6/maven-2.0.6.pom (9.0 kB at 197 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/5/maven-parent-5.pom
[12:36:29] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/5/maven-parent-5.pom (15 kB at 324 kB/s)
[12:36:29] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/apache/3/apache-3.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/apache/3/apache-3.pom (3.4 kB at 70 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/3.0/plexus-utils-3.0.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/3.0/plexus-utils-3.0.pom (4.1 kB at 87 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/spice/spice-parent/16/spice-parent-16.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/spice/spice-parent/16/spice-parent-16.pom (8.4 kB at 171 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/forge/forge-parent/5/forge-parent-5.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/forge/forge-parent/5/forge-parent-5.pom (8.4 kB at 182 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.0.6/maven-plugin-api-2.0.6.jar
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/3.0/plexus-utils-3.0.jar
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.0.6/maven-plugin-api-2.0.6.jar (13 kB at 280 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/3.0/plexus-utils-3.0.jar (226 kB at 2.3 MB/s)
[12:36:30] :	 [Step 1/1] [INFO] 
[12:36:30] :	 [Step 1/1] [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ plaindoll ---
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.0.6/maven-project-2.0.6.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.0.6/maven-project-2.0.6.pom (2.6 kB at 44 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.0.6/maven-settings-2.0.6.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.0.6/maven-settings-2.0.6.pom (2.0 kB at 33 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.0.6/maven-model-2.0.6.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.0.6/maven-model-2.0.6.pom (3.0 kB at 52 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.4.1/plexus-utils-1.4.1.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.4.1/plexus-utils-1.4.1.pom (1.9 kB at 32 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/1.0.11/plexus-1.0.11.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/1.0.11/plexus-1.0.11.pom (9.0 kB at 152 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.0-alpha-9-stable-1/plexus-container-default-1.0-alpha-9-stable-1.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.0-alpha-9-stable-1/plexus-container-default-1.0-alpha-9-stable-1.pom (3.9 kB at 66 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-containers/1.0.3/plexus-containers-1.0.3.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-containers/1.0.3/plexus-containers-1.0.3.pom (492 B at 7.0 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/1.0.4/plexus-1.0.4.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/1.0.4/plexus-1.0.4.pom (5.7 kB at 99 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/junit/junit/3.8.1/junit-3.8.1.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/junit/junit/3.8.1/junit-3.8.1.pom (998 B at 17 kB/s)
[12:36:30] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.0.4/plexus-utils-1.0.4.pom
[12:36:30] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.0.4/plexus-utils-1.0.4.pom (6.9 kB at 116 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/classworlds/classworlds/1.1-alpha-2/classworlds-1.1-alpha-2.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/classworlds/classworlds/1.1-alpha-2/classworlds-1.1-alpha-2.pom (3.1 kB at 52 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.0.6/maven-profile-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.0.6/maven-profile-2.0.6.pom (2.0 kB at 34 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.0.6/maven-artifact-manager-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.0.6/maven-artifact-manager-2.0.6.pom (2.6 kB at 44 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.0.6/maven-repository-metadata-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.0.6/maven-repository-metadata-2.0.6.pom (1.9 kB at 31 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.0.6/maven-artifact-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.0.6/maven-artifact-2.0.6.pom (1.6 kB at 26 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.0.6/maven-plugin-registry-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.0.6/maven-plugin-registry-2.0.6.pom (1.9 kB at 31 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.0.6/maven-core-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.0.6/maven-core-2.0.6.pom (6.7 kB at 112 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.0.6/maven-plugin-parameter-documenter-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.0.6/maven-plugin-parameter-documenter-2.0.6.pom (1.9 kB at 32 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting-api/2.0.6/maven-reporting-api-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting-api/2.0.6/maven-reporting-api-2.0.6.pom (1.8 kB at 30 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting/2.0.6/maven-reporting-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting/2.0.6/maven-reporting-2.0.6.pom (1.4 kB at 24 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/doxia/doxia-sink-api/1.0-alpha-7/doxia-sink-api-1.0-alpha-7.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/doxia/doxia-sink-api/1.0-alpha-7/doxia-sink-api-1.0-alpha-7.pom (424 B at 6.4 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/doxia/doxia/1.0-alpha-7/doxia-1.0-alpha-7.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/doxia/doxia/1.0-alpha-7/doxia-1.0-alpha-7.pom (3.9 kB at 62 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.0.6/maven-error-diagnostics-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.0.6/maven-error-diagnostics-2.0.6.pom (1.7 kB at 26 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/commons-cli/commons-cli/1.0/commons-cli-1.0.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/commons-cli/commons-cli/1.0/commons-cli-1.0.pom (2.1 kB at 36 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.0.6/maven-plugin-descriptor-2.0.6.pom
[12:36:31] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.0.6/maven-plugin-descriptor-2.0.6.pom (2.0 kB at 34 kB/s)
[12:36:31] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interactivity-api/1.0-alpha-4/plexus-interactivity-api-1.0-alpha-4.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interactivity-api/1.0-alpha-4/plexus-interactivity-api-1.0-alpha-4.pom (7.1 kB at 116 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.0.6/maven-monitor-2.0.6.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.0.6/maven-monitor-2.0.6.pom (1.3 kB at 19 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/classworlds/classworlds/1.1/classworlds-1.1.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/classworlds/classworlds/1.1/classworlds-1.1.pom (3.3 kB at 58 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/2.0.5/plexus-utils-2.0.5.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/2.0.5/plexus-utils-2.0.5.pom (3.3 kB at 57 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/2.0.6/plexus-2.0.6.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/2.0.6/plexus-2.0.6.pom (17 kB at 284 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-filtering/1.1/maven-filtering-1.1.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-filtering/1.1/maven-filtering-1.1.pom (5.8 kB at 96 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-components/17/maven-shared-components-17.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-components/17/maven-shared-components-17.pom (8.7 kB at 145 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.15/plexus-utils-1.5.15.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.15/plexus-utils-1.5.15.pom (6.8 kB at 109 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/2.0.2/plexus-2.0.2.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/2.0.2/plexus-2.0.2.pom (12 kB at 197 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interpolation/1.12/plexus-interpolation-1.12.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interpolation/1.12/plexus-interpolation-1.12.pom (889 B at 15 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-components/1.1.14/plexus-components-1.1.14.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-components/1.1.14/plexus-components-1.1.14.pom (5.8 kB at 101 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/plexus/plexus-build-api/0.0.4/plexus-build-api-0.0.4.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/plexus/plexus-build-api/0.0.4/plexus-build-api-0.0.4.pom (2.9 kB at 49 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/spice/spice-parent/10/spice-parent-10.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/spice/spice-parent/10/spice-parent-10.pom (3.0 kB at 51 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/forge/forge-parent/3/forge-parent-3.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/forge/forge-parent/3/forge-parent-3.pom (5.0 kB at 84 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.8/plexus-utils-1.5.8.pom
[12:36:32] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.8/plexus-utils-1.5.8.pom (8.1 kB at 141 kB/s)
[12:36:32] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interpolation/1.13/plexus-interpolation-1.13.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interpolation/1.13/plexus-interpolation-1.13.pom (890 B at 16 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-components/1.1.15/plexus-components-1.1.15.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-components/1.1.15/plexus-components-1.1.15.pom (2.8 kB at 50 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/2.0.3/plexus-2.0.3.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/2.0.3/plexus-2.0.3.pom (15 kB at 267 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.0.6/maven-project-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.0.6/maven-artifact-manager-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.0.6/maven-plugin-registry-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.0.6/maven-profile-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.0.6/maven-core-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.0.6/maven-artifact-manager-2.0.6.jar (57 kB at 1.1 MB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.0.6/maven-plugin-parameter-documenter-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.0.6/maven-project-2.0.6.jar (116 kB at 1.6 MB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting-api/2.0.6/maven-reporting-api-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.0.6/maven-plugin-parameter-documenter-2.0.6.jar (21 kB at 212 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/doxia/doxia-sink-api/1.0-alpha-7/doxia-sink-api-1.0-alpha-7.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.0.6/maven-profile-2.0.6.jar (35 kB at 332 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.0.6/maven-repository-metadata-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting-api/2.0.6/maven-reporting-api-2.0.6.jar (9.9 kB at 76 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.0.6/maven-error-diagnostics-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.0.6/maven-plugin-registry-2.0.6.jar (29 kB at 208 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/commons-cli/commons-cli/1.0/commons-cli-1.0.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/doxia/doxia-sink-api/1.0-alpha-7/doxia-sink-api-1.0-alpha-7.jar (5.9 kB at 41 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.0.6/maven-plugin-descriptor-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.0.6/maven-repository-metadata-2.0.6.jar (24 kB at 162 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interactivity-api/1.0-alpha-4/plexus-interactivity-api-1.0-alpha-4.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.0.6/maven-error-diagnostics-2.0.6.jar (14 kB at 71 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.0.6/maven-plugin-descriptor-2.0.6.jar (37 kB at 193 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/classworlds/classworlds/1.1/classworlds-1.1.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.0.6/maven-artifact-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.0.6/maven-core-2.0.6.jar (152 kB at 782 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.0.6/maven-settings-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interactivity-api/1.0-alpha-4/plexus-interactivity-api-1.0-alpha-4.jar (13 kB at 68 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.0.6/maven-model-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/commons-cli/commons-cli/1.0/commons-cli-1.0.jar (30 kB at 148 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.0.6/maven-monitor-2.0.6.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/classworlds/classworlds/1.1/classworlds-1.1.jar (38 kB at 160 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.0-alpha-9-stable-1/plexus-container-default-1.0-alpha-9-stable-1.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.0.6/maven-artifact-2.0.6.jar (87 kB at 345 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/junit/junit/3.8.1/junit-3.8.1.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.0.6/maven-settings-2.0.6.jar (49 kB at 192 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/2.0.5/plexus-utils-2.0.5.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.0.6/maven-model-2.0.6.jar (86 kB at 331 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-filtering/1.1/maven-filtering-1.1.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.0.6/maven-monitor-2.0.6.jar (10 kB at 39 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/plexus/plexus-build-api/0.0.4/plexus-build-api-0.0.4.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.0-alpha-9-stable-1/plexus-container-default-1.0-alpha-9-stable-1.jar (194 kB at 674 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interpolation/1.13/plexus-interpolation-1.13.jar
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-filtering/1.1/maven-filtering-1.1.jar (43 kB at 141 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/junit/junit/3.8.1/junit-3.8.1.jar (121 kB at 378 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/plexus/plexus-build-api/0.0.4/plexus-build-api-0.0.4.jar (6.8 kB at 21 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interpolation/1.13/plexus-interpolation-1.13.jar (61 kB at 182 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/2.0.5/plexus-utils-2.0.5.jar (223 kB at 649 kB/s)
[12:36:33]W:	 [Step 1/1] [WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[12:36:33] :	 [Step 1/1] [INFO] skip non existing resourceDirectory /opt/buildagent/work/74efd952ef63049f/src/main/resources
[12:36:33] :	 [Step 1/1] [INFO] 
[12:36:33] :	 [Step 1/1] [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ plaindoll ---
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.0.9/maven-plugin-api-2.0.9.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.0.9/maven-plugin-api-2.0.9.pom (1.5 kB at 24 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven/2.0.9/maven-2.0.9.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven/2.0.9/maven-2.0.9.pom (19 kB at 315 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/8/maven-parent-8.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/8/maven-parent-8.pom (24 kB at 409 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/apache/4/apache-4.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/apache/4/apache-4.pom (4.5 kB at 79 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.0.9/maven-artifact-2.0.9.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.0.9/maven-artifact-2.0.9.pom (1.6 kB at 25 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.1/plexus-utils-1.5.1.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.1/plexus-utils-1.5.1.pom (2.3 kB at 40 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.0.9/maven-core-2.0.9.pom
[12:36:33] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.0.9/maven-core-2.0.9.pom (7.8 kB at 134 kB/s)
[12:36:33] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.0.9/maven-settings-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.0.9/maven-settings-2.0.9.pom (2.1 kB at 35 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.0.9/maven-model-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.0.9/maven-model-2.0.9.pom (3.1 kB at 53 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.0.9/maven-plugin-parameter-documenter-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.0.9/maven-plugin-parameter-documenter-2.0.9.pom (2.0 kB at 33 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.0.9/maven-profile-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.0.9/maven-profile-2.0.9.pom (2.0 kB at 36 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.0.9/maven-repository-metadata-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.0.9/maven-repository-metadata-2.0.9.pom (1.9 kB at 33 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.0.9/maven-error-diagnostics-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.0.9/maven-error-diagnostics-2.0.9.pom (1.7 kB at 30 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.0.9/maven-project-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.0.9/maven-project-2.0.9.pom (2.7 kB at 46 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.0.9/maven-artifact-manager-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.0.9/maven-artifact-manager-2.0.9.pom (2.7 kB at 47 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.0.9/maven-plugin-registry-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.0.9/maven-plugin-registry-2.0.9.pom (2.0 kB at 34 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.0.9/maven-plugin-descriptor-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.0.9/maven-plugin-descriptor-2.0.9.pom (2.1 kB at 36 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.0.9/maven-monitor-2.0.9.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.0.9/maven-monitor-2.0.9.pom (1.3 kB at 22 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-toolchain/1.0/maven-toolchain-1.0.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-toolchain/1.0/maven-toolchain-1.0.pom (3.4 kB at 58 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-utils/0.1/maven-shared-utils-0.1.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-utils/0.1/maven-shared-utils-0.1.pom (4.0 kB at 70 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-components/18/maven-shared-components-18.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-components/18/maven-shared-components-18.pom (4.9 kB at 81 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/com/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/com/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.pom (965 B at 17 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-incremental/1.1/maven-shared-incremental-1.1.pom
[12:36:34] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-incremental/1.1/maven-shared-incremental-1.1.pom (4.7 kB at 82 kB/s)
[12:36:34] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-components/19/maven-shared-components-19.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-components/19/maven-shared-components-19.pom (6.4 kB at 112 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.2.1/maven-plugin-api-2.2.1.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.2.1/maven-plugin-api-2.2.1.pom (1.5 kB at 25 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven/2.2.1/maven-2.2.1.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven/2.2.1/maven-2.2.1.pom (22 kB at 386 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/11/maven-parent-11.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/11/maven-parent-11.pom (32 kB at 559 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/apache/5/apache-5.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/apache/5/apache-5.pom (4.1 kB at 71 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.2.1/maven-core-2.2.1.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.2.1/maven-core-2.2.1.pom (12 kB at 197 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.2.1/maven-settings-2.2.1.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.2.1/maven-settings-2.2.1.pom (2.2 kB at 38 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.2.1/maven-model-2.2.1.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.2.1/maven-model-2.2.1.pom (3.2 kB at 56 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interpolation/1.11/plexus-interpolation-1.11.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-interpolation/1.11/plexus-interpolation-1.11.pom (889 B at 16 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.2.1/maven-plugin-parameter-documenter-2.2.1.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.2.1/maven-plugin-parameter-documenter-2.2.1.pom (2.0 kB at 34 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/slf4j/slf4j-jdk14/1.5.6/slf4j-jdk14-1.5.6.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/slf4j/slf4j-jdk14/1.5.6/slf4j-jdk14-1.5.6.pom (1.9 kB at 33 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/slf4j/slf4j-parent/1.5.6/slf4j-parent-1.5.6.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/slf4j/slf4j-parent/1.5.6/slf4j-parent-1.5.6.pom (7.9 kB at 137 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/slf4j/slf4j-api/1.5.6/slf4j-api-1.5.6.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/slf4j/slf4j-api/1.5.6/slf4j-api-1.5.6.pom (3.0 kB at 52 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/slf4j/jcl-over-slf4j/1.5.6/jcl-over-slf4j-1.5.6.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/slf4j/jcl-over-slf4j/1.5.6/jcl-over-slf4j-1.5.6.pom (2.2 kB at 34 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.2.1/maven-profile-2.2.1.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.2.1/maven-profile-2.2.1.pom (2.2 kB at 37 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.2.1/maven-artifact-2.2.1.pom
[12:36:35] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.2.1/maven-artifact-2.2.1.pom (1.6 kB at 27 kB/s)
[12:36:35] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.2.1/maven-repository-metadata-2.2.1.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.2.1/maven-repository-metadata-2.2.1.pom (1.9 kB at 32 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.2.1/maven-error-diagnostics-2.2.1.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.2.1/maven-error-diagnostics-2.2.1.pom (1.7 kB at 29 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.2.1/maven-project-2.2.1.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.2.1/maven-project-2.2.1.pom (2.8 kB at 48 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.2.1/maven-artifact-manager-2.2.1.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.2.1/maven-artifact-manager-2.2.1.pom (3.1 kB at 54 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/backport-util-concurrent/backport-util-concurrent/3.1/backport-util-concurrent-3.1.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/backport-util-concurrent/backport-util-concurrent/3.1/backport-util-concurrent-3.1.pom (880 B at 15 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.2.1/maven-plugin-registry-2.2.1.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.2.1/maven-plugin-registry-2.2.1.pom (1.9 kB at 33 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.2.1/maven-plugin-descriptor-2.2.1.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.2.1/maven-plugin-descriptor-2.2.1.pom (2.1 kB at 36 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.2.1/maven-monitor-2.2.1.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.2.1/maven-monitor-2.2.1.pom (1.3 kB at 22 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/plexus/plexus-sec-dispatcher/1.3/plexus-sec-dispatcher-1.3.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/plexus/plexus-sec-dispatcher/1.3/plexus-sec-dispatcher-1.3.pom (3.0 kB at 52 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/spice/spice-parent/12/spice-parent-12.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/spice/spice-parent/12/spice-parent-12.pom (6.8 kB at 117 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/forge/forge-parent/4/forge-parent-4.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/forge/forge-parent/4/forge-parent-4.pom (8.4 kB at 145 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.5/plexus-utils-1.5.5.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.5/plexus-utils-1.5.5.pom (5.1 kB at 83 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/plexus/plexus-cipher/1.4/plexus-cipher-1.4.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/plexus/plexus-cipher/1.4/plexus-cipher-1.4.pom (2.1 kB at 36 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-component-annotations/1.5.5/plexus-component-annotations-1.5.5.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-component-annotations/1.5.5/plexus-component-annotations-1.5.5.pom (815 B at 14 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-containers/1.5.5/plexus-containers-1.5.5.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-containers/1.5.5/plexus-containers-1.5.5.pom (4.2 kB at 73 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/2.0.7/plexus-2.0.7.pom
[12:36:36] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/2.0.7/plexus-2.0.7.pom (17 kB at 303 kB/s)
[12:36:36] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-api/2.2/plexus-compiler-api-2.2.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-api/2.2/plexus-compiler-api-2.2.pom (865 B at 15 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler/2.2/plexus-compiler-2.2.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler/2.2/plexus-compiler-2.2.pom (3.6 kB at 62 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-components/1.3.1/plexus-components-1.3.1.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-components/1.3.1/plexus-components-1.3.1.pom (3.1 kB at 54 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/3.3.1/plexus-3.3.1.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/3.3.1/plexus-3.3.1.pom (20 kB at 347 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/spice/spice-parent/17/spice-parent-17.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/spice/spice-parent/17/spice-parent-17.pom (6.8 kB at 115 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/sonatype/forge/forge-parent/10/forge-parent-10.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/sonatype/forge/forge-parent/10/forge-parent-10.pom (14 kB at 238 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/3.0.8/plexus-utils-3.0.8.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/3.0.8/plexus-utils-3.0.8.pom (3.1 kB at 55 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/3.2/plexus-3.2.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus/3.2/plexus-3.2.pom (19 kB at 329 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-manager/2.2/plexus-compiler-manager-2.2.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-manager/2.2/plexus-compiler-manager-2.2.pom (690 B at 12 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-javac/2.2/plexus-compiler-javac-2.2.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-javac/2.2/plexus-compiler-javac-2.2.pom (769 B at 13 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compilers/2.2/plexus-compilers-2.2.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compilers/2.2/plexus-compilers-2.2.pom (1.2 kB at 22 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.5.5/plexus-container-default-1.5.5.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.5.5/plexus-container-default-1.5.5.pom (2.8 kB at 48 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.4.5/plexus-utils-1.4.5.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.4.5/plexus-utils-1.4.5.pom (2.3 kB at 39 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-classworlds/2.2.2/plexus-classworlds-2.2.2.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-classworlds/2.2.2/plexus-classworlds-2.2.2.pom (4.0 kB at 70 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/xbean/xbean-reflect/3.4/xbean-reflect-3.4.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/xbean/xbean-reflect/3.4/xbean-reflect-3.4.pom (2.8 kB at 48 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/xbean/xbean/3.4/xbean-3.4.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/xbean/xbean/3.4/xbean-3.4.pom (19 kB at 325 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/log4j/log4j/1.2.12/log4j-1.2.12.pom
[12:36:37] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/log4j/log4j/1.2.12/log4j-1.2.12.pom (145 B at 2.5 kB/s)
[12:36:37] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/commons-logging/commons-logging-api/1.1/commons-logging-api-1.1.pom
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/commons-logging/commons-logging-api/1.1/commons-logging-api-1.1.pom (5.3 kB at 94 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/com/google/collections/google-collections/1.0/google-collections-1.0.pom
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/com/google/collections/google-collections/1.0/google-collections-1.0.pom (2.5 kB at 43 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/com/google/google/1/google-1.pom
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/com/google/google/1/google-1.pom (1.6 kB at 27 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/junit/junit/3.8.2/junit-3.8.2.pom
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/junit/junit/3.8.2/junit-3.8.2.pom (747 B at 13 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.0.9/maven-plugin-api-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.0.9/maven-artifact-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.1/plexus-utils-1.5.1.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.0.9/maven-core-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.0.9/maven-settings-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact/2.0.9/maven-artifact-2.0.9.jar (89 kB at 1.8 MB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.0.9/maven-plugin-parameter-documenter-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-settings/2.0.9/maven-settings-2.0.9.jar (49 kB at 862 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.0.9/maven-profile-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-api/2.0.9/maven-plugin-api-2.0.9.jar (13 kB at 195 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.0.9/maven-model-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-core/2.0.9/maven-core-2.0.9.jar (160 kB at 2.0 MB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.0.9/maven-repository-metadata-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-parameter-documenter/2.0.9/maven-plugin-parameter-documenter-2.0.9.jar (21 kB at 227 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.0.9/maven-error-diagnostics-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-profile/2.0.9/maven-profile-2.0.9.jar (35 kB at 343 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.0.9/maven-project-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/1.5.1/plexus-utils-1.5.1.jar (211 kB at 1.9 MB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.0.9/maven-plugin-registry-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-model/2.0.9/maven-model-2.0.9.jar (87 kB at 710 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.0.9/maven-plugin-descriptor-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-error-diagnostics/2.0.9/maven-error-diagnostics-2.0.9.jar (14 kB at 102 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.0.9/maven-artifact-manager-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-repository-metadata/2.0.9/maven-repository-metadata-2.0.9.jar (25 kB at 178 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.0.9/maven-monitor-2.0.9.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-project/2.0.9/maven-project-2.0.9.jar (122 kB at 734 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-toolchain/1.0/maven-toolchain-1.0.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-registry/2.0.9/maven-plugin-registry-2.0.9.jar (29 kB at 171 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-utils/0.1/maven-shared-utils-0.1.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-artifact-manager/2.0.9/maven-artifact-manager-2.0.9.jar (58 kB at 323 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/com/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-plugin-descriptor/2.0.9/maven-plugin-descriptor-2.0.9.jar (37 kB at 205 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-incremental/1.1/maven-shared-incremental-1.1.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-monitor/2.0.9/maven-monitor-2.0.9.jar (10 kB at 53 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-component-annotations/1.5.5/plexus-component-annotations-1.5.5.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-toolchain/1.0/maven-toolchain-1.0.jar (33 kB at 157 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-api/2.2/plexus-compiler-api-2.2.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/com/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.jar (32 kB at 143 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-manager/2.2/plexus-compiler-manager-2.2.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-incremental/1.1/maven-shared-incremental-1.1.jar (14 kB at 56 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-javac/2.2/plexus-compiler-javac-2.2.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-utils/0.1/maven-shared-utils-0.1.jar (155 kB at 636 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.5.5/plexus-container-default-1.5.5.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-component-annotations/1.5.5/plexus-component-annotations-1.5.5.jar (4.2 kB at 17 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-classworlds/2.2.2/plexus-classworlds-2.2.2.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-api/2.2/plexus-compiler-api-2.2.jar (25 kB at 99 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/xbean/xbean-reflect/3.4/xbean-reflect-3.4.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-manager/2.2/plexus-compiler-manager-2.2.jar (4.6 kB at 17 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/log4j/log4j/1.2.12/log4j-1.2.12.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-compiler-javac/2.2/plexus-compiler-javac-2.2.jar (19 kB at 61 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/commons-logging/commons-logging-api/1.1/commons-logging-api-1.1.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.5.5/plexus-container-default-1.5.5.jar (217 kB at 692 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/com/google/collections/google-collections/1.0/google-collections-1.0.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-classworlds/2.2.2/plexus-classworlds-2.2.2.jar (46 kB at 146 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/junit/junit/3.8.2/junit-3.8.2.jar
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/xbean/xbean-reflect/3.4/xbean-reflect-3.4.jar (134 kB at 424 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/log4j/log4j/1.2.12/log4j-1.2.12.jar (358 kB at 1.0 MB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/commons-logging/commons-logging-api/1.1/commons-logging-api-1.1.jar (45 kB at 123 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/junit/junit/3.8.2/junit-3.8.2.jar (121 kB at 331 kB/s)
[12:36:38] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/com/google/collections/google-collections/1.0/google-collections-1.0.jar (640 kB at 1.6 MB/s)
[12:36:38] :	 [Step 1/1] [INFO] Changes detected - recompiling the module!
[12:36:38]W:	 [Step 1/1] [WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[12:36:38] :	 [Step 1/1] [INFO] Compiling 2 source files to /opt/buildagent/work/74efd952ef63049f/target/classes
[12:36:39] :	 [Step 1/1] [INFO] 
[12:36:39] :	 [Step 1/1] [INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ plaindoll ---
[12:36:39]W:	 [Step 1/1] [WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[12:36:39] :	 [Step 1/1] [INFO] skip non existing resourceDirectory /opt/buildagent/work/74efd952ef63049f/src/test/resources
[12:36:39] :	 [Step 1/1] [INFO] 
[12:36:39] :	 [Step 1/1] [INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ plaindoll ---
[12:36:39] :	 [Step 1/1] [INFO] Changes detected - recompiling the module!
[12:36:39]W:	 [Step 1/1] [WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[12:36:39] :	 [Step 1/1] [INFO] Compiling 1 source file to /opt/buildagent/work/74efd952ef63049f/target/test-classes
[12:36:39] :	 [Step 1/1] [INFO] 
[12:36:39] :	 [Step 1/1] [INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ plaindoll ---
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-booter/2.12.4/surefire-booter-2.12.4.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-booter/2.12.4/surefire-booter-2.12.4.pom (3.0 kB at 51 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-api/2.12.4/surefire-api-2.12.4.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-api/2.12.4/surefire-api-2.12.4.pom (2.5 kB at 42 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/maven-surefire-common/2.12.4/maven-surefire-common-2.12.4.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/maven-surefire-common/2.12.4/maven-surefire-common-2.12.4.pom (5.5 kB at 95 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugin-tools/maven-plugin-annotations/3.1/maven-plugin-annotations-3.1.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugin-tools/maven-plugin-annotations/3.1/maven-plugin-annotations-3.1.pom (1.6 kB at 28 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugin-tools/maven-plugin-tools/3.1/maven-plugin-tools-3.1.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugin-tools/maven-plugin-tools/3.1/maven-plugin-tools-3.1.pom (16 kB at 274 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting-api/2.0.9/maven-reporting-api-2.0.9.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting-api/2.0.9/maven-reporting-api-2.0.9.pom (1.8 kB at 31 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting/2.0.9/maven-reporting-2.0.9.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting/2.0.9/maven-reporting-2.0.9.pom (1.5 kB at 25 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-toolchain/2.0.9/maven-toolchain-2.0.9.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-toolchain/2.0.9/maven-toolchain-2.0.9.pom (3.5 kB at 49 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/commons/commons-lang3/3.1/commons-lang3-3.1.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/commons/commons-lang3/3.1/commons-lang3-3.1.pom (17 kB at 283 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/commons/commons-parent/22/commons-parent-22.pom
[12:36:39] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/commons/commons-parent/22/commons-parent-22.pom (42 kB at 723 kB/s)
[12:36:39] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/apache/9/apache-9.pom
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/apache/9/apache-9.pom (15 kB at 266 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-common-artifact-filters/1.3/maven-common-artifact-filters-1.3.pom
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-common-artifact-filters/1.3/maven-common-artifact-filters-1.3.pom (3.7 kB at 63 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-components/12/maven-shared-components-12.pom
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-shared-components/12/maven-shared-components-12.pom (9.3 kB at 158 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/13/maven-parent-13.pom
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-parent/13/maven-parent-13.pom (23 kB at 377 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/apache/6/apache-6.pom
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/apache/6/apache-6.pom (13 kB at 221 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.0-alpha-9/plexus-container-default-1.0-alpha-9.pom
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-container-default/1.0-alpha-9/plexus-container-default-1.0-alpha-9.pom (1.2 kB at 22 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-booter/2.12.4/surefire-booter-2.12.4.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-api/2.12.4/surefire-api-2.12.4.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/maven-surefire-common/2.12.4/maven-surefire-common-2.12.4.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/commons/commons-lang3/3.1/commons-lang3-3.1.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-common-artifact-filters/1.3/maven-common-artifact-filters-1.3.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/maven-surefire-common/2.12.4/maven-surefire-common-2.12.4.jar (263 kB at 5.3 MB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/3.0.8/plexus-utils-3.0.8.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/shared/maven-common-artifact-filters/1.3/maven-common-artifact-filters-1.3.jar (31 kB at 518 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting-api/2.0.9/maven-reporting-api-2.0.9.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-api/2.12.4/surefire-api-2.12.4.jar (118 kB at 1.9 MB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-booter/2.12.4/surefire-booter-2.12.4.jar (35 kB at 551 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-toolchain/2.0.9/maven-toolchain-2.0.9.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugin-tools/maven-plugin-annotations/3.1/maven-plugin-annotations-3.1.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/commons/commons-lang3/3.1/commons-lang3-3.1.jar (316 kB at 4.7 MB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/codehaus/plexus/plexus-utils/3.0.8/plexus-utils-3.0.8.jar (232 kB at 2.4 MB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/maven-toolchain/2.0.9/maven-toolchain-2.0.9.jar (38 kB at 316 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/reporting/maven-reporting-api/2.0.9/maven-reporting-api-2.0.9.jar (10 kB at 84 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugin-tools/maven-plugin-annotations/3.1/maven-plugin-annotations-3.1.jar (14 kB at 117 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Surefire report directory: /opt/buildagent/work/74efd952ef63049f/target/surefire-reports
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-junit4/2.12.4/surefire-junit4-2.12.4.pom
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-junit4/2.12.4/surefire-junit4-2.12.4.pom (2.4 kB at 42 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-providers/2.12.4/surefire-providers-2.12.4.pom
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-providers/2.12.4/surefire-providers-2.12.4.pom (2.3 kB at 39 kB/s)
[12:36:40] :	 [Step 1/1] [INFO] Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-junit4/2.12.4/surefire-junit4-2.12.4.jar
[12:36:40] :	 [Step 1/1] [INFO] Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/surefire/surefire-junit4/2.12.4/surefire-junit4-2.12.4.jar (37 kB at 626 kB/s)
[12:36:40] :	 [Step 1/1] 
[12:36:40] :	 [Step 1/1] -------------------------------------------------------
[12:36:40] :	 [Step 1/1]  T E S T S
[12:36:40] :	 [Step 1/1] -------------------------------------------------------
[12:36:40] :	 [Step 1/1] Running plaindoll.WelcomerTest
[12:36:41] :	 [Step 1/1] Tests run: 5, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.067 sec
[12:36:41] :	 [Step 1/1] 
[12:36:41] :	 [Step 1/1] Results :
[12:36:41] :	 [Step 1/1] 
[12:36:41] :	 [Step 1/1] Tests run: 5, Failures: 0, Errors: 0, Skipped: 0
[12:36:41] :	 [Step 1/1] 
[12:36:41] :	 [Step 1/1] [Maven Watcher] 
[12:36:41]i:	 [Step 1/1] ##teamcity[projectFinished tc:tags='tc:internal' projectId='org.netology:plaindoll:jar:0.0.2']
[12:36:41] :	 [Step 1/1] [INFO] ------------------------------------------------------------------------
[12:36:41] :	 [Step 1/1] [INFO] BUILD SUCCESS
[12:36:41] :	 [Step 1/1] [INFO] ------------------------------------------------------------------------
[12:36:41] :	 [Step 1/1] [INFO] Total time:  13.738 s
[12:36:41] :	 [Step 1/1] [INFO] Finished at: 2023-05-13T13:36:41+01:00
[12:36:41] :	 [Step 1/1] [INFO] ------------------------------------------------------------------------
[12:36:41] :	 [Step 1/1] [Maven Watcher] building report document...
[12:36:41] :	 [Step 1/1] [Maven Watcher] building report document done
[12:36:41] :	 [Step 1/1] [Maven Watcher] writing report to /opt/buildagent/temp/buildTmp/maven-build-info.xml
[12:36:41] :	 [Step 1/1] [Maven Watcher] done writing report
[12:36:41] :	 [Step 1/1] Process exited with code 0
[12:36:41] :	 [Step 1/1] Publishing artifacts
[12:36:41] :		 [Publishing artifacts] Collecting files to publish: [/opt/buildagent/temp/buildTmp/.tc-maven-bi/maven-build-info.xml.gz => .teamcity]
[12:36:41] :		 [Publishing artifacts] Publishing 1 file using [WebPublisher]: /opt/buildagent/temp/buildTmp/.tc-maven-bi/maven-build-info.xml.gz => .teamcity
[12:36:41] :		 [Publishing artifacts] Publishing 1 file using [ArtifactsCachePublisherImpl]: /opt/buildagent/temp/buildTmp/.tc-maven-bi/maven-build-info.xml.gz => .teamcity
[12:36:41]i:		 [Publishing artifacts] Will publish 1 artifact(s) to TeamCity node with id MAIN_SERVER
[12:36:41] :	 [Step 1/1] Waiting for 2 service processes to complete
[12:36:41]i:	 [Step 1/1] plaindoll.WelcomerTest
[12:36:41]i:		 [plaindoll.WelcomerTest] welcomerSaysFarewell
[12:36:41]i:		 [plaindoll.WelcomerTest] welcomerSaysHunter
[12:36:41]i:		 [plaindoll.WelcomerTest] welcomerSaysSilver
[12:36:41]i:		 [plaindoll.WelcomerTest] welcomerSaysSomething
[12:36:41]i:		 [plaindoll.WelcomerTest] welcomerSaysWelcome
[12:36:41] :	 [Step 1/1] Surefire report watcher
[12:36:41] :		 [Surefire report watcher] 1 report found for paths:
[12:36:41] :		 [Surefire report watcher] /opt/buildagent/work/74efd952ef63049f/target/surefire-reports/TEST-*.xml
[12:36:41] :		 [Surefire report watcher] Successfully parsed
[12:36:41] :			 [Successfully parsed] 1 report
[12:36:41] :			 [Successfully parsed] target/surefire-reports/TEST-plaindoll.WelcomerTest.xml
[12:36:41]i: Stopping performance monitoring process
[12:36:46]i: Performance monitoring process stopped
[12:36:46]i: Publishing performance monitoring build stages data
[12:36:46] : Publishing artifacts
[12:36:46] :	 [Publishing artifacts] Collecting files to publish: [/opt/buildagent/system/perfmon/temp/1/perfmon.csv=>.teamcity/perfmon/, /opt/buildagent/temp/agentTmp/build_stages.txt=>.teamcity/perfmon/]
[12:36:46] :	 [Publishing artifacts] Publishing 2 files using [WebPublisher]: /opt/buildagent/system/perfmon/temp/1/perfmon.csv, /opt/buildagent/temp/agentTmp/build_stages.txt => .teamcity/perfmon
[12:36:46] :	 [Publishing artifacts] Publishing 2 files using [ArtifactsCachePublisherImpl]: /opt/buildagent/system/perfmon/temp/1/perfmon.csv, /opt/buildagent/temp/agentTmp/build_stages.txt => .teamcity/perfmon
[12:36:46]i:	 [Publishing artifacts] Will publish 2 artifact(s) to TeamCity node with id MAIN_SERVER
[12:36:46] : Publishing internal artifacts
[12:36:46] :	 [Publishing internal artifacts] Publishing 1 file using [WebPublisher]
[12:36:46] :	 [Publishing internal artifacts] Publishing 1 file using [ArtifactsCachePublisherImpl]
[12:36:46]i:	 [Publishing internal artifacts] Will publish 1 artifact(s) to TeamCity node with id MAIN_SERVER
[12:36:46] : Build finished

  ```
  </details>
  
5. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`
![screen](tmp/goals.png)
6. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus
7. В pom.xml необходимо поменять ссылки на репозиторий и nexus
8. Запустите сборку по master, убедитесь что всё прошло успешно, артефакт появился в nexus

   
![screen](tmp/releases.png)   
   
<details>
   
<summary>Build log</summary>
 
 ```bash
     
Build 'netology / Build' #6, default branch 'master'
Triggered 2023-05-13 13:39:20 by 'admin'
Started 2023-05-13 13:39:22 on agent 'ip_51.250.84.148'
Finished 2023-05-13 13:39:32 with status NORMAL 'Tests passed: 5'
VCS revisions: 'Netology_HttpsGithubComM1m1craExampleTeamcityGitRefsHeadsMaster' (Git, instance id 1): '51e73f8774ae547467ea320c89aa5be71a2e64aa' (branch: 'refs/heads/master')
TeamCity URL http://localhost:8111/viewLog.html?buildId=6&buildTypeId=Netology_Build 
TeamCity server version is 2022.10.3 (build 117072), server timezone: GMT (UTC)

[13:39:20]W: bt1 (12s)
[13:39:20]i: TeamCity server version is 2022.10.3 (build 117072)
[13:39:20] : The build is removed from the queue to be prepared for the start
[13:39:20] : Collecting changes in 1 VCS root (2s)
[13:39:20] :	 [Collecting changes in 1 VCS root] VCS Root details
[13:39:20] :		 [VCS Root details] "https://github.com/m1m1cra/example-teamcity.git#refs/heads/master" {instance id=1, parent internal id=1, parent id=Netology_HttpsGithubComM1m1craExampleTeamcityGitRefsHeadsMaster, description: "https://github.com/m1m1cra/example-teamcity.git#refs/heads/master"}
[13:39:20]i:	 [Collecting changes in 1 VCS root] Loading current repository state for VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'
[13:39:20]i:		 [Loading current repository state for VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': git -c core.askpass=/opt/teamcity/temp/pass7453834397765322178 -c credential.helper= ls-remote origin
[13:39:20]i:	 [Collecting changes in 1 VCS root] Detecting changes in VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master' (used in 'Build')
[13:39:20]i:	 [Collecting changes in 1 VCS root] Will collect changes for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master' starting from revision d7197c76258f0698d462d20bca987f926ddda2ae
[13:39:20]i:	 [Collecting changes in 1 VCS root] VCS revisions for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master' - d7197c76258f0698d462d20bca987f926ddda2ae..51e73f8774ae547467ea320c89aa5be71a2e64aa
[13:39:20]i:	 [Collecting changes in 1 VCS root] Processing combined checkout rule for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master' 
[13:39:20]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': git -c core.askpass=/opt/teamcity/temp/pass6087999238583522616 -c credential.helper= ls-remote origin
[13:39:21]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': git -c core.askpass=/opt/teamcity/temp/pass4451970304148701723 -c credential.helper= remote prune origin
[13:39:21]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': git -c core.askpass=/opt/teamcity/temp/pass5584544389501923568 -c credential.helper= fetch --progress --no-tags --recurse-submodules=no https://m1m1cra@github.com/m1m1cra/example-teamcity.git +refs/heads/master:refs/heads/master
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Enumerating objects: 5, done.        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Counting objects:  20% (1/5)        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Counting objects:  40% (2/5)        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Counting objects:  60% (3/5)        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Counting objects:  80% (4/5)        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Counting objects: 100% (5/5)        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Counting objects: 100% (5/5), done.        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Compressing objects:  33% (1/3)        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Compressing objects:  66% (2/3)        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Compressing objects: 100% (3/3)        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Compressing objects: 100% (3/3), done.        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0        
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': Receiving objects:  33% (1/3)
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': Receiving objects:  66% (2/3)
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': Receiving objects: 100% (3/3)
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': Receiving objects: 100% (3/3), 678 bytes | 678.00 KiB/s, done.
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': Resolving deltas:   0% (0/2)
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': Resolving deltas:  50% (1/2)
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': Resolving deltas: 100% (2/2)
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': Resolving deltas: 100% (2/2), completed with 2 local objects.
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': From https://github.com/m1m1cra/example-teamcity
[13:39:22]i:	 [Collecting changes in 1 VCS root] VCS root 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master':    d7197c7..51e73f8  master     -> master
[13:39:22]i:	 [Collecting changes in 1 VCS root] Done collecting changes for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master': 1 changes collected 1 changes persisted, total time: 1s,644ms, persisting time: 7ms
[13:39:22] :	 [Collecting changes in 1 VCS root] Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'
[13:39:22] :		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] Upper limit revision: 51e73f8774ae547467ea320c89aa5be71a2e64aa
[13:39:22]i:		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] MaxModId = 2
[13:39:22] :		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] The first revision that was detected in the branch refs/heads/master: db1c910a3f0442d9a9b9c3411db8c9c298019bf1
[13:39:22] :		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] The first revision that was detected in the branch refs/heads/master after the last change of the VCS root or checkout rules: db1c910a3f0442d9a9b9c3411db8c9c298019bf1
[13:39:22] :		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] Latest commit attached to build configuration (with id <= 2): 51e73f8774ae547467ea320c89aa5be71a2e64aa
[13:39:22] :		 [Compute revision for 'https://github.com/m1m1cra/example-teamcity.git#refs/heads/master'] Computed revision: 51e73f8774ae547467ea320c89aa5be71a2e64aa
[13:39:22] : Starting the build on the agent "ip_51.250.84.148"
[13:39:22]i: Agent time zone: Europe/London
[13:39:22]i: Agent is running under JRE: 11.0.16.1+9-LTS
[13:39:22] : Updating tools for build
[13:39:22] :	 [Updating tools for build] Found 1 tool used by the build: maven3_6
[13:39:22] :	 [Updating tools for build] All used tools are up-to-date
[13:39:22]i: Preparing performance monitoring data directory: /opt/buildagent/system/perfmon
[13:39:22]i: Performance monitor is using command line: [perl, /opt/buildagent/system/perfmon/scripts/vmstatlinux.pl, /opt/buildagent/system/perfmon/temp/6/perfmon.csv, 1000]
[13:39:22]i: Starting performance monitoring process
[13:39:22]i: Performance monitoring process started
[13:39:22] : Clearing temporary directory: /opt/buildagent/temp/buildTmp
[13:39:22] : Publishing internal artifacts
[13:39:22] :	 [Publishing internal artifacts] Publishing 1 file using [WebPublisher]
[13:39:22] :	 [Publishing internal artifacts] Publishing 1 file using [ArtifactsCachePublisherImpl]
[13:39:22]i:	 [Publishing internal artifacts] Will publish 1 artifact(s) to TeamCity node with id MAIN_SERVER
[13:39:22] : Using vcs information from agent file: 74efd952ef63049f.xml
[13:39:22] : Checkout directory: /opt/buildagent/work/74efd952ef63049f
[13:39:22] : Updating sources: auto checkout (on agent) (1s)
[13:39:22] :	 [Updating sources] Will use agent side checkout
[13:39:22] :	 [Updating sources] VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master (1s)
[13:39:22] :		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] revision: 51e73f8774ae547467ea320c89aa5be71a2e64aa
[13:39:22]i:		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] Mirrors automatically enabled
[13:39:22] :		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] Git version: 2.40.0.0
[13:39:22] :		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git) (1s)
[13:39:22] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git config http.sslCAInfo
[13:39:22] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git show-ref
[13:39:22] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass9916645201612580797 -c credential.helper= ls-remote origin
[13:39:23] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git show-ref refs/heads/master
[13:39:23] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git log -n1 --pretty=format:%H%x20%s 51e73f8774ae547467ea320c89aa5be71a2e64aa --
[13:39:23]i:			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] fatal: bad object 51e73f8774ae547467ea320c89aa5be71a2e64aa
[13:39:23] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] 'git fetch' required: commit '51e73f8774ae547467ea320c89aa5be71a2e64aa' is not found in the local repository clone.
[13:39:23] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Enumerating objects: 5, done.        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Counting objects:  20% (1/5)        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Counting objects:  40% (2/5)        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Counting objects:  60% (3/5)        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Counting objects:  80% (4/5)        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Counting objects: 100% (5/5)        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Counting objects: 100% (5/5), done.        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Compressing objects:  33% (1/3)        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Compressing objects:  66% (2/3)        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Compressing objects: 100% (3/3)        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Compressing objects: 100% (3/3), done.        
[13:39:23]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0        
[13:39:24]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master] From https://github.com/m1m1cra/example-teamcity
[13:39:24]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master]    d7197c7..51e73f8  master     -> master
[13:39:24]i:				 [/usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass17640825573166482487 -c credential.helper= fetch --progress --recurse-submodules=no origin +refs/heads/master:refs/heads/master]    d7197c7..51e73f8  master     -> origin/master
[13:39:24] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git log -n1 --pretty=format:%H%x20%s 51e73f8774ae547467ea320c89aa5be71a2e64aa --
[13:39:24] :			 [Update git mirror (/opt/buildagent/system/git/git-BA3EC828.git)] /usr/bin/git pack-refs --all
[13:39:24] :		 [VCS Root: https://github.com/m1m1cra/example-teamcity.git#refs/heads/master] Update checkout directory (/opt/buildagent/work/74efd952ef63049f)
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git rev-parse --is-shallow-repository
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git config lfs.storage /opt/buildagent/system/git/git-BA3EC828.git/lfs
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git config core.sparseCheckout true
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git config http.sslCAInfo
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git show-ref
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git show-ref refs/remotes/origin/master
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git log -n1 --pretty=format:%H%x20%s 51e73f8774ae547467ea320c89aa5be71a2e64aa --
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] No 'git fetch' required: commit '51e73f8774ae547467ea320c89aa5be71a2e64aa' is in the local repository clone pointed by 'refs/remotes/origin/master'.
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git branch
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git -c core.askpass=/opt/buildagent/temp/buildTmp/pass14904261784945177925 -c credential.helper= -c credential.helper=/opt/buildagent/temp/buildTmp/credHelper2994316402868481097.sh reset --hard 51e73f8774ae547467ea320c89aa5be71a2e64aa
[13:39:24] :			 [Update checkout directory (/opt/buildagent/work/74efd952ef63049f)] /usr/bin/git branch --set-upstream-to=refs/remotes/origin/master
[13:39:24] : Build preparation done
[13:39:24]W: Step 1/2: Maven (for master) (Maven) (6s)
[13:39:24]i:	 [Step 1/2] Build step condition "teamcity.build.branch equals master" is satisfied
[13:39:24] :	 [Step 1/2] Using predefined Maven user settings: settings(1).xml
[13:39:24] :	 [Step 1/2] Using predefined Maven user settings: settings(1).xml
[13:39:24] :	 [Step 1/2] Initial M2_HOME not set
[13:39:24] :	 [Step 1/2] Current M2_HOME = /opt/buildagent/tools/maven3_6
[13:39:24] :	 [Step 1/2] PATH = /opt/buildagent/tools/maven3_6/bin:/opt/java/openjdk/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
[13:39:24] :	 [Step 1/2] Using watcher: /opt/buildagent/plugins/mavenPlugin/maven-watcher-jdk17/maven-watcher-agent.jar
[13:39:24] :	 [Step 1/2] Using agent local repository at /opt/buildagent/system/jetbrains.maven.runner/maven.repo.local
[13:39:24] :	 [Step 1/2] *** Start reading the project structure ***
[13:39:24]i:	 [Step 1/2] Initial MAVEN_OPTS not set
[13:39:24]i:	 [Step 1/2] Current MAVEN_OPTS not set
[13:39:25]i:	 [Step 1/2] [INFO] Scanning for projects...
[13:39:25]i:	 [Step 1/2] [INFO] Downloading from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/info-maven3-plugin/1.0.3/info-maven3-plugin-1.0.3.pom
[13:39:25]i:	 [Step 1/2] [INFO] Downloaded from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/info-maven3-plugin/1.0.3/info-maven3-plugin-1.0.3.pom (0 B at 0 B/s)
[13:39:25]i:	 [Step 1/2] [INFO] Downloading from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/info-maven3-plugin/1.0.3/info-maven3-plugin-1.0.3.jar
[13:39:25]i:	 [Step 1/2] [INFO] Downloaded from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/info-maven3-plugin/1.0.3/info-maven3-plugin-1.0.3.jar (0 B at 0 B/s)
[13:39:25]i:	 [Step 1/2] [INFO] 
[13:39:25]i:	 [Step 1/2] [INFO] -----------------------< org.netology:plaindoll >-----------------------
[13:39:25]i:	 [Step 1/2] [INFO] Building plaindoll 0.0.3
[13:39:25]i:	 [Step 1/2] [INFO] --------------------------------[ jar ]---------------------------------
[13:39:25]i:	 [Step 1/2] [INFO] 
[13:39:25]i:	 [Step 1/2] [INFO] --- info-maven3-plugin:1.0.3:info (default-cli) @ plaindoll ---
[13:39:25]i:	 [Step 1/2] [INFO] Downloading from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/maven-embedder-api/1.2.4/maven-embedder-api-1.2.4.pom
[13:39:25]i:	 [Step 1/2] [INFO] Downloaded from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/maven-embedder-api/1.2.4/maven-embedder-api-1.2.4.pom (0 B at 0 B/s)
[13:39:25]i:	 [Step 1/2] [INFO] Downloading from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xerces/xercesImpl/2.12.2/xercesImpl-2.12.2.pom
[13:39:25]i:	 [Step 1/2] [INFO] Downloaded from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xerces/xercesImpl/2.12.2/xercesImpl-2.12.2.pom (0 B)
[13:39:25]i:	 [Step 1/2] [INFO] Downloading from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xml-apis/xml-apis/1.4.01/xml-apis-1.4.01.pom
[13:39:25]i:	 [Step 1/2] [INFO] Downloaded from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xml-apis/xml-apis/1.4.01/xml-apis-1.4.01.pom (0 B)
[13:39:25]i:	 [Step 1/2] [INFO] Downloading from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/maven-embedder-api/1.2.4/maven-embedder-api-1.2.4.jar
[13:39:25]i:	 [Step 1/2] [INFO] Downloading from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xerces/xercesImpl/2.12.2/xercesImpl-2.12.2.jar
[13:39:25]i:	 [Step 1/2] [INFO] Downloaded from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/org/jetbrains/maven/maven-embedder-api/1.2.4/maven-embedder-api-1.2.4.jar (0 B at 0 B/s)
[13:39:25]i:	 [Step 1/2] [INFO] Downloading from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xml-apis/xml-apis/1.4.01/xml-apis-1.4.01.jar
[13:39:25]i:	 [Step 1/2] [INFO] Downloaded from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xerces/xercesImpl/2.12.2/xercesImpl-2.12.2.jar (0 B at 0 B/s)
[13:39:25]i:	 [Step 1/2] [INFO] Downloaded from teamcity_local_e223c1ed-ac97-48df-9b7c-49b825f1c849: file:/opt/buildagent/plugins/mavenPlugin/info-plugin/xml-apis/xml-apis/1.4.01/xml-apis-1.4.01.jar (0 B at 0 B/s)
[13:39:26]i:	 [Step 1/2] [INFO] ------------------------------------------------------------------------
[13:39:26]i:	 [Step 1/2] [INFO] BUILD SUCCESS
[13:39:26]i:	 [Step 1/2] [INFO] ------------------------------------------------------------------------
[13:39:26]i:	 [Step 1/2] [INFO] Total time:  0.354 s
[13:39:26]i:	 [Step 1/2] [INFO] Finished at: 2023-05-13T14:39:26+01:00
[13:39:26]i:	 [Step 1/2] [INFO] ------------------------------------------------------------------------
[13:39:26]i:	 [Step 1/2] Process exited with code 0
[13:39:26] :	 [Step 1/2] Initial MAVEN_OPTS not set
[13:39:26] :	 [Step 1/2] Current MAVEN_OPTS not set
[13:39:26] :	 [Step 1/2] Starting: /opt/java/openjdk/bin/java -Dagent.home.dir=/opt/buildagent -Dagent.name=ip_51.250.84.148 -Dagent.ownPort=9090 -Dagent.work.dir=/opt/buildagent/work -Dbuild.number=6 -Dbuild.vcs.number=51e73f8774ae547467ea320c89aa5be71a2e64aa -Dbuild.vcs.number.1=51e73f8774ae547467ea320c89aa5be71a2e64aa -Dbuild.vcs.number.Netology_HttpsGithubComM1m1craExampleTeamcityGitRefsHeadsMaster=51e73f8774ae547467ea320c89aa5be71a2e64aa -Dclassworlds.conf=/opt/buildagent/temp/buildTmp/teamcity.m2.conf -Dcom.jetbrains.maven.watcher.report.file=/opt/buildagent/temp/buildTmp/maven-build-info.xml -Dec2.instance-id=fhmvgsh7ajdb2sca9lg8 -Dec2.local-hostname=teamcity-agent.ru-central1.internal -Dec2.local-ipv4=10.128.0.3 -Dec2.public-hostname=51.250.84.148 -Dec2.public-ipv4=51.250.84.148 -Djava.io.tmpdir=/opt/buildagent/temp/buildTmp -Dmaven.home=/opt/buildagent/tools/maven3_6 -Dmaven.multiModuleProjectDirectory=/opt/buildagent/work/74efd952ef63049f -Dteamcity.agent.cpuBenchmark=527 -Dteamcity.agent.dotnet.agent_url=http://localhost:9090/RPC2 -Dteamcity.agent.dotnet.build_id=6 -Dteamcity.auth.password=******* -Dteamcity.auth.userId=TeamCityBuildId=6 -Dteamcity.build.changedFiles.file=/opt/buildagent/temp/buildTmp/teamcity.changedFiles.txt -Dteamcity.build.checkoutDir=/opt/buildagent/work/74efd952ef63049f -Dteamcity.build.id=6 -Dteamcity.build.properties.file=/opt/buildagent/temp/buildTmp/teamcity.build.parameters -Dteamcity.build.tempDir=/opt/buildagent/temp/buildTmp -Dteamcity.build.workingDir=/opt/buildagent/work/74efd952ef63049f -Dteamcity.buildConfName=Build -Dteamcity.buildType.id=Netology_Build -Dteamcity.configuration.properties.file=/opt/buildagent/temp/buildTmp/teamcity.config.parameters -Dteamcity.maven.userSettings.path=/opt/buildagent/temp/buildTmp/maven_settings_7619389650743303426.xml -Dteamcity.maven.watcher.home=/opt/buildagent/plugins/mavenPlugin/maven-watcher-jdk17 -Dteamcity.projectName=netology -Dteamcity.runner.properties.file=/opt/buildagent/temp/buildTmp/teamcity.runner.parameters -Dteamcity.tests.recentlyFailedTests.file=/opt/buildagent/temp/buildTmp/teamcity.testsToRunFirst.txt -Dteamcity.version=2022.10.3 (build 117072) -Dmaven.repo.local=/opt/buildagent/system/jetbrains.maven.runner/maven.repo.local -classpath /opt/buildagent/tools/maven3_6/boot/plexus-classworlds-2.6.0.jar: org.codehaus.plexus.classworlds.launcher.Launcher -f /opt/buildagent/work/74efd952ef63049f/pom.xml -B -s /opt/buildagent/temp/buildTmp/maven_settings_7619389650743303426.xml -Dmaven.test.failure.ignore=true clean deploy
[13:39:26] :	 [Step 1/2] in directory: /opt/buildagent/work/74efd952ef63049f
[13:39:27] :	 [Step 1/2] [INFO] Scanning for projects...
[13:39:27] :	 [Step 1/2] [INFO] 
[13:39:27] :	 [Step 1/2] [INFO] -----------------------< org.netology:plaindoll >-----------------------
[13:39:27] :	 [Step 1/2] [INFO] Building plaindoll 0.0.3
[13:39:27] :	 [Step 1/2] [INFO] --------------------------------[ jar ]---------------------------------
[13:39:27] :	 [Step 1/2] [Maven Watcher] project started: org.netology:plaindoll:jar:0.0.3
[13:39:27] :	 [Step 1/2] org.netology:plaindoll (3s)
[13:39:27]i:		 [org.netology:plaindoll] ##teamcity[importData tc:tags='tc:internal' type='surefire' path='/opt/buildagent/work/74efd952ef63049f/target/surefire-reports/TEST-*.xml' whenNoDataPublished='nothing' logAsInternal='true']
[13:39:27]i:		 [org.netology:plaindoll] ##teamcity[importData tc:tags='tc:internal' type='surefire' path='/opt/buildagent/work/74efd952ef63049f/target/failsafe-reports/TEST-*.xml' whenNoDataPublished='nothing' logAsInternal='true']
[13:39:27] :	 [Step 1/2] [Maven Watcher] 
[13:39:27]i:	 [Step 1/2] ##teamcity[projectStarted tc:tags='tc:internal' projectId='org.netology:plaindoll:jar:0.0.3' groupId='org.netology' artifactId='plaindoll' testReportsDir0='/opt/buildagent/work/74efd952ef63049f/target/surefire-reports' testReportsDir1='/opt/buildagent/work/74efd952ef63049f/target/failsafe-reports']
[13:39:27] :	 [Step 1/2] Importing data from '/opt/buildagent/work/74efd952ef63049f/target/failsafe-reports/TEST-*.xml' (not existing file) with 'surefire' processor
[13:39:27] :	 [Step 1/2] Importing data from '/opt/buildagent/work/74efd952ef63049f/target/surefire-reports/TEST-*.xml' (not existing file) with 'surefire' processor
[13:39:27] :	 [Step 1/2] Surefire report watcher
[13:39:27] :		 [Surefire report watcher] Watching paths:
[13:39:27] :		 [Surefire report watcher] /opt/buildagent/work/74efd952ef63049f/target/failsafe-reports/TEST-*.xml
[13:39:27] :	 [Step 1/2] Surefire report watcher
[13:39:27] :		 [Surefire report watcher] Watching paths:
[13:39:27] :		 [Surefire report watcher] /opt/buildagent/work/74efd952ef63049f/target/surefire-reports/TEST-*.xml
[13:39:27] :	 [Step 1/2] [INFO] 
[13:39:27] :	 [Step 1/2] [INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ plaindoll ---
[13:39:27] :	 [Step 1/2] [INFO] Deleting /opt/buildagent/work/74efd952ef63049f/target
[13:39:27] :	 [Step 1/2] [INFO] 
[13:39:27] :	 [Step 1/2] [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ plaindoll ---
[13:39:27]W:	 [Step 1/2] [WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[13:39:27] :	 [Step 1/2] [INFO] skip non existing resourceDirectory /opt/buildagent/work/74efd952ef63049f/src/main/resources
[13:39:27] :	 [Step 1/2] [INFO] 
[13:39:27] :	 [Step 1/2] [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ plaindoll ---
[13:39:28] :	 [Step 1/2] [INFO] Changes detected - recompiling the module!
[13:39:28]W:	 [Step 1/2] [WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[13:39:28] :	 [Step 1/2] [INFO] Compiling 2 source files to /opt/buildagent/work/74efd952ef63049f/target/classes
[13:39:28] :	 [Step 1/2] [INFO] 
[13:39:28] :	 [Step 1/2] [INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ plaindoll ---
[13:39:28]W:	 [Step 1/2] [WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[13:39:28] :	 [Step 1/2] [INFO] skip non existing resourceDirectory /opt/buildagent/work/74efd952ef63049f/src/test/resources
[13:39:28] :	 [Step 1/2] [INFO] 
[13:39:28] :	 [Step 1/2] [INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ plaindoll ---
[13:39:28] :	 [Step 1/2] [INFO] Changes detected - recompiling the module!
[13:39:28]W:	 [Step 1/2] [WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[13:39:28] :	 [Step 1/2] [INFO] Compiling 1 source file to /opt/buildagent/work/74efd952ef63049f/target/test-classes
[13:39:28] :	 [Step 1/2] [INFO] 
[13:39:28] :	 [Step 1/2] [INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ plaindoll ---
[13:39:28] :	 [Step 1/2] [INFO] Surefire report directory: /opt/buildagent/work/74efd952ef63049f/target/surefire-reports
[13:39:28] :	 [Step 1/2] 
[13:39:28] :	 [Step 1/2] -------------------------------------------------------
[13:39:28] :	 [Step 1/2]  T E S T S
[13:39:28] :	 [Step 1/2] -------------------------------------------------------
[13:39:29] :	 [Step 1/2] Running plaindoll.WelcomerTest
[13:39:29] :	 [Step 1/2] Tests run: 5, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.056 sec
[13:39:29] :	 [Step 1/2] 
[13:39:29] :	 [Step 1/2] Results :
[13:39:29] :	 [Step 1/2] 
[13:39:29] :	 [Step 1/2] Tests run: 5, Failures: 0, Errors: 0, Skipped: 0
[13:39:29] :	 [Step 1/2] 
[13:39:29] :	 [Step 1/2] [INFO] 
[13:39:29] :	 [Step 1/2] [INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ plaindoll ---
[13:39:29] :	 [Step 1/2] [INFO] Building jar: /opt/buildagent/work/74efd952ef63049f/target/plaindoll-0.0.3.jar
[13:39:29] :	 [Step 1/2] [INFO] 
[13:39:29] :	 [Step 1/2] [INFO] --- maven-shade-plugin:3.2.4:shade (default) @ plaindoll ---
[13:39:29]i:	 [Step 1/2] plaindoll.WelcomerTest
[13:39:29]i:		 [plaindoll.WelcomerTest] welcomerSaysFarewell
[13:39:29]i:		 [plaindoll.WelcomerTest] welcomerSaysHunter
[13:39:29]i:		 [plaindoll.WelcomerTest] welcomerSaysSilver
[13:39:29]i:		 [plaindoll.WelcomerTest] welcomerSaysSomething
[13:39:29]i:		 [plaindoll.WelcomerTest] welcomerSaysWelcome
[13:39:29] :	 [Step 1/2] [INFO] Replacing original artifact with shaded artifact.
[13:39:29] :	 [Step 1/2] [INFO] Replacing /opt/buildagent/work/74efd952ef63049f/target/plaindoll-0.0.3.jar with /opt/buildagent/work/74efd952ef63049f/target/plaindoll-0.0.3-shaded.jar
[13:39:29] :	 [Step 1/2] [INFO] 
[13:39:29] :	 [Step 1/2] [INFO] --- maven-install-plugin:2.4:install (default-install) @ plaindoll ---
[13:39:29] :	 [Step 1/2] [INFO] Installing /opt/buildagent/work/74efd952ef63049f/target/plaindoll-0.0.3.jar to /opt/buildagent/system/jetbrains.maven.runner/maven.repo.local/org/netology/plaindoll/0.0.3/plaindoll-0.0.3.jar
[13:39:29] :	 [Step 1/2] [INFO] Installing /opt/buildagent/work/74efd952ef63049f/pom.xml to /opt/buildagent/system/jetbrains.maven.runner/maven.repo.local/org/netology/plaindoll/0.0.3/plaindoll-0.0.3.pom
[13:39:29] :	 [Step 1/2] [INFO] 
[13:39:29] :	 [Step 1/2] [INFO] --- maven-deploy-plugin:2.7:deploy (default-deploy) @ plaindoll ---
[13:39:30] :	 [Step 1/2] [INFO] Uploading to nexus: http://158.160.102.180:8081/repository/maven-releases/org/netology/plaindoll/0.0.3/plaindoll-0.0.3.jar
[13:39:30] :	 [Step 1/2] [INFO] Uploaded to nexus: http://158.160.102.180:8081/repository/maven-releases/org/netology/plaindoll/0.0.3/plaindoll-0.0.3.jar (3.2 kB at 16 kB/s)
[13:39:30] :	 [Step 1/2] [INFO] Uploading to nexus: http://158.160.102.180:8081/repository/maven-releases/org/netology/plaindoll/0.0.3/plaindoll-0.0.3.pom
[13:39:30] :	 [Step 1/2] [INFO] Uploaded to nexus: http://158.160.102.180:8081/repository/maven-releases/org/netology/plaindoll/0.0.3/plaindoll-0.0.3.pom (1.5 kB at 13 kB/s)
[13:39:30] :	 [Step 1/2] [INFO] Downloading from nexus: http://158.160.102.180:8081/repository/maven-releases/org/netology/plaindoll/maven-metadata.xml
[13:39:30] :	 [Step 1/2] [INFO] Downloaded from nexus: http://158.160.102.180:8081/repository/maven-releases/org/netology/plaindoll/maven-metadata.xml (301 B at 6.4 kB/s)
[13:39:30] :	 [Step 1/2] [INFO] Uploading to nexus: http://158.160.102.180:8081/repository/maven-releases/org/netology/plaindoll/maven-metadata.xml
[13:39:30] :	 [Step 1/2] [INFO] Uploaded to nexus: http://158.160.102.180:8081/repository/maven-releases/org/netology/plaindoll/maven-metadata.xml (332 B at 1.9 kB/s)
[13:39:30] :	 [Step 1/2] [Maven Watcher] 
[13:39:30]i:	 [Step 1/2] ##teamcity[projectFinished tc:tags='tc:internal' projectId='org.netology:plaindoll:jar:0.0.3']
[13:39:30] :	 [Step 1/2] [INFO] ------------------------------------------------------------------------
[13:39:30] :	 [Step 1/2] [INFO] BUILD SUCCESS
[13:39:30] :	 [Step 1/2] [INFO] ------------------------------------------------------------------------
[13:39:30] :	 [Step 1/2] [INFO] Total time:  3.188 s
[13:39:30] :	 [Step 1/2] [INFO] Finished at: 2023-05-13T14:39:30+01:00
[13:39:30] :	 [Step 1/2] [INFO] ------------------------------------------------------------------------
[13:39:30] :	 [Step 1/2] [Maven Watcher] building report document...
[13:39:30] :	 [Step 1/2] [Maven Watcher] building report document done
[13:39:30] :	 [Step 1/2] [Maven Watcher] writing report to /opt/buildagent/temp/buildTmp/maven-build-info.xml
[13:39:30] :	 [Step 1/2] [Maven Watcher] done writing report
[13:39:30] :	 [Step 1/2] Process exited with code 0
[13:39:30] :	 [Step 1/2] Publishing artifacts
[13:39:30] :		 [Publishing artifacts] Collecting files to publish: [/opt/buildagent/temp/buildTmp/.tc-maven-bi/maven-build-info.xml.gz => .teamcity]
[13:39:30] :		 [Publishing artifacts] Publishing 1 file using [WebPublisher]: /opt/buildagent/temp/buildTmp/.tc-maven-bi/maven-build-info.xml.gz => .teamcity
[13:39:30] :		 [Publishing artifacts] Publishing 1 file using [ArtifactsCachePublisherImpl]: /opt/buildagent/temp/buildTmp/.tc-maven-bi/maven-build-info.xml.gz => .teamcity
[13:39:30]i:		 [Publishing artifacts] Will publish 1 artifact(s) to TeamCity node with id MAIN_SERVER
[13:39:30] :	 [Step 1/2] Waiting for 2 service processes to complete
[13:39:30] :	 [Step 1/2] Surefire report watcher
[13:39:31] :		 [Surefire report watcher] 1 report found for paths:
[13:39:31] :		 [Surefire report watcher] /opt/buildagent/work/74efd952ef63049f/target/surefire-reports/TEST-*.xml
[13:39:31] :		 [Surefire report watcher] Successfully parsed
[13:39:31] :			 [Successfully parsed] 1 report
[13:39:31] :			 [Successfully parsed] target/surefire-reports/TEST-plaindoll.WelcomerTest.xml
[13:39:31]W: Step 2/2: Maven (for other branches) (Maven)
[13:39:31]W:	 [Step 2/2] Build step Maven (for other branches) (Maven) is skipped because of unfulfilled condition: "teamcity.build.branch does not equal master"
[13:39:31]i: Stopping performance monitoring process
[13:39:32]i: Performance monitoring process stopped
[13:39:32]i: Publishing performance monitoring build stages data
[13:39:32] : Publishing artifacts
[13:39:32] :	 [Publishing artifacts] Collecting files to publish: [/opt/buildagent/system/perfmon/temp/6/perfmon.csv=>.teamcity/perfmon/, /opt/buildagent/temp/agentTmp/build_stages.txt=>.teamcity/perfmon/]
[13:39:32] :	 [Publishing artifacts] Publishing 2 files using [WebPublisher]: /opt/buildagent/system/perfmon/temp/6/perfmon.csv, /opt/buildagent/temp/agentTmp/build_stages.txt => .teamcity/perfmon
[13:39:32] :	 [Publishing artifacts] Publishing 2 files using [ArtifactsCachePublisherImpl]: /opt/buildagent/system/perfmon/temp/6/perfmon.csv, /opt/buildagent/temp/agentTmp/build_stages.txt => .teamcity/perfmon
[13:39:32]i:	 [Publishing artifacts] Will publish 2 artifact(s) to TeamCity node with id MAIN_SERVER
[13:39:32] : Publishing internal artifacts
[13:39:32] :	 [Publishing internal artifacts] Publishing 1 file using [WebPublisher]
[13:39:32] :	 [Publishing internal artifacts] Publishing 1 file using [ArtifactsCachePublisherImpl]
[13:39:32]i:	 [Publishing internal artifacts] Will publish 1 artifact(s) to TeamCity node with id MAIN_SERVER
[13:39:32] : Build finished

 ```
 
   </details>
   
9. Мигрируйте `build configuration` в репозиторий
![screen](tmp/mb.png) 
![screen](tmp/sync.png)  
10. Создайте отдельную ветку `feature/add_reply` в репозитории
```bash
root@bhdevops:/home/avdeevan/teamcity/example-teamcity# git branch -r
origin/HEAD -> origin/master
origin/feature/add_reply
origin/master
root@bhdevops:/home/avdeevan/teamcity/example-teamcity# 
```
11. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`
```java
package plaindoll;

public class Welcomer{
	public String sayWelcome() {
		return "Welcome home, good hunter. What is it your desire?";
	}
	public String sayFarewell() {
		return "Farewell, good hunter. May you find your worth in waking world.";
	}
	public String sayNeedGold(){
		return "Not enough gold";
	}
	public String saySome(){
		return "something in the way";
	}
	public String sayGoodEveningHunter(){
		return "Good evening, hunter!";
	}
}
```
12. Дополните тест для нового метода на поиск слова `hunter` в новой репликe
```java
package plaindoll;

import static org.hamcrest.CoreMatchers.containsString;
import static org.junit.Assert.*;

import org.junit.Test;

public class WelcomerTest {
	
	private Welcomer welcomer = new Welcomer();

	@Test
	public void welcomerSaysWelcome() {
		assertThat(welcomer.sayWelcome(), containsString("Welcome"));
	}
	@Test
	public void welcomerSaysFarewell() {
		assertThat(welcomer.sayFarewell(), containsString("Farewell"));
	}
	@Test
	public void welcomerSaysHunter() {
		assertThat(welcomer.sayWelcome(), containsString("hunter"));
		assertThat(welcomer.sayFarewell(), containsString("hunter"));
	}
	@Test
	public void welcomerSaysSilver(){
		assertThat(welcomer.sayNeedGold(), containsString("gold"));
	}
	@Test
	public void welcomerSaysSomething(){
		assertThat(welcomer.saySome(), containsString("something"));
	}
	@Test
	public void welcomerSaysGoodEveningToHunter(){
		assertThat(welcomer.saySome(), containsString("hunter"));
	}
}
}
```
13. Сделайте push всех изменений в новую ветку в репозиторий
![screen](tmp/git.png)
14. Убедитесь что сборка самостоятельно запустилась, тесты прошли успешно
![screen](tmp/autobuild.png)   
15. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`
16. Убедитесь, что нет собранного артефакта в сборке по ветке `master`
![screen](tmp/afterbuild.png)   
17. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки
![screen](tmp/art1.png)   
18. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны
![screen](tmp/art2.png)   
19. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity
	
https://github.com/m1m1cra/example-teamcity/tree/master/.teamcity/Netology	
	
20. В ответ предоставьте ссылку на репозиторий

---

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
