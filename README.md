# My self Git Server

Sometimes I just need a private git server

# Prepare

1. I chose debian 10 as my server, so I need to install `git` on it by running:

```
sudo apt install git
```

2. Make the git-server-directory just like:`/home/$Your_User_Name/gitworkstation/`

3. Set the global git configuration by running:

   ```
   git config --global user.name $Your_name
   git config --global user.email $Your_email
   ```

- This will change the global git settings, if you just need change this project, you can use `--local` instead of `--global`

4. Create the first git project, goto `git-server-directory` and running:

```
git init --bare firstproject.git
```

- Please pay attention that this will create a directory under `git-server-directory` named `firstproject.git`,  and this project will only be edit by remote operation, this means `firstproject.git` is just for share

5. Now you can goto your local workstation and run:

   ```
   git clone $Your_User_Name@$You_IP_Address:/home/$Your_User_Name/gitworkstation/firstproject.git
   ```

   to clone the project.

- Git may warn you this is an empty repository but please ignore it.

6. Edit any thing in `firstproject.git` under the local workstation, just like:

   ```
   touch README.md
   ```

7. Add the new `README.md` file:

   ```
   git add README.md
   ```

- If you have many files, you can try `git add *`  to avoid input file and directory name one by one

8. Write a commit log:

   ```
   git commit -m 'Create README.md file'
   ```

9. Update to remote server:

   ```
   git push
   ```

- Sometimes you need run `git push origin master` etc for different branch

10. Update local repository by running:

    ```
    git pull
    ```

11. Chose history version:

    First you need to get the history hash by running:`git log`

    Second you just need run `git checkout %hash`

- This may cause you can't run `git pull` successfully unless run `git checkout master` before pull the remote repository.
