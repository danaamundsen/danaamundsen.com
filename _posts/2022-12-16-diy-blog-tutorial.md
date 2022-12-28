---
layout: post
title: DIY Website or Blog with Github Pages
image: http://www.icefairy.net/artlog/
desc: 
tags: ["Tutorials", "Web Design"]
comments: true
published: false
---

In this blog post I am going to take you step by step through how I set up my blog with Github Pages. You do not have to do everything the way that I did! But I can only speak to my own experience. I hope that this guide encourages you to try making your own website.

### Table of Contents
- Why run your own blog?
- Getting Started with Githug Pages
- Setting Up Your `_config.yml` File 
- Image Hosting with Site44
- Resources

<!--more-->

### Why run your own blog?

With twitter going down the drain and AI image generators scraping data from websites like DeviantArt and ArtStation, I think this is a great time for artists to start running their own blogs and websites again. Many artists do, but I still see artists with no website or personal blog. If you are only sharing your work on social media, you are at the mercy of advertisers, CEOs, admins, and algorithms. You may be giving permission to use your work in ways you don't realize. Your account could be suspended, or the social media network could collapse, and where would that leave you and the people who follow you?

Having your own blog or website gives you control over your work. It gives you freedom to post whatever you want, however you want. You can choose to make your website as simple or as complex as you want. You can present your work in the way that you descide. And best of all, you don't have to worry about an algorithm, advertisers, or buy-outs.

#### Why Github Pages?

Github Pages are free, simple, and entirely editable. You work directly with the code of the site so the only limits are your own patience and technical knowledge. They are also incredibly quick to set up. While I do believe that it is possible to set up a Github Pages site with zero prior experience with HTML, CSS, and other coding languages, I admit that it would be more difficult. 

### Getting Started

