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

### 3. Empty website creation

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

Available themes are really great for a wide variety of content and tweaking is actually not as daunting as it looks at first to a newbie. I went with the second option and chose the hyde-y theme. You can go ahead an clone the theme into the ```themes/``` directory of your website (```~/mywebsite/themes/``` in my case).

Up until this point, we haven't deviated at all from the official docs. However, after this when following the docs blindly leads to major PITA later on, at least in my experience. Which is why, in Part 2, we are going to follow a different workflow to tweak and publish our website to github pages.


