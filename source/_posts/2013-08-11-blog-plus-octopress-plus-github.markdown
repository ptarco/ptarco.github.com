---
layout: post
title: "Blog + Octopress + GitHub"
date: 2013-08-11 18:04
comments: true
categories: 

keywords: "blog, octopress, this, GitHub, Blog + Octopress + GitHub"
description: "Blog + Octopress + GitHub"

---

---

<!--more-->
### Quick Summary for creating and deploying a post
{% codeblock %}
$ rake new_post["New Post"]
$ rake generate
$ git add .
$ git commit -am "Some comment here." 
$ git push origin source
$ rake deploy
{% endcodeblock %}

###Installation Process
Go to the terminal and clone the Octopress repo:
{% codeblock %}
git clone git://github.com/imathis/octopress.git octopress
cd octopress
{% endcodeblock %}
###Check the version of Ruby is 1.9.2. This version is required.
{% codeblock %}
ruby --version
bundle install
{% endcodeblock %}
###This command installs Octopress
{% codeblock %}
rake install
{% endcodeblock %}
###Deploying to Github
Create a new Github repository. If you are creating a personal blog create a repo called:
{% codeblock %}
username.github.com
{% endcodeblock %}
After creating the repo, run the following command.
{% codeblock %}
$rake setup_github_pages
{% endcodeblock %}
Which is supposed to:
___
* init a git repo
* rename the branch from master to source
* add your repo to origin.
___

Running the previous command shows this:
{% codeblock %}
Enter the read/write url for your repository
{% endcodeblock %}
You have to enter it like this:
{% codeblock %}
git@github.com:username/username.github.com.git
{% endcodeblock %}
For me it didn’t rename the branch from master to source or add my remote repo. I did it manually (see below)
###Add your remote repo
Check what remote repositories you have:
{% codeblock %}
git remote -v
{% endcodeblock %}
My output was:
{% codeblock %}
octopress   git://github.com/imathis/octopress.git (fetch)
octopress   git://github.com/imathis/octopress.git (push)
{% endcodeblock %}
To add your repo do:
{% codeblock %}
git remote add origin git@github.com:username/username.github.com.git
{% endcodeblock %}
Rename the branch from master to source
{% codeblock %}
$git branch
* master
$git branch -m master source
$git branch
* source
{% endcodeblock %}
Preview on development stage
{% codeblock %}
$ rake preview
{% endcodeblock %}
Then browse to:
{% codeblock %}
localhost:4000
{% endcodeblock %}
If you get this error:
{% codeblock %}
Sorry, I cannot find /
{% endcodeblock %}
Read this link: Deploying to a Subdirectory
###First push to Github
{% codeblock %}
$rake generate
$git add .
$git commit -am "First deploy to github." 
$git push origin source
$rake deploy
{% endcodeblock %}
Create a new posting
{% codeblock %}
$rake new_post["Creating a Github Blog Using Octopress"]
{% endcodeblock %}
Go to the app folder source/_posts to find the new posting
Edit the posting and then follow these steps
{% codeblock %}
$rake generate
$git add .
$git commit -m "Initial blog post." 
$git push origin source
$rake deploy
{% endcodeblock %}
Add a custom domain
Go to source folder and create 2 files :
(mate if you are using Textmate)
{% codeblock %}
cd source
mate CNAME
mate .nojekyll
{% endcodeblock %}
Open the CNAMe file and this line:
{% codeblock %}
www.yourdomain.com
{% endcodeblock %}
The NoJekyll file will make Octopress works in Github Pages.
Push again to github
{% codeblock %}
rake generate
git add .
git add -am 'domain configuration'
git push origin source
rake deploy
{% endcodeblock %}
Github need time to read your CNAME and updating the sites.
___