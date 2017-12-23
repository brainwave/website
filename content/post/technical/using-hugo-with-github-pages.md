---
title: "Using Hugo with Github Pages: Part 1"
date: 2017-12-23T01:06:37+05:30
type: "post"
draft: false
author: "Brahm Prakash Mishra"
tags: [Technical Articles]
categories: ["technical"]
---
This post explores how to go about building a website with [Hugo](gohugo.io), a static website generator. I found easy to get confused, even frustrated, while attempting to build my first real website. If you are like me and have never dabbled in web development before, this post is for you.

### 1. Overview and Workflow
We are going to do the following in order -

1. Install hugo
2. Create an empty website
3. Test our setup with local webserver
4. Use a hugo theme
5. Publish a sample website
6. Customize our site

The docs are indeed quite sufficient for [1] through [5]. But [6] was where I faced some real struggle so thats the bit I am going to focus on.

### 2. Installing Hugo

Head over to the well illustrated steps on [Install Hugo](https://gohugo.io/getting-started/installing/) page. On Arch Linux system, hugo was actually present in the official repos and installing it was as easy as

```
sudo pacman -S hugo 
```

### 3. New website creation

The following commands create a new website, and start a local hugo server to serve it at a specific port on localhost. In my case it was `//localhost:1313/`. 
```
hugo new site mywebsite
cd mywebsite
hugo server -D
```

At this point, you can browse to that IP address on your browser, and find out of hugo is working. It won't display anything but anything other than a "not found" page means that hugo is responding to requests.

The generated has most of the folder structure needed for themes to function properly. You have two possible courses of action from this point onward.

1. Create your own site design from Hugo templates, *or*
2. Use an existing theme and tweak it to your needs 

Available themes are really great for a wide variety of content and tweaking is actually not as daunting as it looks at first to a newbie. I went with the second option and chose the hyde-y theme. Clone any theme from the hugo [website](https://themes.gohugo.io)  into the ```themes/``` directory of your website (```~/mywebsite/themes/``` in my case).

```
cd themes/
git clone https://github.com/enten/hyde-y
```

Now that we have the theme, we need to activate it by creating adding this to the top of the config.toml
```
publishDir = "public"
```
Additionally, we need to make the config file such that we can easily publish it on github. I added an option to use a public/ directory for publishing my website. Additionally, hugo websites do not render correctly on github pages unless the baseurl is set to root (i.e, setting it to username.github.io doesn't work very well).  So we need to set the baseurl to root.
```
baseurl = "/"
publishDir = "public"
```

Subsequently, we want to run the actual command to publish our website into the public folder.
```
hugo
```

And done! We have a functional website, published from content we tested locally. All that remains now is to publish on github, to get the website up and running. Subsequently, we might want to explore ways of tweaking the look and behavior of our website. Do not add any folder to version control yet. The reason for this is that any theme you cloned from a git repo would have come with its own version control files inside themes/.git. So, to add this to your repo, you need to use git submodules. However, in my testing, I found it quite cumborsome to use. Primarily because, if I am creating a number of websites that use the same theme, I want to sync all my changes to theme elements across all. This means, I need to make changes directly to content files of my theme. I can't just make local changes per website in the /layouts folder as is the suggested method. To actually use the submodule method while making changes to the theme folder, I need to fork the theme, clone 'that', then add submodule and then follow the submodule workflow. Its a lot of hassle for something very simple, which is why  I went with a workaround instead.

The quick fix that I found was to delete the .git folder inside the downloaded theme. This makes git treat themes just like any other file, and you do not have to mess with git submodules. You can make changes either directly inside the theme folder, or add your customizations to /layouts foldre.

However, before doing any of this, make sure that the license of the theme you are using permits you to do so. If not, you might be in violation of license terms.
Up until this point, we haven't deviated at all from the official docs. However, after this when following the docs blindly leads to major PITA later on, at least in my experience. Which is why, in Part 2, we are going to follow a different workflow to tweak and publish our website to github pages.

In the next post, I'll be adding version control to my website, and establishing a workflow to manage and publish it on github pages.



