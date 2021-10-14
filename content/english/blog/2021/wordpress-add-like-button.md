---
title: "WordPress: add a like button to your posts using PHP and Javascript"
date: 2021-09-29
author: Jane
image: /images/blog/page-header-template-before-1024x413.png
description : "This is meta description"
---

This week I had a client request a modification to an existing WordPress page template which already had two post anchor identifiers to retrieve get_the_author_meta and get_the_date. It was a custom template that displays a [CPT](https://wordpress.org/plugins/custom-post-type-ui/) by category to a page.

You can see the example below of the get requests:

![Header](/images/blog/page-header-template-before-1024x413.png)

So I found this repository on Github by Jon Masters and decided to implement it, but modifying the custom post type template instead of the standard blog page template.

Jon gives walkthrough instructions, but since I modified it for a custom post type template I will do my own walkthrough, in case you are looking to modify a CPT template as well.

# 1. Run Query Monitor to find the template file you are after
If you install the Query Monitor plugin, you can click on ‘templates’ to see which WordPress template file is being called in. It’s not perfect though. In this case, it showed me a template hierarchy of 5 template files, none of which contained the section I wished to modify. If this happens, then you can just dig around through the template files and if the naming convention is obvious you shouldn’t have too much trouble. In this case I was editing the header-insight.php

# 2. open your functions file and add the post-like.php file code
Ok, this will make your functions file enormously long, but since Jon has shared the code I am going with what he as built for us already. Of course you can refactor that code into a post-like.php template file and call it into your functions file, but let’s keep it simple and add the post-like.php into functions.php like so:

{{< gist genesis16 184494fad656fb55aa08216cf2232701 >}}

# 3. Change theme name
In the pile of code we just added to functions.php go hit control F, and replace “YourThemeTextDomain” with your theme name. This isn’t necessary but I think it makes your code clearer to read.

# 4. Add the javascript file to your library
Add this javascript to your theme/lib/js/simple-likes-public.js path and save. Here’s the code to save you time:

{{< gist genesis16 2ee8b7bdbb7e91e3d494b0826ec2db63 >}}

# 5. replace the svg with font awesome
I found the SVG file came out massive, and of course its easy to modify it with CSS, but it’s also easy to add font awesome icons in, and Jon has already commented out the instructions on how to do this. In case you would like to see it anyway:

![Header](/images/blog/functions-get-like-fa-1024x512.png)

# 6. add the likes function within the loop of your template
Now we are going to go into our template file, in my case it’s header-insights.php and find the section where the GET parameters that are already calling in the author and the date, and we are going to echo in our function here:

![Header](/images/blog/add-simple-like-loop-header-1024x520.png)

# 7. Check your page template and make sure your like button is working
Now we’re going to go to our post template file, refresh the page and see if our like button is working. If you click and un-click the button, the heart will turn on and off which is correct. The way the function is setup, it only allows one user to like a post by calling your IP address into the wp_postmeta table in SQL, so for example you cannot publish a post and click like a hundred times to look really cool, LOL. You can see the finished product below:

![Header](/images/blog/header-template-after-1024x398.png)

_Alpha Omega Digital is a WordPress agency based in Melbourne, Australia but also services clients from Sydney, Brisbane, Newcastle, Perth, Adelaide, Darwin and Hobart. Have a project in mind? Contact me [here](/images/)._