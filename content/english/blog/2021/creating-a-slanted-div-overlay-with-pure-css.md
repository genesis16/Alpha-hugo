---
title: "Creating a slanted div overlay with pure CSS"
date: 2021-06-11
author: Jane
image: /images/blog/diagonal-cover-1024x355-1.png
description : "This is meta description"
---

When a client approached me and wanted a slanted div overlay on the homepage, I knew straight away it would have to be built in CSS. Why? Because the overlay his graphic designer built into the image, did not display correctly on devices. The text was completely unreadable.

So I went searching the deep dark corners of the internet for a slanted DIV overlay, and I found this awesome article. Nils explains it in a much cooler way than me, and has awesome graphics to match, so I won’t go into detail here. Regardless I am sharing the code I used to implement this on a WordPress site and you are welcome to cut and paste it into your next project.

![Header](/images/blog/diagonal-cover-1024x355.png)

# Step 1.
First I cloned Nils pen on Codepen, and added the code from the article. Now with the code he provided, as soon as I dumped it into WordPress it did not display the same. I had to modify it heavily to get the look I wanted. Mostly because he was using the transform:skewY property, and for this project I need to use transform:skewX. That and I needed multiple media queries to work with WordPress. I started with the overlay, and then made some design decisions on how wide I wanted it to be. It had to be wide enough to cover roughly half the image, and comfortable display the text inside it, but not so wide that it don’t go all the way to the edge of the screen.

![Header](/images/blog/skew-y.png)

# Step 2.
Then I added my text into the heading tags, and added a default margin for a wide screen. Because we are using the transform:skewX() property, everything inside the DIV is going to skew including the text. We don’t want this. Here’s an example of the ugliness that skewed text is, check out this H2 element:

![Header](/images/blog/slanted-div-overlay.--1024x336.png)

# Step 3.
I added the transform:skewX() property to each heading element. Since the overlay has a property of transform:skew(200.25deg), we have to apply transform: skewX(-20deg) to each heading element to ensure the headings are upright.

![Header](/images/blog/skew-y-1.png)

![Header](/images/blog/slanted-div-skew-right-1024x400.png)

# Step 4.
I started working on the media queries to make the page look responsive on all devices. This was a tad painful, as I had to keep tweaking the elements and overlay to get the right balance, but I got there. Now mind you if you view the Codepen, and it doesn’t look right on devices- this code has been used on a live wordpress site, so the responsive widths work on WordPress but they will not work on Codepen. Click [here](https://codepen.io/genesis16/pen/KKWQzom) to view the source code.

_Alpha Omega Digital is a WordPress web development agency based in Melbourne, Australia but also services clients from Sydney, Brisbane, Newcastle, Perth, Adelaide, Darwin and Hobart._


