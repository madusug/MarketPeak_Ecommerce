# MARKETPEAK_ECOMMERCE

This is to document the development of an e-commerce websitefor a new online marketplace named "MarketPeak". This platform will feature product listings, a shopping cart, and user authentication.

## Initiate Git Repository

For this step, I created a directory on my local repository and named it, "MarketPeak_Ecommerce". I proceeded to initialize Git within the directory by using `cd MarketPeak_Ecommerce` and `git init`. Doing this allows me to create a new git repository. I also created a README.md file to introduce and explain the project.

![GitInit](./img/1%20Git%20Init.png)

### Create Git Ignore file for .DS_Store

I created a git ignore file to avoid any issue with .DS_Store. The first thing I did was to create the .gitignore file using `touch .gitignore`. I then added .DS_Store to the .gitignore file and ran the following commands, `echo ".DS_Store" > .gitignore`, `echo ".DS_Store" >> ~/.gitignore_global`, `echo "._.DS_Store" >> ~/.gitignore_global`, `echo "**/.DS_Store" >> ~/.gitignore_global`, `echo "**/._.DS_Store" >> ~/.gitignore_global` and `git config --global core.excludesfile ~/.gitignore_global`.


## Stage and Commit the Template to Git

In this step, I will be adding the website files to the Git repository. To do this successfully, I need to first stage the website files `git add .`. Next, I set my git global configuration with my git username and email, `git config --global user.name "madusug"` and `git config --global user.email "jamesmadusha@gmail.com"`. Next step is to commit the changes in the staging environment `git commit -m "Initial commit with basic e-commerce site structure"`.

![StageCommit](./img/3%20First%20Stage%20and%20Commit.png)


## Push the code to your GitHub repository

Here, I created a repository on Github to allow for easy storage, sharing, and collaboration. I created the repository named "MarketPeak_Ecommerce" on my remote GitHub. To connect my remote repo to my local repo, I ran the following: `git remote add origin https://github.com/madusug/MarketPeak_Ecommerce.git`. To push the contents of my local repo to my remote repo, I used `git push -u origin main`.

![PushGit](./img/4%20Remote%20Repo.png)
![PushCode](./img/5%20Remote%20Add%20Push.png)
![RemoteAfter](./img/5%20After%20push.png)

