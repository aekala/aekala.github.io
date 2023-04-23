---
title: How To Make a Blog in 2023
date: 2023-04-22 12:31:21
tags:
---

  <link rel="stylesheet" href="/../css/post.css">

<img src="/../images/pyramid.webp" alt="pyramids" style="margin: 0; padding: 1rem 0 1rem 0;">

If someone doesn't want to have to deal with any coding or web design, then using a website builder like Squarespace or WordPress is a great option.

I decided to build my blog with [Hexo](https://hexo.io/), a static site generator. A static site generator is a tool to generate a fully static website from a set of templates and configuration files. The benefit of static site generation is that webpages are pre-built rather than created on-demand, reducing the time it takes a website to load in the viewer's browser.

The main reason I opted not to use a service like Squarespace was I wanted to completely own my website and not be locked into any specific vendor.
Hexo also uses Node.js which I was already comfortable with. A very popular framework for creating blogs is Ruby on Rails. I considered using this as I had already used Ruby on Rails in a web application course at Ohio State but went with Hexo as I preferred to work with Node.js on this project.

# Requirements

Before starting any work on this project, I wrote down a list of requirements I wanted to achieve. Writing these down helped guide my planning and research in deciding which technologies to use.

1\) Sort posts chronologically. I wanted to be able to view posts in order and show the most recent ones on the homepage.

- Hexo, like other static site generators such as Jekyll and Hugo, implements this using a designated section of YAML (an easily readable language commonly used in configuration files) code at the beginning of each post. This section is called Front Matter, and it contains data such as the title of the post and a timestamp that is later used to sort the posts in chronological order.

2\) Reusable components, specifically for headers and footers.

- I wanted to adhere to the DRY (Don't Repeat Yourself) principle as much as possible with this project. If I wanted to make a change to the header or footer I should only need to do it in one place, instead of having to manually update a ton of different files. Hexo accomplishes this using partials which enable sharing the same component across different pages.

3\) Responsive design, pages must look good on all devices and screen sizes.

- There are few things I dislike spending time on more than writing media breakpoints, so I specifically searched for a Hexo theme that had this already accounted for in its CSS.

4\) Quick load times. It's a blog, **not** a Bethesda game.

- I'm pretty happy with the results here currently, but there is still room for improvement. I used Google Lighthouse to see how I can improve metrics such as First Contentful Paint (the length of time from when the page starts loading to when any part of the page's content is rendered on the screen) and Time to Interactive (the amount of time it takes for the page to become fully interactive to the user).

  There are some recommendations the tool has made that I'll eventually implement such as converting my images to WebP format as it offers better compression and therefore faster load times in the browser. Google found in a [study](https://developers.google.com/speed/webp/docs/webp_study#conclusion) that WebP file sizes are on average 25-34% smaller than their JPEG equivalent.

5\) Upload quickly. Write a post and have it up on the blog in minimal steps.

- I can quickly create a new post using the `hexo new post` command. I can pass it a title and it will generate a new post with the title and a timestamp in its front matter.

  Once I've finished writing, all I have to do is push my changes to my GitHub repository, and GitHub will take care of the rest. GitHub runs an automatic build of my project with its new changes and then deploys the project to my website. From the time I send my changes to GitHub, it only takes about 30 seconds for my website to reflect my changes.

# Themes

Hexo has an active community of users and designers who have open-sourced their themes for use by other Hexo developers. I went with Cactus by [probberechts](https://github.com/probberechts) for the theme of my blog because I liked the font and the way the content was organized. I made changes to the color theme, the header and the footer, and added an image to the home page.

# Deployment

Once I was satisfied with the design of my blog, next came the question of how to share it on the internet. Up until this point, my blog had only existed on my computer. My laptop would boot up a web server and serve my blog via a port on my computer for me to view in my browser but only my browser.

GitHub provides a website and hosting for one website per user via its GitHub Pages service. The name of the website GitHub provides to you has your username in it, so mine was aekala.github.io, not the best-looking URL.
So I purchased averagecase.com through Google Domains and set it up to point to aekala.github.io.

Lastly following the instructions in Hexo's [documentation](https://hexo.io/docs/github-pages), I set up automatic deployments to my website when I push changes to GitHub.
