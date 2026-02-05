
**2.1 Git Basics - Getting a Git Repository**

`git init` creates a new subdirectory .git containing repository files.

If you use `git clone` .git is created automatically.


`git status -s   or   git status --short` displays a simpler output of git status where
	?? represents untracked files
	A represents new files added to the staging area
	M represents modified files
	MM represents files with stages and unstaged changes

`$ cat .gitignore`          
`*.[oa]`                                  tells Git to ignore any files ending in ".o" or ".a"
`*~`                                         tells Git to ignore any files whose names end with a "~"

EXAMPLE .gitignore FILE:
```
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```
There can be multiple .gitignore files in different subdirectories of the repository

`git diff --staged` compares your staged changes to your last commit
`git diff` is only for your changes that are not staged