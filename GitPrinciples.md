
# Github Procedures


In order to maintain the workflow of this project in a way that allows us to easily revert bugs and see progress updates, we should strive to use Git as correctly as possible, the following are some aspects to these procedures.


## Branching
Branching is the act of treating your workspace as a tree, where branches are continually stemming from a central master branch. The master branch is the "clean" copy of your project, which promises to be bug free as possible for anyone who clones the repository.

![enter image description here](https://backlog.com/app/themes/backlog-child/assets/img/guides/git/collaboration/using_branches_001.png)
 
To tackle an aspect of the project, one should create a new branch based on the most relevant copy to the feature to be implemented. This is not always the master branch, which may not be updated with features still in testing.
Once a branch has features that are ready to add to the master branch, we can merge it in, and through that process prune the branch from the project if desired.

Branches should ideally always solve ONE issue, not be an entire feature. Remember that the more you add to one branch, the longer it's going to take to review and merge it. Push and create merge requests every time you have a piece working.

Branches should also be named appropriately, describing the issue they aim to fix. A good way to ensure that branches are uniform in naming is through the use of a board (Jira and Trello are popular ones) and simply give a branch the name as the number of an issue on the board.

    example: 
    Good Names: issue_923, infinite_training_fix, issue_923_fix_type_error
    Bad Names: bug_fix, creates_new_module, matan_fix_2



Whatever is decided, it's important to keep things uniform for easy searching of past and current issues.

To create a branch on Github:
1. Click the branch selector and type in a unique branch name and hit `Enter`, remembering that whatever branch you are currently looking at is the one this new one will branch from.
2. In your console at the repository address, type: `git checkout <NAME>`
3. You need to either stash or commit any changes to your current branch before checking out a new one.
4. **Never** push directly to the master branch, your code should only ever be on a sub branch that gets reviewed before merging.

![enter image description here](https://github-images.s3.amazonaws.com/enterprise/2.13/assets/images/help/branch/branch-selection-dropdown.png)

## Merges

When you have work that you believe is ready to be a part of the main project (ie. master branch), you create a Merge Request, essentially asking a teammate to take a look at what you have done and review it for quality. Code should never be merged in without the approval of a reviewer, unless the reviewer is aware of the changes before you have made them and they are 1-5 lines of code at most.

Also, merge requests should be often 5-10 file changes. The more changes to various files, the less predictable the review of the code, and the chance of bugs arising is inflated. Also, any more than 10 files changed often means you are trying to merge more than one functional change.

To make a merge request:
* Push all of your features to your branch, and on Github navigate to your branch's page. Click `New Pull Request`, where you'll be asked to decide what branch you are trying to merge into, generally this is the branch you stemmed from in the first place. 
* You will be given a series of changes between the branches, review these to make sure you want to have all of these merged in (ensuring no loose files such as .pycache are included). 
* Now choose a reviewer or multiple if desired, create a relatively descriptive section on your changes, specifying the functionality that is aimed for rather than the lines of code. 
* Create the request.


You should be checking daily under "Pull Requests" to see if someone has assigned you to review their code. If someone has, do the following:
* Under the "Files Changed" section, navigate each change, using the + button to leave comments as needed. This is for anything stemming from incorrect code to poor styling.
* Now checkout the branch and run the code (or paste into a Google Collab and test there.) 
* Leave a label on the request, whatever is appropriate. If it's good to go, simply label it "approved" and either merge it yourself or let the developer know.

You should also always be updating your working branch to account for approved merged. You want to avoid your branch being behind, as this causes merge conflicts.

![enter image description here](https://cdn0.tnwcdn.com/wp-content/blogs.dir/1/files/2018/10/Suggested-Changes-screenshot-796x375.png)
Example of leaving code specific comments on a line.

![enter image description here](https://help.github.com/assets/images/help/issues/issues_applying_labels_dropdown.png)
Example of labeling a merge request so that other developers know its status.
## Merge Conflicts
Conflicts are caused when two people are trying to edit and merge the same file. The repository has no idea how to handle this, and asks that you pick each conflict and determine the "correct" version.

For this reason, make sure you are never working on the same file as someone else, even if on different branches, since the feature to be merged in first will cause the subsequent feature to create a conflict, often resulting in lost work.

![enter image description here](https://help.github.com/assets/images/help/pull_requests/view-merge-conflict-with-markers.png)
Example of fixing a conflict

## Git Commands Reference

    git pull 
    --> pull any merged changes into your own working branch
    git add <File1> <File2>... 
    --> add changed files to commit
    git add -A 
    --> add all changed files to commit
    git commit -m "<Message>" 
    --> commit files with commit message
    git push 
    --> push commit to your working branch
    git checkout <Branch> 
    --> shift to another branch
    git stash 
    --> stash current changes in order to avoid commiting
    git reset --hard 
    --> erase all current changes on branch


![enter image description here](https://rubygarage.s3.amazonaws.com/uploads/article_image/file/599/git-cheatsheet-5.jpg)