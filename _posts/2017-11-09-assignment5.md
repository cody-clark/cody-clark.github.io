# Creating an Online Portfolio with Jekyll

## Overview

An online portfolio can only help the job hunt, but creating and maintaining sites through WordPress is a pain, and services like Wix and Weebly are expensive or make you use stupid URLs. 

Jekyll is a static site generator that can easily build websites by running a single line of code; unfortunately, generating a Jekyll site generally requires setting up a development environment and the knowledge of Ruby. This guide will show you how to set up your own portfolio site for free without typing a single line of code.

## Objectives

1. Create an online portfolio for free to showcase your work 
1. Customize your site without coding or using any WYSIWYG editors
1. Use Markdown to add your portfolio pieces

## Getting Started

**Create a Github Account**

1. Go to [github.com](https://github.com/).
1. In the upper right-hand corner, click **Sign up**.
1. Enter your Username, Email address, and Password in the respective fields, then click **Create an account**.

   > **Note:** Your Username will be your site’s URL, so make sure your username reflects you and your personal brand. For example: codyjtclark.github.io  

1. Select the free plan, Unlimited public repositories for free, if it already isn’t checked, then click **Continue**.
1. Scroll down to the bottom of the page if necessary, then click **skip this step**.

   > **Note:** Never give information if you’re not required to. 

**Find a Theme and Fork the Repository**

1. Go to http://jekyllthemes.org/themes/moon/, then click **Homepage**.
	
   > **Note:** You can browse more themes at jekyllthemes.org. While setting up hosting on Github and editing certain files will be the same, other features may not be available. 

1. In the upper right-hand corner, click **Fork**.
1. Verify your email address if prompted. 

**Change the Repository Name to username.github.io**

1. Go to github.com/YourUsername
1. Click on your newly forked repository.
1. In the upper middle page, click **Settings**.
1. Under Repository name, type username.github.io.

   > **Note:** Replace username with your actual username. This will be your site’s URL.

**Customizing Your Site**

1. Delete the Placeholder Pages
1. From your Repository page, **click _posts**.
1. Click **2012-05-22-readability-post.md**.
1. On the right side of the page, click the trashcan icon.
1. Scroll down, then click **Commit changes**.

   > **Note:** It’s bad practice to directly merge changes to the Master, but best Git practices are out of the scope of this tutorial. 

1. Repeat these steps until all of the pages are deleted.

**Edit the _config.yml**

1. From your Repository page, click **_config.yml**.
1. Click the pencil icon to edit the file.
1. Change the Title to your name.
1. Change the Bio to your tagline. 
1. Change the Description to fit you.

   > **Note:** This Description will be used to describe your site as it appears in Google search results. Once the Google crawlers log this description, it will not change until your site is crawled again. Definitely proofread this. 

1. Scroll down until you see # Social. 

   > **Note:** The octothorp (#) tells the file not to render the text by rendering the line as a comment. If you don’t have an account or don’t want to link to it from your portfolio, just add a # to the beginning of the line. Similarly, if you want to link to an account, delete the # then replace username with your account’s username.   

1. When you’re finished, scroll down, then click **Commit changes**.

**Edit the about.md page**

1. From your Repository page, click **about**, then click **index.md**.
1. Click the pencil icon to edit the file. 
1. Use the description you wrote earlier, or write something else. 
1. For text formatting options using Markdown, please refer to [this page](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf).

**Add a Blog post**
1. From your Repository page, click **_posts**, then click **Create new file**.
1. Name your file with the following format: year-month-day-postname.md
1. Copy and paste the following into the beginning of your document:

   ```
   ---
   layout: post
   title: "PUT YOUR TITLE HERE"
   date: 2017-11-14
   excerpt: "Think of the except as preview text that entices the reader to click to the full post."
   tags: [TAG, TAG]
   comments: true
   ---
   ```

1. Edit the title, date, excerpt, and tags. 
1. Add your writing sample.
1. Scroll down, then click Commit new file.
1. Repeat these steps to add more blog posts.	

**Add a Project post**
1. From your Repository page, click **_posts**, then click **Create new file**.
1. Name your file with the following format: year-month-day-projectname.md
1. Copy and paste the following into the beginning of your document:

   ```
   ---
   layout: post
   title:  "Title"
   date:   2017-11-14
   excerpt: "Use the excerpt to describe your project."
   project: true
   tag:
   - tag1 
   - tag2
   comments: false
   ---
   ```

1. Edit the title, date, excerpt, and tags. 
1. Add your project.
1. Scroll down, then click Commit new file.
1. Repeat these steps to add more Projects.	
