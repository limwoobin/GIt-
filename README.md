# GIt-Command 


- #### git init : git 생성하기
```shell script
$ git init
Initialized empty Git repository in C:/workspace/git-command/.git/
```

- #### git clone <url> : git repository 가져오기 (ex - git clone https://github.com/limwoobin/git-command)
```shell script
$ git clone https://github.com/limwoobin/git-command
Cloning into 'git-command'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 15 (delta 1), reused 15 (delta 1), pack-reused 0
Unpacking objects: 100% (15/15), 2.72 KiB | 67.00 KiB/s, done.
```

<hr/>

## git add : 파일의 추적을 시작하겠다는 의미

- #### git add -h : git add 의 도움말을 볼 수 있음
```shell script
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
