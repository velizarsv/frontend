### Basic Questions
<details>
<summary>1. What is Git?</summary>
Answer: Git is a distributed version control system that allows multiple developers to work on a project simultaneously without interfering with each other’s changes. It tracks changes in source code during software development.
  </details>
<details>
 <summary>2. What is the difference between git clone and git fork?</summary>
Answer: git clone creates a local copy of a repository from a remote source, allowing you to work on it locally. git fork, typically used in platforms like GitHub, creates a personal copy of someone else's repository under your account, allowing you to propose changes via pull requests.
  </details>
  <details>
<summary>3. How do you stage changes in Git?</summary>
Answer: You stage changes using the git add <file> command. This prepares the specified file for the next commit. You can also use git add . to stage all modified files in the current directory.
</details>
  
### Intermediate Questions
  <details>
 <summary> 4. What is the purpose of branches in Git?</summary>
Answer: Branches allow developers to work on different features or fixes independently without affecting the main codebase. This enables parallel development and helps manage different versions of a project.</details>
<details>
 <summary> 5. Explain the difference between git merge and git rebase.</summary>
Answer: git merge combines changes from one branch into another, creating a new commit that includes both histories. In contrast, git rebase moves or combines a sequence of commits to a new base commit, resulting in a linear project history.
</details>
<details>
 <summary>6. How can you resolve merge conflicts in Git?</summary>
Answer: Merge conflicts occur when two branches have competing changes. To resolve them, you must manually edit the conflicting files to choose which changes to keep, then stage the resolved files with git add <file> and complete the merge with git commit.</details>
  
### Advanced Questions
<details>
 <summary>7. What are Git tags and how are they used?</summary>
Answer: Tags are references that point to specific commits, often used to mark release points (e.g., v1.0). They can be lightweight (just a pointer) or annotated (with metadata). You create tags using git tag <tagname>.</details>
<details>
 <summary>8. Describe how you would revert a commit that has already been pushed to a remote repository.</summary>
Answer: To revert a pushed commit, use git revert <commit-hash>. This creates a new commit that undoes the changes made by the specified commit without altering the project's history.</details>
<details>
 <summary>9. What is the purpose of .gitignore?</summary>
Answer: The .gitignore file specifies intentionally untracked files that Git should ignore. This is useful for excluding temporary files, build artifacts, or sensitive information from being committed to the repository.
Expert Questions</details>
<details>
 <summary>10. How do you handle large binary files in Git?</summary>
Answer: For large binary files, it's recommended to use Git LFS (Large File Storage). This extension allows you to store large files outside of your main repository while still tracking them with Git.</details>
<details>
 <summary>11. Explain how you would implement a continuous integration workflow using Git.</summary>
Answer: A continuous integration (CI) workflow typically involves setting up automated tests that run whenever code is pushed to the repository. You can use services like Jenkins or GitHub Actions to automate testing and deployment processes based on specific branch events.
 </details>
<details>
 <summary>12. Can you explain what "cherry-picking" means in Git?</summary>
Answer: Cherry-picking allows you to apply a specific commit from one branch onto another branch without merging all changes from the source branch. This is done using git cherry-pick <commit-hash>.
</details><details>
 <summary>13. Create and switch to the new branch</summary>
Answer: git checkout -b feature-branch-name <commit-hash>.
</details>
