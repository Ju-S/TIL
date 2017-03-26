# Git
---

Download Git Bash
---
[Download Git](https://git-for-windows.github.io/)  
Download and Install.

How to use  
---
First, **create repository** in **github**.  
Then, create some folder for **connect with github**.  
Second, Right-Click on **folder** and select the **Git Bash Here**.  
Third, type **`git init`** on git bash. Now, **folder is can use for github!**  

Quick Manual
---
1. Do "How to use".
2. Create or modify the file.
3. See folder status using `git status`.
4. Add file on staging area using `git add "file"`.
5. Descript about file using `git commit -m "description"`.
6. Connect folder with github using `git remote add origin githubRepsitoryUrl`.
7. Push file using `git push origin master`.
8. Now, files are on github.

Command
---
##### git status  
`git status` is show **git status**(create file or folder, modified file and etc...) about **folder, connected github**.

##### git add  
`git add "file name"` is add file on staging area **(Not on github)**.

##### git commit
`git commit -m "commit text"` is commit the file when use cammand, `git add`. Commit is description of file.  

### git remote
---
##### git remote add
`git remote add origin https://github.com/Ju-S/TIL` is **connect the folder with github.** Now, we can **push** on github.  

##### git remote -v
`git remote -v` is show connect status of folder.

---
##### git push
`git push origin master` is push the **staging area file** on github.
