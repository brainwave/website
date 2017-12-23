---
title: "Using Hugo with Github Pages: Part 2"
date: 2017-12-23T19:08:00+05:30
type: "post"
draft: false
author: "Brahm Prakash Mishra"
tags: [Technical Articles]
categories: ["technical"]
---
The previous post featured on just getting a website up and running in hugo. This post focusses on customizing the website, to your liking and publishing it on github. There are three ways of accomplishing this in the documentation -

1. Make a docs folder in your website root, change the ```publishDir``` option in your config to docs. Then create an empty git repo *not* named as per <username>.github.io. It can be named anything else. Then upload that to github, and in repository settings choose to publish the website from ```docs``` folder. The issue is that this approach is for project pages, not the best suited for a personal website.

2. The alternative given is to go with the gh-pages approach, mentioned in hugo docs. However, even this approach is only for project pages. Your website ends up getting named as ```username.github.io/mywebsite/``` which is not very encouraging. You ideally want your website to be called just username.github.io.

3. You will get a username.github.io url for your homepage if you use ```publishDir = "."``` in your ```config.taml```. However, then your project root folder will get cluttered with a barrage of files and folders from the generated website. Its never a good idea.

The solution to above issues is actually to create two git repos. Github only publishes the repository ```<username>.github.io``` on a website by the same name.

Create a new repository on github with the name <username>.github.io. Also, create another git repo called website (or any other name you want to call the repo that stores your website root folder). Then, navigate to your website root folder and add a gitignore file that ignores the public directory of your website altogether.

```
echo "public">>.gitignore
git init
git remote set origin "<url to your repo>"
git status
git add .
git commit -m "First commit"
git push
```

This should push your website into github. However, notice that we didn't push the 'public' folder. This is because we will create a new git repository inside public, and set its upstream to <username>.github.io repository. That way, we can track the changes to website, and *generated* website separately, in separate repos. Also, files from the published website do not clutter the project root folder and remain insid the public folder.

```
cd public
git init
git remote set origin <url to your username.github.io repo>
git add .
git commit -m "Initial commit for published website"
git push
```
And done! Now if you navigate to <username>.github.io on your browser, you should see your published website up and ready. If it doesn't show up right away, but you didn't get any error emails, your website is still getting compiled, give it a while. You can always check if your website was successfully published by scrolling down the ```settings``` page of your <username>.github.io repository. It will show you a message saying your website was published successfully.

* A repository named username.github.io that tracks the content ```public``` folder of our repository.

In the next post, I'll be talking about basics of working with hugo, and how to modify the supplied theme elements to get desired look & feel and behavior of the website.

