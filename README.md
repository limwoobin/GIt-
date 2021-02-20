# GIt-Command 


> #### git init : git 생성하기
```shell script
PS C:\workspace\git-command> git init
Initialized empty Git repository in C:/workspace/git-command/.git/
```
<br />

> #### git clone <url> : git repository 가져오기 (ex - git clone https://github.com/limwoobin/git-command)
    
```shell script
PS C:\workspace\git-command> git clone https://github.com/limwoobin/git-command
Cloning into 'git-command'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 15 (delta 1), reused 15 (delta 1), pack-reused 0
Unpacking objects: 100% (15/15), 2.72 KiB | 67.00 KiB/s, done.
```

<br />
    
<hr/>

> ## git add : 파일의 추적을 시작하겠다는 의미
<pre><code>
    디렉토리의 파일은 Untracked , Tracked 두 가지의 상태로 나누어짐.
    파일에 수정이 일어나면 git 이 파일의 변경을 감지해 사용자에게 알려주는 것과 같은 파일을 추적하는 상태를 Tracked.
    이와 반대로 파일을 저장소에 저장할 필요가 없어 파일이 변경되어도 git 이 신경쓰지 않는 상태를 Untracked.
    새로 만든 파일은 Untracked 상태. 이후 git add 를 통해 해당 파일을 add 해주면 해당 파일은 Staging area 에 저장
    즉 , Tracked 상태가 되어 git 이 파일을 추적하게 된다.
</code></pre>

<br />

> #### git add -h : git add 의 도움말을 볼 수 있음

```shell script
PS C:\workspace\git-command> git add -h
usage: git add [<options>] [--] <pathspec>...

    -n, --dry-run         dry run
    -v, --verbose         be verbose

    -i, --interactive     interactive picking
    -p, --patch           select hunks interactively
    -e, --edit            edit current diff and apply
    -f, --force           allow adding otherwise ignored files
    -u, --update          update tracked files
    --renormalize         renormalize EOL of tracked files (implies -u)
    -N, --intent-to-add   record only the fact that the path will be added later
    -A, --all             add changes from all tracked and untracked files
    --ignore-removal      ignore paths removed in the working tree (same as --no-all)
    --refresh             don't add, only refresh the index
    --ignore-errors       just skip files which cannot be added because of errors
    --ignore-missing      check if - even missing - files are ignored in dry run
    --chmod (+|-)x        override the executable bit of the listed files
    --pathspec-from-file <file>
                          read pathspec from file
    --pathspec-file-nul   with --pathspec-from-file, pathspec elements are separated with NUL character
```
<br />

> #### git add . 혹은 git add -A : 모든 변경사항을 add 한다.
<br />

> #### git add <file name> : file name 에 해당하는 파일을 추적
<br />
    
> #### git add -u : 변경사항이 있는 파일만 add ( 새로 생긴 파일은 제외 )
<br />

> #### git add -p 혹은 git add --patch : 변경사항을 보여주며 차례차례 commit 사항을 정할 수 있음    
    
```shell script
PS C:\workspace\git-command> git add -p
(1/1) Stage this hunk [y,n,q,a,d,e,?]?

y : 이 조각(hunk) 이 이후 커밋에 포함될 수 있도록 stage 시킨다
n : 이 조각이 이후 커밋에 포함되지 않도록 stage 대상에서 제외한다
q : 이 조각 및 이후 모든 조각들을 stage 시키지 않는다
a : 이 조각과 이후 현재 파일 내 모든 조각들을 stage 시킨다
d : 이 조각 및 이후 현재 파일 내의 모든 조각들을 stage 시키지 않는다
e : 현재 조각 내용을 직접 편집한다
? : 조각 관련 도움말을 표시한다

[출처] - https://nochoco-lee.tistory.com/40
```
<br />
<hr/>

> ### git commit -m "commit message" : 모든 파일의 변경사항 커밋하기

```shell script
PS C:\workspace\git-command> ls
README.md test.sh
```

```shell script
PS C:\workspace\git-command> vi test.sh

test
test23

:wq
```
test.sh 파일을 수정하고 저장

```shell script
PS C:\workspace\git-command> git add test.sh
PS C:\workspace\git-command> git commit -m "test commit"
[master 2993728] test commit
 1 file changed, 2 insertions(+)
```

