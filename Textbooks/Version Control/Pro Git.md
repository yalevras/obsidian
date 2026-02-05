
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
