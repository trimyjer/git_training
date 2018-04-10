## An Awesome Git tutorial/reference
https://www.atlassian.com/git/tutorials/

## Basic Collaboration Workflow
Schematic demonstrating core concept: https://guides.github.com/introduction/flow/

Github's tutorial: https://services.github.com/on-demand/github-cli/
#### Download repo
0. Create repository on github website
1. `git clone <repo>` -- using link from github.com
2. `cd <repo>`
#### Create new branch and make changes (hack da mainframe)
3. `git checkout -b <branch_name>` (or `git branch <branch_name>` then `git checkout <branch_name>`)
4. Crush some code
5. `git commit -m "message"`
6. Crush some code
7. `git commit -m "message"`
#### Collaborate (& listen)
8. `git push origin <branch_name>`
9. File Pull Request (PR) on Github website
10. Request review on PR
11. Have reviewer merge PR
#### Synchronize Changes Locally
12. `git checkout master`
13. `git pull origin master`
14. `git branch -d <new_branch>` -- delete new_branch

## Forking Collaboration Workflow
Forking tutorial: https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow

Purpose of forking:
> The main advantage of the Forking Workflow is that contributions can be integrated without the need for everybody to push to a single central repository. Developers push to their own server-side repositories, and only the project maintainer can push to the official repository. This allows the maintainer to accept commits from any developer without giving them write access to the official codebase.

Note: Forking can also be used on smaller projects to prevent accidental commits pushed to the central repository
#### Create fork and download repo
0. Find repository on github website (a.k.a. "central" or "maintainer" repository) 
1. Create fork on github website
2. clone fork `git clone <repo>` -- using link from fork
#### Set references to remote git repos
3. set remote for central repository: `git remote add upstream <repo>` -- using link from central repository
4. view remotes: `git remote -v`  
   Note: This command should show `origin` associated with the url for your fork and `upstream` associated with the url for the maintainer repository.  
   Also note: `origin` and `upstream` are just common conventions but could actually be named anything 
#### Make changes and hack da mainframe
3. `git checkout -b <branch_name>`
4. Crush some code
5. `git commit -m "message"`
6. Crush some code
7. `git commit -m "message"`
#### Collaborate (& listen)
8. push commits to forked remote: `git push origin <branch_name>`
9. File Pull Request (PR) on Github website.  
   Note: this pull request will look a little different than above - the base will be `central/master` and the comparison branch will be `your_username/new_branch`
10. Request review on PR
11. Have reviewer merge PR
#### Synchronize Changes Locally
12. `git checkout master`
13. `git pull upstream master`
14. `git branch -d <new_branch>` -- delete new_branch

## Current ERI Collaboration Workflow

#### Download repo
1. `git clone <repo>` -- using link from github.com
2. `cd <repo>`
#### Make changes and hack da mainframe
3. `git checkout -b dev`
4. Crush some code
5. `git commit -m "message"`
6. Crush some code
7. `git commit -m "message"`
8. `git push origin dev`
#### Merge changes locally using rebase strategy and push changes to origin/master
9. `git checkout master`
10. `git pull origin master` -- sync changes with origin/master
11. `git checkout dev`
12. `git rebase master` -- move dev branch to tip of master branch
13. `git checkout master`
14. `git merge dev`
15. `git push origin master`

### Disadvantages of ERI workflow
- harder to review other's code because there is no centralized location (such as a Pull Request) for discussion
- authors must merge their own code locally which does not encourage the code review process through PRs
- many steps required for merging/pushing changes
- harder to collaborate on code on the same branch
- harder to incorporate continuous integration
