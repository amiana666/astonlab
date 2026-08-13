## Создание папки, в которой будет создан новый гит-репозиторий
boxuser@Amireizel:~/hwlab$ mkdir astonlab
vboxuser@Amireizel:~/hwlab$ cd astonlab/
vboxuser@Amireizel:~/hwlab/astonlab$ git status
fatal: not a git repository (or any of the parent directories): .git
## Так, как репозитория нет, что проверено командой git status, создаем новый
vboxuser@Amireizel:~/hwlab/astonlab$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint: 	git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint: 	git branch -m <name>
Initialized empty Git repository in /home/vboxuser/hwlab/astonlab/.git/
vboxuser@Amireizel:~/hwlab/astonlab$ git branch
## Нам рекомендуют указать имя, но по дефолту ветка мастер создается сама, напрямую ее именовать не нужно, если только у нас не должнa быть dtnrf с названием `main` 
vboxuser@Amireizel:~/hwlab/astonlab$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
## Создаем файл README.md и коммитим его
vboxuser@Amireizel:~/hwlab/astonlab$ echo "# astonlab" >> README.md
vboxuser@Amireizel:~/hwlab/astonlab$ git add .
vboxuser@Amireizel:~/hwlab/astonlab$ git commit -m "Initial commit"
[master (root-commit) 3884ad1] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
## Проверяем что у нас есть по итогу
vboxuser@Amireizel:~/hwlab/astonlab$ git show
commit 3884ad19d03474e156465311414d2ba12422b55f (HEAD -> master)
Author: Anastasia Anishchenko <a.anishchenko@mail.astondevs.ru>
Date:   Thu Aug 13 09:03:38 2026 +0000

    Initial commit

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..de58e5e
--- /dev/null
+++ b/README.md
@@ -0,0 +1 @@
+# astonlab
vboxuser@Amireizel:~/hwlab/astonlab$ git branch
* master
## У нас теперь есть фетка с нашим первым коммитом, создадим ветку develop и переключимся на нее
vboxuser@Amireizel:~/hwlab/astonlab$ git checkout -b develop
Switched to a new branch 'develop'
vboxuser@Amireizel:~/hwlab/astonlab$ git branch
* develop
  master
## Создадим файл .gitignore и добавим его к нашему последнему коммиту
vboxuser@Amireizel:~/hwlab/astonlab$ touch .gitignore
vboxuser@Amireizel:~/hwlab/astonlab$ git add .
vboxuser@Amireizel:~/hwlab/astonlab$ git commit --amend
[develop ecc423f] Initial commit
 Date: Thu Aug 13 09:03:38 2026 +0000
 2 files changed, 1 insertion(+)
 create mode 100644 .gitignore
 create mode 100644 README.md
vboxuser@Amireizel:~/hwlab/astonlab$ git show
commit ecc423ff03175abab02396e3d01c1415a6f62b68 (HEAD -> develop)
Author: Anastasia Anishchenko <a.anishchenko@mail.astondevs.ru>
Date:   Thu Aug 13 09:03:38 2026 +0000

    Initial commit

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..e69de29
diff --git a/README.md b/README.md
new file mode 100644
index 0000000..de58e5e
--- /dev/null
+++ b/README.md
@@ -0,0 +1 @@
+# astonlab
## Проверим наш статус гит-репозитория и начнем документировать действия в REPORT.md
vboxuser@Amireizel:~/hwlab/astonlab$ git status
On branch develop
nothing to commit, working tree clean
vboxuser@Amireizel:~/hwlab/astonlab$ touch REPORT.md
vboxuser@Amireizel:~/hwlab/astonlab$ nano REPORT.md
## Создаем связь с нашим репозиторием и пушим туда 2 ветки
vboxuser@Amireizel:~/hwlab/astonlab$ git remote add origin https://github.com/amiana666/astonlab.git
vboxuser@Amireizel:~/hwlab/astonlab$ git remote -v
origin	https://github.com/amiana666/astonlab.git (fetch)
origin	https://github.com/amiana666/astonlab.git (push)
vboxuser@Amireizel:~/hwlab/astonlab$ git push --all origin
Username for 'https://github.com': amiana666
Password for 'https://amiana666@github.com': 
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 2 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (6/6), 425 bytes | 425.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/amiana666/astonlab.git
 * [new branch]      develop -> develop
 * [new branch]      master -> master
vboxuser@Amireizel:~/hwlab/astonlab$ 
## Создаем новую ветку под текущий issue
vboxuser@Amireizel:~/hwlab/astonlab$ git branch
* develop
  master
vboxuser@Amireizel:~/hwlab/astonlab$ git checkout -b introduction_to_linux
Switched to a new branch 'introduction_to_linux'
vboxuser@Amireizel:~/hwlab/astonlab$ git branch
  develop
* introduction_to_linux
  master
## Перемещаем файл README.md из текущего issue (использование в качестве примера)
vboxuser@Amireizel:~/hwlab/Introduction_To_Linux$ ls
img  matereals  README.md  REPORT.md  src
vboxuser@Amireizel:~/hwlab/Introduction_To_Linux$ cp README.md /home/vboxuser/hwlab/astonlab
vboxuser@Amireizel:~/hwlab/Introduction_To_Linux$ cd ..
vboxuser@Amireizel:~/hwlab$ cd astonlab/
vboxuser@Amireizel:~/hwlab/astonlab$ ls
README.md  REPORT.md
## Коммитим последние изменения и пушим в удаленный репозиторий
vboxuser@Amireizel:~/hwlab/astonlab$ git add .
vboxuser@Amireizel:~/hwlab/astonlab$ git push --set-upstream origin introduction_to_linux
Username for 'https://github.com': amiana666
Password for 'https://amiana666@github.com': 
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'introduction_to_linux' on GitHub by visiting:
remote:      https://github.com/amiana666/astonlab/pull/new/introduction_to_linux
remote: 
To https://github.com/amiana666/astonlab.git
 * [new branch]      introduction_to_linux -> introduction_to_linux
branch 'introduction_to_linux' set up to track 'origin/introduction_to_linux'.
vboxuser@Amireizel:~/hwlab/astonlab$ git status
On branch introduction_to_linux
Your branch is up to date with 'origin/introduction_to_linux'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   .gitignore
	modified:   README.md
	new file:   REPORT.md

vboxuser@Amireizel:~/hwlab/astonlab$ git commit -m "feat: add issue-branch"
[introduction_to_linux 4e9d809] feat: add issue-branch
 3 files changed, 384 insertions(+), 1 deletion(-)
 create mode 100644 REPORT.md
vboxuser@Amireizel:~/hwlab/astonlab$ git status
On branch introduction_to_linux
Your branch is ahead of 'origin/introduction_to_linux' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
vboxuser@Amireizel:~/hwlab/astonlab$ git push
Username for 'https://github.com': amiana666
Password for 'https://amiana666@github.com': 
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 2 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 6.72 KiB | 6.72 MiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/amiana666/astonlab.git
   ecc423f..4e9d809  introduction_to_linux -> introduction_to_linux
## На github делаем merge request по ветке в develop
Во вкладке Pull requests -> New pull requests -> Мерджим с выбором веток: источник -> цель
## Создаем issue + ветка в самом гитхаб




