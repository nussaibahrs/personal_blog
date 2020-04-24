---
title: Hello world, and I finally switched to blogdown
author: ''
date: '2019-03-03'
slug: hello-world-and-i-finally-switched-to-blogdown
categories:
  - R
  - blog
tags: ["blogdown"]
image:
  caption: ''
  focal_point: ''
---
The website is finally *kinda* live! I wonder how many hello-world posts I've written over the past 12 years (I do tend to fall in and out with blogging A LOT) but as of today, I'm saying goodbye to Wordpress and all its faff. I've spent all weekend setting up by first `blogdown` website in **R** and I can't believe how easy it has been. The plan is to use this space as a portfolio for [work](/#projects) with open and reproducible science in mind,  [tutorials](/tutorial/) and experiments in dataviz, because my folder organisation skills are practically inexistent so everything I currently have is one big mess. 

There's currently quite a lot of pages that either say "Under construction" or "Text goes here". Bear with me, I'm going to be updating things here as I go. I'm going to turn commenting on asap and it would be great to get some suggestions/critique if you have any. That's it for now! 

If you're interested in knowing how I set up this blog, see below.

### Setting up a `blogdown` site

Much of the information I used to set up this website came from [the blogdown book](https://bookdown.org/yihui/blogdown/). Just follow it to the letter and you'll be fine.

* I'm hosting this website on [Netlify](http://netlify.com/) using GitHub. So to start with, make sure you have GitHub account and create a repository for your blog (mine is called blogdown). You also need to have Git installed on your computer and integrate it into R. You can read more about how to do this on: [Initial set up and Create a local Git repository] (http://r-pkgs.had.co.nz/git.html#git-init).

*  Open R Studio and create a **New Project**, **Choose New Directory** and then **select Website using blogdown**. Follow through the instructions, and click on **Create Project**. You will also be prompted to link your GitHub repository to the project. Alternatively, this can be done under *Tools* -> *Project Options*. 

* Once your blog is set up in RStudio, just click on Commit to bring all the newly downloaded files and folders under version control. *Note:* You always need to write a commit message to be able to Commit the changes. This is already good practice so that future collaborators (including you) knows what the edits were for. 

* You can use now preview your new blog locally using `blogdown::serve_site()`. You'll be provided with a local server address which you can then use in your browser. To stop the server, either restart R or use `servr::daemon_stop(1)`. 

*  To write posts choose **New Post** from the Addins menu at the top. You'll be prompted to add some metadata, and if you're like me, your first post will be entitled "Hello World" (I'm boring that way). The formatting is done using Markdown so if you're unfamilliar with it, here's a [cheatsheet](https://www.rstudio.com/wp-content/uploads/2016/03/rmarkdown-cheatsheet-2.0.pdf) to get you started. 

* Final step: get a [Netlify account](http://netlify.com/) and choose **New Site from Git**, select GitHub as your host space and then choose the repository in which your blog was installed. Click on *Deploy Website* and congratulations, your website is now live!

The above was written for a user who has relative experience with R and GitHub. There'll be a lot of trials and error but if you're like me, you're gonna have fun figuring things out. Again, the [blogdown: Creating websites with R Markdown](https://bookdown.org/yihui/blogdown/) is your first to-go resource if you're actually planning to set up your blog using `blogdown`. 

Until next time!
