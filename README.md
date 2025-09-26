# merge-conflict-demo
Learn how to resolve merge conflicts using vimdiff

To intentionally create a merge conflict in a GitHub repository and learn to resolve it with `vimdiff`, follow these step-by-step actions:

***

### 1. Setup: Create and Clone a Test Repo

- Create a repository on GitHub (e.g., `merge-conflict-demo`)
- Clone it locally:
  ```sh
  git clone https://github.com/yourusername/merge-conflict-demo.git
  cd merge-conflict-demo
  ```

### 2. Prepare a File

- Create `conflict.txt`:
  ```sh
  echo "This is line one." > conflict.txt
  git add conflict.txt
  git commit -m "Add conflict.txt"
  git push
  ```

### 3. Create Two Branches with Conflicting Changes

- Create and checkout branchA:
  ```sh
  git checkout -b branchA
  echo "This is branch A's change." >> conflict.txt
  git commit -am "Update conflict.txt in branchA"
  git push origin branchA
  ```
- Go back to main branch and make a different change:
  ```sh
  git checkout main
  echo "This is main branch's change." >> conflict.txt
  git commit -am "Update conflict.txt in main"
  git push
  ```

### 4. Try to Merge branchA into main (will cause conflict)

  ```sh
  git merge branchA
  ```

You will get a **merge conflict error** in `conflict.txt`. Git will mark the conflict with `<<<<<<<`, `=======`, and `>>>>>>>`.[1][2]

***

## Using vimdiff to Resolve the Conflict

- Launch vimdiff for the conflicted file:
  ```sh
  git mergetool --tool=vimdiff
  ```
- vimdiff will show:
  - Local changes (main branch)
  - Incoming changes (branchA)
  - Base (common ancestor)

- Edit and resolve the conflict using vimdiff's interface (merge, delete, or correct lines as needed).
- Save and exit vimdiff.
- Stage and complete the merge:
  ```sh
  git add conflict.txt
  git commit
  ```

***

## Summary Table

| Step        | Command                               | Purpose                       |
|-------------|---------------------------------------|-------------------------------|
| Repo setup  | git clone repo & cd                   | Local repo initialization     |
| Make file   | echo > conflict.txt; commit & push    | Establish base file           |
| Branch A    | git checkout -b branchA; edit; commit | New branch with changes       |
| Main branch | git checkout main; edit; commit       | Main branch changes           |
| Merge       | git merge branchA                     | Induce conflict               |
| Vimdiff     | git mergetool --tool=vimdiff          | Visual conflict resolution    |
| Commit      | git add conflict.txt; git commit      | Finalize resolved merge       |

***

This workflow will guarantee a merge conflict and walk you through resolving it interactively with vimdiff.[3][4][1]

[1](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts)
[2](https://codeforphilly.github.io/decentralized-data/tutorials/actually-using-git/lessons/conflicting-branches/)
[3](https://docs.github.com/articles/resolving-a-merge-conflict-using-the-command-line)
[4](https://stackoverflow.com/questions/161813/how-do-i-resolve-merge-conflicts-in-a-git-repository)
[5](https://docs.github.com/articles/resolving-a-merge-conflict-on-github)
[6](https://learning.nceas.ucsb.edu/2023-04-coreR/session_10.html)
[7](https://www.youtube.com/watch?v=mOJazBNrG-c)
[8](https://learn.microsoft.com/en-us/azure/devops/repos/git/merging?view=azure-devops)
[9](https://unstop.com/blog/merge-in-git)
