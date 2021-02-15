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

> #### git remote -v : 현재 디렉터리에 연결되어 있는 원격 저장소(repository) 확인

```shell script
PS C:\workspace\git-command> git remote -v
origin  https://github.com/limwoobin/git-command (fetch)
origin  https://github.com/limwoobin/git-command (push)
```

> #### git remote remove name : 연결되어있는 원격 저장소 제거

```shell script
PS C:\workspace\git-command> git remote remove origin
PS C:\workspace\git-command> git remote -v


```
