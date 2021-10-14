---
title: "Change Favicon Colour for Dark mode"
date: 2021-07-23
author: Jane
image: /images/blog/dark-mode.jpeg
description : "This is meta description"
---

This has been reposted with permission from [Bill Erickson](https://www.billerickson.net/). You can see the original post [here](https://www.billerickson.net/favicon-dark-mode).

![Header](/images/blog/dark-mode.jpeg)

When you upload a favicon image in the WordPress customizer, it provides a helpful preview to see how your favicon will appear in browsers using light or dark mode.

![header](/images/blog/ee6fdc33-6408-40ad-93d4-37cf972a37c6.png)

When the favicon color doesn’t work well with dark mode, a common fix is to replace the transparent PNG with a JPG that has a white background, but then you end up with a white square in dark mode.

Alternatively, you can use an SVG for the favicon and modify the favicon styling based on the color scheme.

You can see this in use in the recent [NerdPress](https://www.nerdpress.net/) redesign we just launched.

# Create SVG favicon
Create a square SVG with your desired icon. It will look something like this:

	<svg xmlns="http://www.w3.org/2000/svg" width="512" height="512" viewBox="0 0 512 512">
		<path fill="#0F145B" d="......" />
	</svg>

Remove any styling from the shapes in the SVG (so the ``fill`` and ``stroke`` attributes) and add those styles with inline CSS.

You can use ``@media ( prefers-color-scheme: dark )`` to style the dark mode version differently. Here’s what my SVG now looks like:

	<svg xmlns="http://www.w3.org/2000/svg" width="512" height="512" viewBox="0 0 512 512">
		<style>
			path {
				fill: #0F145B;
			}
			@media ( prefers-color-scheme: dark ) {
				path {
					fill: #43C1C5;
				}
			}
		</style>
		<path d="....." />
	</svg>

# Add SVG favicon to your theme
I added my favicon.svg to my theme’s ``/assets/images/`` directory, but you can add it anywhere in your theme.

Add the following code to your theme’s functions.php file to include the SVG favicon.

	/**
	* SVG Favicon
	*/
	function be_svg_favicon() {
		echo '<link rel="icon" href="' . esc_url( get_stylesheet_directory_uri() . '/assets/images/favicon.svg' ) . '" type="image/svg+xml">';
	}
	add_action( 'wp_head', 'be_svg_favicon', 100 );

It seems that the SVG favicon is prioritized over the WP generated one regardless of whether it appears before or after it in the page markup, but I have the priority set to 100 so it will appear after, just in case.

Even with this approach, you should upload a JPG version of the favicon in the WordPress customizer. There are still [many browsers that don’t support SVG favicons](https://caniuse.com/link-icon-svg) so you’ll want a fallback.

_Alpha Omega Digital is a WordPress web development agency based in Melbourne, Australia but also services clients from Sydney, Brisbane, Newcastle, Perth, Adelaide, Darwin and Hobart._