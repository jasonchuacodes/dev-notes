#### Problem
Cannot access files or run `pnpm dev` because of permission denied.

#### Reason
Permissions granted for current user doesn't include reading/writing in the current directory and its contents.

#### Solution
Change the ownership of the directory and grant all access with the ff command:
`sudo chown -R username:username /path/to/file/`

For example: 
```shell
sudo chown -R jason:jason /home/jason/Ubuntu_projects/online-auction/
```

Let's breakdown the command:
-   `sudo`: It stands for "superuser do" and is used to execute a command with administrative or root privileges. By using `sudo`, you temporarily elevate your privileges to perform actions that require administrative access.
-   `chown`: It is a command used to change the ownership of files and directories in Linux/Unix systems.
-   `-R`: It is an option for the `chown` command that stands for "recursive." When used, it changes the ownership of the specified directory and its contents, including all subdirectories and files.
-   `jason:jason`: The first "jason" represents the username, and the second "jason" represents the group name. In this case, both the user and group are set to "jason." By specifying `jason:jason`, you are assigning ownership of the directory to the user "jason" and the group "jason."
-   `/home/jason/Ubuntu_projects/online-auction/`: This is the path to the directory for which you want to change the ownership. Replace it with the actual path to your `/online-auction/` directory.

If you're unsure as to what the value for username is, run the following in the terminal and it will display your current username:
```shell
whoami
```
