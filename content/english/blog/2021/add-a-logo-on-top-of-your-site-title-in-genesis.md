---
title: "Add a logo on top of your site title in Genesis"
date: 2021-03-05
author: Jane
image: /images/blog/alphadigital-logo-site-title.png
description : "This is meta description"
---

Hi everyone, I wanted to share how I fixed an issue I was having trying to add my logo alongside my site title in Genesis. Out of the box, Genesis gives you the option to edit both your site title and your header image, and it looks easy enough from the customiser:



In theory, you would upload your logo to your header image, and Genesis would call in both the title AND the header image and display both. Except in Genesis it doesn’t. It allows you one or the other, and that wasn’t going to work for me.

I searched far and wide for a solution, and couldn’t find one so after some time playing around with my dev tools, I came up with a workable solution and that is using a pseudo element in CSS.

> A Pseudo element is used to style specified parts off an element, eg. Before, first-line, first-child and so on.

Using pseudo elements in CSS allows us to further customise our Genesis theme without having to copy markup in the parent theme files, altering it, and adding a copy of that file to our child theme.

The specific pseudo element that I used to add my logo to my site title in Genesis, was the ::before selector. I targeted my .site-title a element, and added a ::before pseudo class to add an image above my site title.

You can see the result here:

![Header](/images/blog/alphadigital-logo-site-title.png)

So there you have it, a pseudo class to add your logo above your site title in Genesis. and you can copy the markup on [Github](https://github.com/alphaomegadigital/addlogotoheadergenesis). Whilst I could have only shared the site-title a with the pseudo element, I added all my site-title CSS in as well in case it is different from yours, depending on which theme you are using.

I hope this solution works for you, and please leave a comment and let me know if you need any help.

{{< gist alphaomegadigital 88a6a54b35c642549987c62df3b74c9c >}}

_Alpha Omega Digital is a WordPress web development agency based in Melbourne, Australia but also services clients from Sydney, Brisbane, Newcastle, Perth, Adelaide, Darwin and Hobart._