---
title: "Fix your broken wordpress site by troubleshooting plugin conflicts"
date: 2020-12-07
author: Jane
image: /images/blog/plugin-deactivate.jpeg
description : "This is meta description"
---

{{< figure src="/images/blog/code-1-512x338.png" height="50px">}}

Whether you are new to WordPress or a seasoned user, you have no doubt had some experience with WordPress plugin repository – the good the bad and the UGLY.

If you’re starting out on WordPress, you have most likely fallen into the “more is better” trap and installed every plugin that sounds great you can get your hands on. This is a very bad idea. I’ll attempt to explain why:

> “More plugins equal more functionality, and also more opportunities for your site to break”
> 
> -- Jane James

---

Why’s that? Each plugin is build and maintained by a different developer/company. This means they all have different code structures, and some are built on http1, and newer plugins support [http2](https://www.cloudflare.com/learning/performance/http2-vs-http1.1/), some of them are built on HTML, and others [HTML5](https://www.w3.org/TR/html5-diff/), Some do not support [CSS3](https://www.w3schools.com/css/) and so on. On top of this, these plugins are also developed for certain versions of [PHP](https://www.w3schools.com/php/default.asp) and [WordPress](https://wordpress.com/). Installing so many plugins without reading the docs first and referring back to your owns sites versioning of PHP and WordPress, there is likely to be a conflict between two plugins who are targeting the same WordPress core [hooks](https://developer.wordpress.org/plugins/hooks/), which will usually result in your site going down, or breaking in some way.

So, if you find yourself in the unsavoury position of your WordPress site breaking or not functioning as it should, here’s a walkthrough on how to troubleshoot that. Note this is a beginners guide; we will not be diving into the theme files or showing you how to [debug](https://wordpress.org/support/article/debugging-in-wordpress/) in WordPress, as that is more advanced and most definitely not for a WordPress user.

# Checking plugin conflicts, using a plugin
After ranting on about how you shouldn’t just install plugin willy nilly, and how they can break your site I’m going to….ask you to install another plugin. LOL. Let’s do this.

## 1. Deactivate all your WordPress plugins. You can bulk deactivate them from the installed plugins menu like so:

![Header](/images/blog/plugin-deactivate.jpeg)

## 2. Change your theme to the Twenty Twenty or Twenty Twenty one default theme.
By deactivating your current [theme](https://en-au.wordpress.org/themes/twentytwenty/), we are excluding all of the files and functions that could be contributing to your site breaking, and my process of elimination, we will ascertain whether a plugin has broken your site or if it’s part of your theme files.

## 3. Install the Health Check & Troubleshooting plugin in your plugin repository
Click on plugins, add new, and search for [Health Check & TroubleShooting](https://en-au.wordpress.org/plugins/health-check/) in the wordpress plugin repository. You can also download it [here](https://en-au.wordpress.org/plugins/health-check/) and upload the zip file.

![Header](/images/blog/health-check-plugin.jpeg)

## 4. Activate the plugin, and then navigate to ‘Tools’ and ‘Site health’

![Header](/images/blog/sitehealth-tools.jpeg)

## 5. Click on the troubleshooting tab, and enter troubleshooting mode.

![Header](/images/blog/enable-troubleshooting-mode.jpeg)

## 6. Check the warnings you are given in troubleshooting mode.
If there are none that are obvious, then navigate to the front end of your site and see if the error is happening. If it is, then move on to Step 7.

## 7. Reactivate the plugins, one by one and check the front end of your site until the error is reproduced.
This is tedious, but it’s likely we will find the plugin that is causing issues for you, or if the error is not happening then we will know it’s code in your theme files.

## 8. If you have found the plugin causing issues, delete it, and reinstall your theme.
Once your working theme is reinstalled and the plugin has been deleted, your site should be working perfectly! Congratulations! At this stage I would search and test an alternative plugin to the one that was causing issues, and if that is not an option, I would log a ticket with the plugin developer and ask them to assist you in figuring out why this plugin is breaking your site. They may or may not be able to get to the root of the issue, but most will be helpful and try to assist you in anyway they can.

## 9. If you have arrived at step 9, then there is an issue with one of your theme files.
Most likely your style.css file of functions.php file if you have been making edits to your child theme directly from the wordpress dashboard. If this is the case, you need to contact your hosting provider, and ask them to reinstall the latest backup of the site from when the site was working. If you’re unsure I would go 7 days back, reinstall the files and see if it is functioning properly.

So if you made it through this tutorial, and you gave this a go, please let me know in the comments how it worked out for you, or what additional steps you took to find the source of your site errors.

_Alpha Omega Digital is a WordPress web development agency based in Melbourne, Australia but also services clients from Sydney, Brisbane, Newcastle, Perth, Adelaide, Darwin and Hobart._