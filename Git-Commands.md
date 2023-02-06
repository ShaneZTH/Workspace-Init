# Git Setup and Commands Combination

## Repo Setup
  <details>
  <summary>Expand</summary>

  ### Create a new repo on the Command Line

  ``` bash
  git init
  git add README.md
  git commit -m "init"

  // To name(rename) the default branch as "master"
  git branch -M master

  // For HTTPS connection mode
  git remote add origin <your-git-repo-url>
  git push -u origin master
  ```

  ### Push an existing repo from the Command Line

  ```bash
  git remote add origin <your-git-repo-url>

  // To name(rename) the default branch as "master"
  git branch -M master
  git push -u origin master
  ```
  </details>

</br>

## Git Username/Email Configuration

### To set your global username/email configuration:
  - Open the terminal

  - Set your username:
    `git config --global user.name "FIRST_NAME LAST_NAME" `

  - Set your email address:
    `git config --global user.email "MY_NAME@example.com" `
  

### To set repository-specific username/email configuration:
  - From the command line, change into the repository directory

  - Set your username:
    `git config user.name "FIRST_NAME LAST_NAME"`

  -Set your email address:
    `git config user.email "MY_NAME@example.com"`

  - Verify your configuration by displaying your configuration file:
    `cat .git/config`

## Delete Branch

- **Local Branch**
  - To delete local branches with no exception:
    -  `git branch -d <local-branch>`
  - To delete local branches with force:
    - `git branch -D <local-branch>`

- **Remote Branch**
  - To delete a *remote* branch:
    - `git push <remote_name> --delete <branch_name>`
    - `git push origin --delete <remote-branch-name>`
  - Simple version:
    - `git push <remote_name> :<branch_name>`

## Git Stash
- Stash (all): `git stash [-a/--all]`
- Notes:
  - `git stash pop` throws away the (topmost, by default) stash after applying it
  - `git stash apply` leaves it in the stash list for possible later reuse (or you can then git stash drop it)
  - `git stash pop` **OR** `git stash apply && git stash drop`

## Update current branch with latest changes
- First do `git checkout master` and `git pull` to retrieve all updates (Not pulling from the master branch could result in not getting all latest updates)
- Then, 
  - `git rebase origin/master` [Preferred]
  - `git merge master` [Avoid] This would mess up the commit timeline

## Rename a Branch
- Rename the Git branch locally with the `git branch -m new-branch-name`
- Push the new branch to your GitHub or GitLab repo
- **Delete** the branch with the old name from your remote repo

## Git Commons
- Prevent any `.class` file to be versioned (didn't include them in the `.gitignore` initially)
  -  `git rm -r --cached *.class`

- Remove a folder from Git repo without deleting it from local machine (stop tracking)
  - Add the folder path to `.gitignore` file
  - Remove the folder from local git tracking<br/>
    - `git rm -r --cached path_to_folder/`
  - Push changes to git repo 

[comment]: <> (&nbsp;&nbsp;&nbsp;&nbsp;`git rm -r --cached path_to_folder/`)
  

<!-- 
To use toggle in MD
<details>
  <summary>Detailed Steps</summary>

    ```bash
    
    ```
    
  </details> -->