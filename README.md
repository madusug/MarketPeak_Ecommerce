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

## Clone the repository on the Linux Server

To deploy the e-commerce platform, I cloned the GitHub repository to my EC2 instance. For this to work, I first created the ec2-instance on AWS.

![EC2](./img/6%20Set%20up%20EC2%20Instance.png)

My next step was to ssh into my instance. I did this by using `cd downloads` to go to the downloads folder. I then used `chmod 400 Dareykey.pem` to change the permissions for the pem file. This allowed me to ssh into my instance using, `ssh -i "Dareykey.pem ec2-user@ipaddress`.

![ssh](./img/7%20ssh.png)


I went on to install git using `sudo yum install git -y`. This would allow us to clone the repo from remote to instance.

![installgit](./img/8%20install%20git.png)

Next step was to clone the repository from my remote repo to my instance using HTTPS method. I did this using `git clone https://github.com/madusug/MarketPeak_Ecommerce.git`

![clone](./img/9%20clone%20git.png)


## Install a Web Server on EC2

Apache HTTP Server (httpd) is a free and open-source web server that delivers web content through the internet. Installing it on Linux EC2 instance allows me to host MarketPeak Ecommerce site. Next, I installed Apache Web Server on the EC2 instance. I ran the following commands: 
`sudo yum update -y`
`sudo yum install httpd -y`
`sudo systemctl start httpd`
`sudo systemctl enable httpd`

![installwebserver](./img/10%20Install%20Web%20Server.png)

This first updated the linux server and then installed httpd (Apache), started the web server and ensured it automatically starts on server boot.

## Configure HTTPD for Website

In order for us to see the website from the EC2 instance, I configured the HTTPD to poin tto the directory on the Linux server where the website code is tored. This is usually /var/www/html.

First, I prepared the web directory by clearing the default HTTPD web directory
Next, I copied the MarketPeak Ecommerce website files to it.

![configure](./img/11%20Configure.png)

Since I just cleared /var/www/html and copied the website files to it, I would need to reload the web server using: `sudo systemctl reload httpd`


## Access Website from Browser

With HTTPD configured and the website files copied to /var/www/html, MarketPeak_Ecommerce is now live on the internet. I ran into an issue when trying to view the website on a browser. This issue was that I only saw the text, "It works" when I used just my IP address. After some research, I discovered that you need to input the IPaddress alongside the name of the web folder. Eg: 3.28.7.19/2130_waso_strategy

![browser](./img/12%20Browser1.png)


## Continuous Integration and Deployment Workflow

In this section, I will be making some bug fixes and changes to the website. To do this, I will create a branch and make the changes on that branch.

Upon making the change to the index.html file, I staged the change and committed before pushing to my remote repo.

![change](./img/13%20changes.png)

### Pull Request

I created a pull request for this change on github

![PR](./img/14%20PR.png)

Now that the change has been merged with main on my repo, I want to be able to see the change on the browser when I visit the IP Address online.
For this to happen, I did the following:
1. Switch to Main 2. Pull from main on the remote repo

![Pull](./img/15%20pull.png)

Upon pulling the change, I went to the browser to check if the change was reflected on the browser but it wasn't. After some research, I decided to remove the content of /var/www/html and copy the website folder into /var/www/html again. Upon doing this, I could see the change reflected.
`sudo rm -rf /var/www/html/*`
`sudo cp -r ~/MarketPeak_Ecommerce/* /var/www/html/`

![Browser2](./img/16%20browser.png)
