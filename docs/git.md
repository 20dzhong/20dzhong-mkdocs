# Github
Git is a version control system, it allows people to clone repositories, upload their own works, and collaborate with others

The examples will be using command line / terminal to interact with git, and of course, to use git, you have to download it first: 
[https://git-scm.com/downloads](https://git-scm.com/downloads)

**https://github.com/JohnDoe/Repo** will be used as an example (it doesn't exist), it will be substituted by your desired repository

## Cloning a Repository 

* Open terminal and change into your desired directory
```bash
git clone https://github.com/JohnDoe/Repo
```

## Pushing a existing  project to Github

* First go to your Github page and create a new Repository

* Open terminal and change into your desired directory

* If it's your first time using github, you'll have to set up your username and password
```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

* Initiate a repository in your current project folder
```bash
git init
```

* Add all the file to the prepare for commit
```bash
git add .
```

* Commit your progress (save a checkpoint basically), the commit message can be whatever you want
```bash
git commit -m "First Commit"
```

!!! info "Setting up your url"
    * Link your local directory to your Github directory:
        * if you are changing the link:
        ```bash
        git remote set-url origin https://github.com/JohnDoe/Repo
        ```
        
        * if you are adding the link:
        ```bash
        git remote add origin https://github.com/JohnDoe/Repo    
        ```

* Double check to make sure you have to right link
```bash
git remote -v 
```

* Finally push your commits and changes to the GitHub
```bash
git push -u origin master
```
