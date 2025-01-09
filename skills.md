This document compiles a list of skills/habits that I consider useful for working with me:


- using git:
    - suitable use of different branches (see [git flow branching model](), allthough this often is too complicated)
    - sometimes it is better to *rebase* instead of *merge* to keep the history simple
    - writing good commit messages, preferably using [conventional commits specification](https://www.conventionalcommits.org/en/).
        - use `git commit --amend` to improve the last commit (message)
        - use `git rebase -i HEAD~4` to improve an older commit (message)
    - use a prompt like https://starship.rs/ to stay informed about the state of your repos
    - configure and use `git difftool`
    - use git [aliases](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases)

- writing (python) code:
    - write unittests (often preferably before implementing the actual feature)
        - exception: experimental code which is not intended to be used again in several weeks
    - stick to pep8 and use a linter like black to ensure pep8 compatibility.
    - write docstrings and keep them up to data
    - use typing hints
    - check your assumptions in the code by generously using `assert`-statements
    - use interactive debugging, e.g. with [ipydex](https://github.com/cknoll/ipydex/)
    - avoid hardcoded file-paths
        - exception: specifying paths in **one central place** in the repository might be OK
        - consider obtaining paths from command line args, environment variables or configuation files.