git log 명령어를 이용해 커밋이 지정한 메시지로 정상적으로 저장되었는지 확인
```shell script
PS C:\workspace\git-command> git log

commit 299372869c6666d5908f3f89384e88cf9330af82 (HEAD -> master)
Author: limwoobin <drogba02@naver.com>
Date:   Sun Feb 14 17:21:10 2021 +0900

    test commit
```

<hr/>

> ### git clone "url" : git repository 받아오기

```shell script
PS C:\workspace\git-command> git clone https://github.com/limwoobin/git-command
Cloning into 'git-command'...
remote: Enumerating objects: 52, done.
remote: Counting objects: 100% (52/52), done.
remote: Compressing objects: 100% (44/44), done.
remote: Total 52 (delta 13), reused 14 (delta 1), pack-reused 0
Unpacking objects: 100% (52/52), 12.83 KiB | 94.00 KiB/s, done.
```

```shell script
PS C:\workspace\git-command> ls
git command/
```
git repository 를 받아온 후 내 디렉터리에서 확인 가능

<hr/>

> ## git remote : 원격 저장소를 관리할 수 있는 명령어

<br />

> #### git remote -v : 현재 디렉터리에 연결되어 있는 원격 저장소(repository) 확인

```shell script
PS C:\workspace\git-command> git remote -v
origin  https://github.com/limwoobin/git-command (fetch)
origin  https://github.com/limwoobin/git-command (push)
```

<br />

> #### git remote remove "name" : 연결되어있는 원격 저장소 제거

```shell script
PS C:\workspace\git-command> git remote remove origin
PS C:\workspace\git-command> git remote -v
```

```
origin : 원격 저장소의 이름
git clone 을 이용하면 자동으로 origin 이라는 이름의 원격저장소가 등록됨.
```

<br />

> #### git remote add `<별칭>` `<연결할 url>` : 내 디렉터리에 원격 repository 연결

<code> ex) git remote add origin https://github.com/limwoobin/git-command</code>

```shell script
PS C:\workspace\> mkdir test_dir
PS C:\workspace\> cd test_dir
PS C:\workspace\test_dir\> pwd
PS C:\workspace\test_dir\> C:\workspace\test_dir
```

테스트를 위해 빈 디렉터리 생성 후 접속

```shell script
PS C:\workspace\test_dir> git remote -v
fatal: not a git repository (or any of the parent directories): .git
```

빈 디렉터리이므로 위와 같은 메시지 발생. 
이 디렉터리를 git 으로 관리/사용하기 위한 설정 필요

```shell script
PS C:\workspace\test_dir> git init
Initialized empty Git repository in C:/workspace/test_dir/.git/

PS C:\workspace\test_dir> ls -al
drwxr-xr-x 1 drogb 197609 0  2월 16 18:43 ./
drwxr-xr-x 1 drogb 197609 0  2월 16 18:42 ../
drwxr-xr-x 1 drogb 197609 0  2월 16 18:43 .git/
```

위와 같이 git init 을 이용해 이 디렉터리를 git 으로 관리한다는 명렁어를 실행하면 .git 파일을 확인할 수 있음

```shell script
PS C:\workspace\test_dir> git remote -v
PS C:\workspace\test_dir>
PS C:\workspace\test_dir> git remote add origin https://github.com/limwoobin/git-command
PS C:\workspace\test_dir> git remote -v
origin  https://github.com/limwoobin/git-command (fetch)
origin  https://github.com/limwoobin/git-command (push)
PS C:\workspace\test_dir>
```

이 디렉터리와 git repository 가 연결된 것을 확인할 수 있음

<br />

<hr/>

> #### git diff : 로컬 디렉터리에 있는 파일과 최근 커밋된 파일과의 차이를 보여줌

로컬 디렉터리의 파일을 변경해 최근 커밋된 파일과의 차이를 만듦

```shell script
PS C:\workspace\git-command> ls
README.md test.sh
```

differentTest 라는 문구를 추가하고 저장.

```shell script
PS C:\workspace\git-command> vi test.sh
test

differentTest



:wq
```


```shell script
PS C:\workspace\git-command> git diff
warning: LF will be replaced by CRLF in test.sh.
The file will have its original line endings in your working directory
diff --git a/test.sh b/test.sh
index fb0d3cb..8c4b4a2 100644
--- a/test.sh
+++ b/test.sh
@@ -1,2 +1,3 @@
 test
-test23
+
+diffentTest
```

<br />
<hr/>

