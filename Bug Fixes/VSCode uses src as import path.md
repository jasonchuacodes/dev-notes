#### Problem
By default, VSCode uses src/file-to-path as the default autoimport path.
This causes a problem in NestJS as the modules are being checked based on the relative path.

#### Solution
To set VSCode to use relative paths instead of absolute paths in your imports, you can modify the "typescript.preferences.importModuleSpecifier" setting in your VSCode user settings.

1. Open the VSCode settings by pressing `Ctrl + ,` on Windows or `Cmd + ,` on Mac.
2. Make sure that you are on the `Workspace` tab 
3. Search for "typescript.preferences.importModuleSpecifier" in the search bar.
4. Click on "Edit in settings.json" to open the `settings.json` file.
5. Add the following line to the `settings.json` file:
   ```
   "typescript.preferences.importModuleSpecifier": "relative"
   ```
5. Save the file.

This should allow VSCode to use relative paths when importing files.