---
layout:       post
title:        "Going dark (Web Edition) 🌙"
description:  "Improvment in CSS file to use dark mode on the website"
date:         2019-04-08 19:00:00 +0200
categories:   web
image:        /assets/img/post/going-dark-web-edition-0.png
---

![Cover]({{ page.image }})

## The darkness is coming

There is a new trend - making stuff dark. In the past you have to decide the style of your website (light or dark) or you have to add custom settings for the user and store that preference somehow.

`Safari 12.1` (which is part of `macOS 10.14.4`) adds support for detecting a color theme. It can pass this information and specific version of the website can be rendered. When your system uses `Dark Mode` (`System Preferences -> General -> Appearance -> Dark`), Safari automatically has dark UI and tries to render a website using `dark theme` if it possible. Your website's CSS file needs some tweaks to be dark-ready.

## Simple website

Let's create a very basic website by using two files: `index.html` and `main.css`. The first file contains standard `HTML5` template with a one header and a one paragraph, the second file contains values for styling.

The content of `index.html` file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" type="text/css" href="main.css">
    <title>Dark Website Example</title>
</head>
<body>
    <h1>Website Title</h1>
    <p>Some random words.</p>
</body>
</html>
```

The content of `main.css` file:

```css
body {
    color: black;
    background: white;
}
```

The result of these code:

![Simple website with default style](/assets/img/post/going-dark-web-edition-1.png)

Plain white website despite the fact that `Dark Mode` is enabled in the system (look at the dark toolbar at the top of the browser).

## Adding support for Dark Mode

To enable using dark content on the website, `prefers-color-scheme` media query needs to be used. Just add it and override the proper values.

The improved content of `main.css` file:

```css
body {
    color: black;
    background: white;
}

@media (prefers-color-scheme: dark) {
    body {
        color: white;
        background: black;
    }
}
```

It checks if the dark mode (color scheme) is enabled and renders proper colors according to it. The result of these changes:

![Simple website with enabled dark mode](/assets/img/post/going-dark-web-edition-2.png)

You can take a look at this website here: [Dark Website Example](https://albinek.com/DarkWebsiteExample/).

The example code used in this post can be found here: [Dark Website Example on GitHub](https://github.com/albinekcom/DarkWebsiteExample).

## Is it the future?

Dark style is trendy right now and I think it could be the future (better browsing at night, more content-focused and lower battery consumption by the device). You don't need some custom things like remember the user preferecnes etc., just use this media query and that's all! Looking forward to supporting this funciton in the other browsers (Firefox 67 already did it), better adoptation on the websites and more users with enabled `Dark Mode` by default.

Maybe changing the colors will not be enough (the icons could need some tweaks too) so ask your local UI/UX expert about it. 😉

Read [prefers-color-scheme - CSS: Cascading Style Sheets](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme) about the browser compatibility and more parameters.

## Conclusions

- Use `prefers-color-scheme` media query in CSS file and override values for another theme.
- Try to design your website to be not hardcoded (or even hardcolored?) with only one style. Be polite to dark lovers. 🌙