> ## git fetch : 원격 repository 의 파일을 다운받음
> (로컬 브랜치는 원래 가지고 있던 로컬 repository의 최근 커밋 위치를 가리키고, 원격 저장소 origin/master는 가져온 최신 커밋을 가리킴)

```shell script
PS C:\workspace\> git clone https://github.com/limwoobin/git-command git-command2
Cloning into 'git-command'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 15 (delta 1), reused 15 (delta 1), pack-reused 0
Unpacking objects: 100% (15/15), 2.72 KiB | 67.00 KiB/s, done.

PS C:\workspace\> cd git-command2
PS C:\workspace\git-command2> ls 
README.md
```

테스트를 위해 git-command2 라는 이름의 디렉터리로 clone

```shell script
PS C:\workspace\git-command2> vi test.sh

test

fetch test!!
~
~
~
~
~
~
~
~
~
~
~
:wq
```

```shell script
PS C:\workspace\git-command2> git add .
PS C:\workspace\git-command2> git commit -m "fetch test"
[master bcd186a] fetch test
 1 file changed, 1 insertion(+), 1 deletion(-)
PS C:\workspace\git-command2> git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 287 bytes | 287.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/limwoobin/git-command
   1d0df15..bcd186a  master -> master
```

테스트 파일인 test.sh 를 생성 후 저장 및 푸시

```shell script
PS C:\workspace\git-command> git fetch
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 267 bytes | 33.00 KiB/s, done.
From https://github.com/limwoobin/git-command
   1d0df15..bcd186a  master     -> origin/master
```

git-command 디렉터리로 돌아온 후 fetch 로 변경사항 내려받기
이 때 가져온 최신 commit 은 이름없는 로컬 branch 로 가져오게 됨.
FETCH_HEAD 이라는 이름으로 checkout 해서 확인 가능

```shell script
PS C:\workspace\git-command> git checkout FETCH_HEAD
PS C:\workspace\git-command> git branch 
* (HEAD detached at FETCH_HEAD)
  master
```

FETCH_HEAD 라는 이름의 branch 로 체크아웃하면 위와 같이 확인 가능


```shell script
PS C:\workspace\git-command> 
commit bcd186afa69eb27e6b06ea16b9b661e11edd2e46 (HEAD, origin/master, origin/HEAD)
Author: limwoobin <drogba02@naver.com>
Date:   Fri Feb 19 16:17:38 2021 +0900

    fetch test

commit 1d0df15b680e340599f31c30f8b75c7894420aea (master)
Author: limwoobin <drogba02@naver.com>
Date:   Fri Feb 19 15:52:49 2021 +0900

    git fetch test
```

위와 같이 fetch 로 가져온 최신 commit 은 
bcd186afa69eb27e6b06ea16b9b661e11edd2e46(HEAD , origin/master , origin/HEAD) 인것을 확인 가능

기존의 디렉터리의 최신 commit 은
1d0df15b680e340599f31c30f8b75c7894420aea (master) 인 것을 확인 할 수 있음

```shell script
PS C:\workspace\git-command> git checkout master
* master
PS C:\workspace\git-command> git merge
Updating 1d0df15..bcd186a
Fast-forward
 test.sh | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

다시 master branch 로 돌아와 FETCH_HEAD branch 와 merge.

```shell script
PS C:\workspace\git-command> git log
commit bcd186afa69eb27e6b06ea16b9b661e11edd2e46 (HEAD -> master, origin/master, origin/HEAD)
Author: limwoobin <drogba02@naver.com>
Date:   Fri Feb 19 16:17:38 2021 +0900

    fetch test

commit 1d0df15b680e340599f31c30f8b75c7894420aea
Author: limwoobin <drogba02@naver.com>
Date:   Fri Feb 19 15:52:49 2021 +0900

    git fetch test
```

![fetch](https://user-images.githubusercontent.com/28802545/108589005-931bd080-739f-11eb-93d1-e6a72b9549cc.png)

![fetch2](https://user-images.githubusercontent.com/28802545/108589019-a464dd00-739f-11eb-9f28-16bfbe2bf7f1.png)

https://backlog.com/git-tutorial/kr/stepup/stepup3_2.html (이미지 출처)

위와 같이 최신 커밋 bcd186afa69eb27e6b06ea16b9b661e11edd2e46에 (HEAD -> master, origin/master, origin/HEAD) 를 확인 가능
