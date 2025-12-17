#  1. Affirmation of the Day: 

**_I am becoming a Git expert – version control is the foundation of modern DevOps._**


# 2. Core concepts of GIT :

1. Repository = project folder with history
1. Commit = snapshot of changes + message
1. Branch = independent line of development (main/master is default)
1. Staging area = what you select to commit (git add)
1. Remote = GitHub (origin)

# 3. Git Introduction – Commits & Branching

## Git Basics Recap
- Git: Distributed version control system.
- Tracks changes, enables collaboration, rollback, branching.

## Key Git Workflow
1. Modify files
2. `git add <file>` → stage changes
3. `git commit -m "message"` → create snapshot
4. `git push` → send to remote (GitHub)

## Important Commands
| Command                    | Purpose                              | Example                              |
|----------------------------|--------------------------------------|--------------------------------------|
| git status                | See what's changed/staged            | git status                           |
| git add <file>            | Stage file for commit                | git add notes/day3.md                |
| git add .                 | Stage all changes                    | git add .                            |
| git commit -m "msg"       | Commit staged changes                | git commit -m "Add Day 3 notes"      |
| git log                   | View commit history                  | git log --oneline                    |
| git branch                | List branches                        | git branch                           |
| git branch <name>         | Create new branch                    | git branch feature-login             |
| git checkout <branch>     | Switch branch                        | git checkout feature-login           |
| git switch <branch>       | Modern alternative to checkout       | git switch main                      |
| git checkout -b <name>    | Create + switch to new branch        | git checkout -b day3-practice        |
| git merge <branch>        | Merge branch into current            | git merge feature-login              |
| git push origin <branch>  | Push branch to GitHub                | git push origin main                 |

## Why Branching?
- Work on features/bugs without breaking main code.
- Standard flow: main → create feature branch → work → PR → merge.

## Best Practices
- Commit often, small logical changes.
- Write clear commit messages (imperative mood: "Add X", "Fix Y").
- Never commit sensitive data (use .gitignore).


# 4. Clone an external repo, create a branch, make changes, commit, and push to your own fork.

* `cd ~/git-practice                  # or any folder`
* `git clone https://github.com/jwasham/coding-interview-university.git`
* `cd coding-interview-university`
* `ls                                 # see contents`
* `git checkout -b pavan-git-practice-001  #Create and switch to a new branch`
 
<!-- Pavan Kumar's practice on Dec 16, 2025 -->
- Practicing Git branching and commits for DevOps journey. ## ADD Lines at end of the README.md file and Save the file.

#Stage and commit
* `git status                         # see changes`
* `git add README.md`
* `git status                         # should show staged`
* `git commit -m "Add practice note from Pavan Kumar - Day 3 Git exercise"`

# 5.Final Push & Cleanup
git switch main
git add .
git commit -m "Day 3: Complete Git intro and practice"
git push origin main
