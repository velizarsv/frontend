# How to remove node_modules

## Create a `.gitignore` file

1. Check for an existing `.gitignore` file in the project directory

```Bash
ls -a
```

2. If your project directory has a `.gitingore` file - skip to step 3. Otherwise, continue with:

Create a `.gitignore` file in the git repository

```Bash
touch .gitignore
```

## Remove the `node_modules` directory

3. Open up the `.gitignore` and add the following line to the file 

```
**/node_modules
```

4. Remove the `node_modules` folder from the git repository

```Bash
git rm -r --cached node_modules
```

## Commit All Changes

5. Commit the git repository without the `node_modules` folder

```Bash
git commit -m "Removed node_modules folder"
```

6. Push the change to the remote repo

```
git push origin main
```
  
7. Commit the `.gitignore` file

```Bash
git add .gitignore
git commit -m "Updated the .gitignore file"
git push origin main
```
