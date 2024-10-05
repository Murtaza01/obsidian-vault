
# version control 

in order to keep track of your progress *(versions)*  we can create a new git that will keep track of our files inside our folder, using the code below:

`~ git init `


inside the folder you want to have your git, note that the folder would be hidden, and it wouldn't track progress until you run this command:

`~ git add 'file name'`

alternatively we can use the `.` to say everything in our folder:

`~ git add .`


you can see what files you are keeping track of inside your working directory using the below command:

`~ git status `

then you can use the command below to commit your progress and save it:

`~ git commit -m 'the code is complete'`

the `-m` stands from message and its the message  we see in our progress

to see your commits we use the command below:

`~ git log`

to revert your file to a specific version from your git, you can use the message as an indicator and using this command:

`~ git checkout 'file name'`

to know what is the difference between your files (the one you committed and the one you currently working on and may added some to it) you can use the command:

`~ git diff 'file name'`

# adding local git to the gitHub

when we want to remotely add our local files to our repositories we can use the below command:

`~ git remote add origin 'the repository url'`

the repository url is given inside the repository you create in github, and `origin` is the name you can give to your remote repository, but it is recommended to keep it as origin

this only creates a remote, in order to push our project that we have git in it, we use the following command:

`~ git push -u origin main`

# `gitignore`

sometimes you want to ignore some files, with `gitignore` you can do just that, you simply create a file called `gitignore` and inside put everything you want ignore

`~ touch .gitignore`

you should remove any files from the staging area, using the command 

`~ git rm --cached -r . `


# git clone

to clone a repository you simply take the url and then run this command:

`~ git clone url`

this will install the repository inside the directory that you ran the command in, make it locally yours, so you can modify on the repository


# git branch

a branch works as an alternative to the main commit, instead of committing changes to the main, you can branch your project to fix bugs or do some changes that might break the program, see the following commands:

`~ git branch 'branch name'`

to create a new branch

`~ git branch` 

to see the list of branches

`~ git checkout 'branch name'`

to switch to the named branch

and then to commit these changes we use the same commands we used in committing the main branch:

`~ git add .`  && `~ git commit -m 'message'`

to merge those changes we go to the main branch and run the command:

`~ git merge 'name of the branch'`

# pull request 

a pull request is when another person takes your repository and `fork` it, its not the same as cloning, because cloning is downloading the repository into your local computer

forking a repository makes another copy of that repository that you can do some changes to

when you do that *(fork a repository)* and add some changes, you can request a pull into the main repository, so that the owner of that repository might decided to *(pull)* that request

its different from push because its not coming from the owner, but rather from another person requesting a push *(pull)*

# gh 

a tool that help authenticate and verify your token with other useful things

```zsh
gh auth token // shows saved token
gh auth status // shows info
```


