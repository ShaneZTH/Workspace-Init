# Git Setup and Commands

## Repo Setup
  <details>
  <summary>Create a new repo on the Command Line</summary>

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
  </details>

  <details>
  <summary>Push an existing repo from the Command Line</summary>
  
  ### Push an existing repo from the Command Line

  ```bash
  git remote add origin <your-git-repo-url>

  // To name(rename) the default branch as "master"
  git branch -M master
  git push -u origin master
  ```
  </details>

  <details>
  <summary>Connect Remote Repository via SSH</summary>

  ### Connect Remote Repository via SSH

  - Go to the .ssh/ subdirectory: `cd ~/.ssh/`
  - Check if you have an existing SSH key pair
  - Ohterwise, continue with the following steps
    - Generate a ssh key
      `ssh-keygen -t <SSH Key Types> -C "<comment>"`
      `ssh key gen`

      For *2048-bit RSA* key:
      `ssh-keygen -t rsa -b 2048 -C "<comment>"`

      Press `Enter` to set filename(key name) and passphrase (or leave as default)

  - Configure SSH
    - Attempts to ssh to GitHub 
      ```
      eval $(ssh-agent -s)

      // Replace github with your git host
      ssh -T git@github.com
      ```

    - Add the SSH private key to the ssh-agent
      ```bash
      // Format
      ssh-add <directory to private SSH key>

      // Example
      ssh-add ~/.ssh/id_rsa 
      ```

    - Evaluate the connection: `ssh -T git@github.com`


  - Try `git fetch` in your repo and see if passphrase is still needed (if no passphrase was set, then nothing should pop up)

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


## Other Useful tricks

### 1. Cherry-Pick

  `git cherry-pick <commitHash>`\
  作用：把commit复制到当前分支作为一个新的commit
  ```text
  a -> b -> c(HEAD)(master)
      |
      -> d -> e(branch B)
  ```
  `git cherry-pick <commitHash d>`

  ```text
  a -> b -> c -> d(HEAD)(master)
      |
      -> d -> e(branch B)
  ```
  
  *遇到冲突时可以用`--continue`(处理冲突后继续操作)/ `--abort`(放弃操作)*

[comment]: <> (&nbsp;&nbsp;&nbsp;&nbsp;`git rm -r --cached path_to_folder/`)
  

<!-- 
To use toggle in MD
<details>
  <summary>Detailed Steps</summary>

    ```bash
    
    ```
    
  </details> -->
