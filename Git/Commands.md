> First of all, it wont work if you dont have git installed on your machine

you can find more information on [Git Documentation](https://docs.github.com/en/get-started/using-git/about-git) page.

---

```
git init
```
Creates a new repository, with the data strucutre for git version control inside a hidden folder.
Usage:
```
mkdir my_project
cd my_project
git init
```
---
```
git clone
```
Believe me, it does exactly it says... clones an existing repository!
Usage:
```
git clone https://github.com/user/repository.git
```
---
```
git add
```
this code performs staging, the first step of an two-step process. with this proccess, you can add on your code timeline / history, all the advancements with specified details in each advancement.
its like creating a new branch, just for a new code with a new feature being added via `git add`, and then the second part of the command:
```
git commit
```
will launch this stage branch, as an snapshot!

---
