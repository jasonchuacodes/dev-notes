Here's how to set your Git commit author and email:

1. Set your Git username:
   ```
   git config --global user.name "Your Name"
   ```

2. Set your Git email address:
   ```
   git config --global user.email "youremail@example.com"
   ```

3. Verify the settings:
   ```
   git config --global user.name
   git config --global user.email
   ```

4. If you want to set these for a specific repository only, navigate to that repository and use the commands without the `--global` flag:
   ```
   cd /path/to/your/repository
   git config user.name "Your Name"
   git config user.email "youremail@example.com"
   ```

5. To view all your Git configurations:
   ```
   git config --list
   ```

6. If you need to change these settings later, simply run the commands again with the new information.
