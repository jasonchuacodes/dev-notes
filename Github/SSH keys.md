### Checking for existing SSH keys
1. Before you generate a new SSH key, you should check your local machine for existing keys
```shell
$ ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

______

### Generating new SSH key
1.  Open Terminal.
2.  Paste the text below, substituting in your GitHub email address.
```shell
$ ssh-keygen -t ed25519 -C "your_email@example.com"
```

__________

### Adding your SSH key to the ssh-agent
1. Start the ssh-agent in the background.

```shell
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```
2.  Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace _id_ed25519_ in the command with the name of your private key file.

```shell
$ ssh-add ~/.ssh/id_ed25519
```

______________

### Adding a new SSH key to your Github account
After adding a new SSH authentication key to your account on GitHub.com, you can reconfigure any local repositories to use SSH.

1. Copy the SSH public key to your clipboard.
If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

```shell
$ cat ~/.ssh/id_ed25519.pub
  # Then select and copy the contents of the id_ed25519.pub file
  # displayed in the terminal to your clipboard
```
2. In your settings, go to `SSH` and `GPG` keys
3. Click `New SSH keys`
4. Give it a title describing your device like - `Windows_11/work`
5. Paste  the key which was copied using the command in step 1