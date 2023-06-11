---
title: "Pimp My PC: An Introduction to Linux Ricing"
date: 2023-06-10 15:57:04
tags:
---

<link rel="stylesheet" href="/../css/post.css">

<img src="/../images/ricing/my_unix_rice.png" alt="linux rice" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">my current linux rice setup</p>

# What is ricing?

"Ricing" is the practice of customizing one's experience with their operating system, both functionally and aesthetically.
Functional customizing involves configuring a window manager or desktop environment program on top of their operating system. It can also often include using applications via CLI (Command Line Interface) over those with a GUI (Graphical User Interface) to create your optimal workflow.
Aesthetic customizing typically includes setting color themes, fonts, icons, and wallpapers.

You can rice your OS to optimize its performance, but more often the focus is on aesthetics.
Many (myself included) use window managers for the productivity benefits of using tiling to organize open windows into non-overlapping areas and being able to utilize keyboard shortcuts to perform many actions.

<video style="padding: 0 0 0 0;" controls  alt="video example of a tiling window manager">
  <source src="/../images/ricing/tiling_example.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video><p class="img-caption">example of a tiling window manager</p>

The term “ricing” comes from street racing. Asian drivers would customize their (typically Japanese-built) cars with paints, rims, spoilers, stickers, and other accessories. Originally it was an insulting term with racial overtones, but over time it was adopted by the online programming community and now refers to customizing your operating system to make it look cooler or work better for you.

# What is Linux and why is it used for ricing?

Linux is a family of open-source operating systems. Just like how Windows and macOS are operating systems that manage your computer’s memory and processes and provide a user interface for you, Linux operating systems provide many of the same things. Although how many services and how user-friendly the operating system is can vary across the Linux ecosystem. For example, Ubuntu and Linux Mint are known to be beginner-friendly operating systems that work right out of the box, with a GUI and an app store for installing commonly-used software. On the other end of the spectrum exists operating systems like Arch Linux, which are purposely minimal and require the user to manually set up anything extra they want such as sound or a GUI.

Linux operating systems are the ones predominantly used for ricing because of the high level of control they grant to the user and the large ecosystem of open-source software that allows for communities to form around creating software to meet their needs.

You can rice operating systems like Windows and MacOS, but you will be limited in the scope of things you can do. So it would be more for aesthetics than anything else, but some workarounds exist to use features you would typically see in a Linux rice.

<img src="/../images/ricing/unix_rice_macos.jpg" alt="macOS rice example" style="margin: 0; padding: 1rem 0 1rem 0">
<p class="img-caption">example of a rice built in macOS</p>

# Components of a Setup

There is no concrete list of components a setup needs to be considered "complete", but the following are some software applications that you'll find in most rices.

1. Window Manager or Desktop Environment

- Window Manager (WM): a single program that handles how your operating system manages open windows of applications. It allows you to change the size and position onscreen of your windows. Many window managers use keyboard shortcuts to quickly organize your windows in however you see fit.

- Desktop Environment (DE): a more fully-fledged suite of programs that include a GUI, and a window manager along with more pre-installed applications for use with our operating system.

2. Application Launcher

- A popup window for quickly searching for and launching applications.
- Rofi and dmenu are the most popular options.
<video style="padding: 1rem 0 0 2rem;" controls  alt="video example of rofi">
  <source src="/../images/ricing/rofi_example.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
<p class="img-caption">example video of using rofi</p>

3. Taskbar

- A taskbar is a menu that runs along the top, bottom, or side edge of the screen, just like what you would see when using Windows or macOS.
- A popular option here is Polybar. You can easily customize it to show information such as the time, resource usage, network connection, and currently playing music.

<img src="/../images/ricing/polybar_example.png" alt="polybar example">
<p class="img-caption">example of polybar taskbar</p>

4. Color Theme

- Many people design their rice with a color theme in mind and coordinate the color of their applications and wallpaper to match their theme.

<img src="/../images/ricing/unix_rice_pink.jpg" alt="unix rice pink example">
<p class="img-caption">pink color theme</p>

<img src="/../images/ricing/unix_rice_orange.jpg" alt="unix rice orange example" style="padding-top:1rem;">
<p class="img-caption">orange color theme</p>

<img src="/../images/ricing/unix_rice_windows.webp" alt="unix rice orange example" style="padding-top:1rem;">
<p class="img-caption">Linux OS themed to look like a Windows operating system from the 90's</p>

<img src="/../images/ricing/unix_rice_thatcher.webp" alt="unix rice margaret thatcher example" style="padding-top:1rem;">
<p class="img-caption">rice themed after former British PM Margaret Thatcher</p>

<video style="margin: 1rem 0 0 2rem;" controls  alt="ricky bobby meme video">
  <source src="/../images/ricing/ricky_bobby.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video><p class="img-caption">how i feel about that last one</p>

5. Browser Launch Page (optional)

- One neat thing I've seen a lot of people do is design their own web pages to open when they launch their web browsers. It's a way to customize your experience with the application we probably use the most on our computers.
- I created my own by writing a simple web page in HTML and CSS and added some JavaScript to write a message that changes depending on the time and day of the week.

  Afterwards, I installed the [New Tab Redirect](https://chrome.google.com/webstore/detail/new-tab-redirect/icpgjfneehieebagbmdbhnlpiopdcmna) extension for Google Chrome.
  You can simply set the extension to use the HTML file on your computer. Or if you want to use the launch page across multiple computers you can do what I did which was host my files in an AWS S3 bucket and set the redirect URL in the New Tab Redirect settings to the URL of the HTML file hosted in S3. This way if I want to make any changes to the launch page I only need to update the files in my S3 bucket instead of having to manually download the new files across all my computers.

<img src="/../images/ricing/chrome_start_page.png" alt="my chrome launch page example" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 2rem;">
<p class="img-caption">my browser launch page</p>

6. Whatever You Like

- An aspect of ricing I appreciate is that there is no one right way to do it. The communities around ricing I've seen all appreciate setups that are way out there. The way we interact with operating systems like MacOS and Windows has long been that we use it as it comes out of the box, with the biggest changes we make typically being the wallpaper we set and the various applications we use on it.

  At the end of the day the only one using your computer is you, so ricing ends up being a really cool way to express your personality through creating a setup that works just for you. For example, I need a setup that allows me to quickly switch between typing in English and Japanese, so I configured Japanese language support on my operating system using Ibus and added keyboard shortcuts to easily switch between the two.

  It's also an iterative process. My aesthetic preferences and the functionality I need have changed greatly from the time when I created my first rice, and my current setup reflects that. I've included some resources below that are great places to get started in ricing their OS, and I encourage anyone to reach out to me if they're interested and have questions!

# Resources to Learn More

- https://www.reddit.com/r/unixporn/
- https://github.com/polybar/polybar
- https://github.com/davatorium/rofi
- https://wiki.archlinux.org/
