### Problem
The  project `sph` is split into two main directories - `fe` and `be`. 
I need to install a linter package "husky" which needs the .git file. 

The problem is, the .git file is inside the parent directory and the package.json file is inside `fe` directory.

____

### Solution
You don't need to run `git init` again inside the "fe" folder. The root folder "sph" is already initialized as a Git repository, and running `git init` again in a subdirectory will create a separate repository within that subdirectory.

To resolve the issue and make Husky work, you can follow these steps:

1. Navigate to the root folder of your project ("sph") using the command line or terminal.

2. Run the following command to initialize the Git submodules, if you haven't done so already:
   ```
   git submodule init
   ```

3. Now, install Husky in the "sph" directory (not in "fe"):
   ```
   npm install husky --save-dev
   ```

4. After installing Husky, you can configure it in your project's package.json file, which should be located in the "fe" directory. Add the following lines under the "scripts" section of your package.json file:
   ```json
   "scripts": {
     "precommit": "lint-staged"
   },
   "lint-staged": {
     "*.{js,jsx}": "eslint --fix"
   }
   ```

5. Finally, you need to set up Git hooks using Husky. Run the following command from the root folder ("sph"):
   ```
   npx husky install
   ```

   This will set up the Git hooks required for Husky to run.

Now, when you commit your code, Husky will automatically run the ESLint linter on the staged JavaScript and JSX files before the commit is made.

Note: Make sure you have the required dependencies (`eslint` and `lint-staged`) installed in your project for the ESLint configuration to work properly. If you haven't already installed them, you can do so by running:
```
npm install eslint lint-staged --save-dev
```

Remember to adjust the ESLint configuration according to your project's needs.

`.husky/commit-msg`
```js
#!/usr/bin/env sh

. "$(dirname -- "$0")/_/husky.sh"

  

npx --no-install commitlint --edit
```