First, you may want to purchase your own domain. I use [NameCheap](http://www.namecheap.com), so that is what I reccommend. You don't have to use a custom domain, however, and can host your site at yourusername.github.io.

If you don't have one, make a [GitHub](https://github.com) account. Then, follow the instructions to [create a new GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site).

Here is a summary of the instructions

1. Create a new repository
2. Type in the name of your repository
3. Click 'Create Repository'

Simple, right?

Next we need to tell GitHub that this repository is going to be a website.

1. Navigate to your site repository on GitHub
2. Click on **Settings** on the top menu
3. Choose **Pages** from the left side menu
4. Set *Source* to **Deploy from branch** and *Branch* to **main** then hit **Save**

While we are in our settings, let's [configure our custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site) if we will be using one. 

1. Type in your custom domain name (eg. `www.yourdomain.com`) and hit **Save**. This will add a CNAME file to the root source of your branch.
2. Navigate to your DNS provider (NameCheap, GoDaddy, or wherever your purchased your domain) and create a CNAME record that points your subdomain to to the default domain of your site. On NameCheap, this will be done under the "Advanced DNS" settings. The most common subdomain is www. If you want to use the subdomain `www.yourdomain.com` for your user site, create a CNAME that points `www.yourdomain.com` to `yourusername.github.io`. You could use a different subdomain, like `blog.yourdomain.com` by creating a CNAME that points `blog.yourdomain.com` to `yourusername.github.io`.
3. Return to your GitHub repository settings and check that the domain has connected. You should see "Your site is live at: http://www.yourdomain.com" Click and see if your site is up! Sometimes this can take a minute.

Congratulations! You just made a website! Now let's see what we can do with it.

### Setting Up Your `_config.yml` File

Now we will set up our `_config.yml` file. This is where you will assign your website a title, description, theme, and more. There are a dozen or so [supported themes](https://pages.github.com/themes/) for GitHub Pages, but for the purposes of this tutorial we will be using the [Minimal](https://github.com/pages-themes/minimal) theme. This is my preferred theme because it is easy to customize with your own colors, fonts, and logo. Feel free to experiment with other themes if you find one that suits you.

1. Return to the main directory of your repository branch.
2. Click **Add file > Create new file**
3. Name your file `_config.yml` and paste the following into the file

```
title: [The title of your site]
logo: /assets/img/logo.png
description: [A short description of your site's purpose]
show_downloads: ["true" or "false" (unquoted) to indicate whether to provide a download URL]
google_analytics: [Your Google Analytics tracking ID]
theme: jekyll-theme-minimal
excerpt_separator: <!--more-->
```

4. Replace the bracketed content with your own site information.
5. Hit **Commit new file**

Give your site a minute to update, then try refreshing your website. While working like this I like to keep my website open in another tab or window so that I can easily check the updates as they go live. It should now look something like [the default minimal theme](https://pages-themes.github.io/minimal/).

Awesome!

### Setting Up Your File Directory

Now let's go back to our repository and fill in our file directory. These are the basic files that we will use to make a blog. To start we will be cloning these files from the Minimal theme repository. We will go in and edit these files later, but first let's put them all in and see what happens. 

- `_layouts/default.html`
- `_layouts/post.html`
- `_includes/head-custom.html`
- `_includes/head-custom-google-analytics.html`
- `_assets/css/style.scss`
- `assets/img/logo.png`
- `index.html`
- `_posts/[YYY-MM-DD]-my-first-post.md`

#### `_layouts`

The `_layouts` folder is where you define the layout of the site. You can define as many layouts as you like. For our website we will make a 'default' layout and a 'post' layout.

1. Click **Add file > Create new file**
2. Name your file `_layouts/default.html`
3. Copy and paste [the default.html file from the original minimal theme](https://github.com/pages-themes/minimal/blob/master/_layouts/default.html)
4. Hit **Commit new file**
5. Create a new file in the `_layouts` folder named `post.html`
6. Copy and paste [the post.html file from the original minimal theme](https://github.com/pages-themes/minimal/blob/master/_layouts/post.html)

#### `_includes`

The `_includes` folder is for additional data in the `<head>` of your website. This is where you define the favicon, add any metadata for sharing on social media websites, and where you can import fonts. I will talk about all three of these things further along in the tutorial.

Return to your main directory and create the `_includes/head-custom.html` and `head-custom-google-analytics.html` in the same way, copying from [the original files in the minimal theme](https://github.com/pages-themes/minimal/tree/master/_includes).

#### `assets`

Your assets folder is where the style.scss file lives, and also where image files will go.

Let's create our `style.scss` file so that we can edit the css of our website. Return once more to your main file directory and create the file `assets/css/style.scss`. For now, all you need to do is paste the following code to import the css of the minimal theme.

```
---
---

@import "{{ site.theme }}";
```

Next, let's upload a logo file.

1. In order to create the `img` folder we will have to create a file. While you are in the assets folder, create a new file and name it `img/image.html`. You can leave the file blank or write whatever you want in it because we are just going to delete the file shortly.
2. While in the `img` folder, click **Add file > Upload files** and upload a file named `logo.png` 
3. Click **Commit changes**
4. Delete the image.html file that you created.

#### `index.html`

Okay, we're almost there! The `index.html` file is the landing page of your website. When someone goes to `www.yourdomain.com` the index.html file is the one that will be displayed. 

In the main directory of your repository, create a file `index.html` and paste in the following code.

```
---
layout: default
---

  {% for post in site.posts %}

      <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>

        {{ post.excerpt }}

      <small><a href="{{ site.baseurl }}{{ post.url }}">Permalink</a> | Date: {{ post.date | date: "%D" }} | Author: {{ post.author }}</small>

  <hr></hr>

  {% endfor %}
  ```

And commit the file.

#### `_posts`

Finally, we will need a `_post` folder. This is where all of your posts will go.

Let's make our first blog posts. The name of every post file should be be formatted `YYYY-MM-DD-title.md` with the date being the date posted and not the date drafted.

Posts can be written in [markdown](https://github.github.com/gfm/) or html. In our `_config.yml` file, I had you define am `excerpt_separator` as `<!--more-->`. On your index page, only the content above the excerpt_separator will be displayed. This is helpful if you have long posts.

1. In the main directory, create a new file `_posts/[YYYY-MM-DD]-my-first-most.md` where the bracketed information is todays date (eg. 2022-12-16).
2. In the file, past the following code.

```
---
layout: post
title: This is my first post
publish: true
---

This is the content of my first post! [This is a link to my website](http://template.icefairy.net). You can also make font *italic* or **bold** or _underlined_ with markdown.

And you can make lists
- item 1
- item 2
- item 3

<!--more-->

And this is the stuff under the read more.
```

You can change the title and post content and commit the file. Feel free to try out some markdown or html in the post. I included a few examples of things you can do with markdown to give you some ideas. After that, commit the post and refresh your website.
