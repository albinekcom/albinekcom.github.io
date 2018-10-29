---
layout:       post
title:        "Optimizing raster images 👁👁"
description:  "Tools for optimizing raster images"
date:         2018-10-29 22:00:00 +0200
categories:   graphics
image:        /assets/img/post/optimizing-raster-images-0.png
---

![Cover]({{ page.image }})

## Show me your #nice_pictures

In the previous blog posts ([Optimizing vector graphics 👁](optimizing-vector-graphics)) I described how in a easy way optimize vector images. Vectors are great but we are still surrounded by typical, classic images. `JPEG`, `PNG`, `GIF`... These files could be also improved (with smaller file size as an output). How you can do it? By using a proper tool!

## Perfect tool?

Simple optmizing raster images looks very similar to vector graphics. Use sophisticated tool and you are done. So it is time to find this Swiss Army knife. During browsing the Internet you can encounter stuff named like:

- pngquant
- PNGGauntlet
- jpegoptim
- Gifsicle
- OptiPNG
- DeflOpt
- PNGOut
- PNGOptimizer
- AdvPNG
- (...)

A lot of stuff. So what is the good solution? You can always use each one, try it with some special flags, compare the results and find an image with the fewest bytes at the end. Maybe there is a tool with already integrated other optimizers? 🤔

## Optimizing using ImageOptim

This is a macOS application. It contains some of the previously listed tools. The usage is quite simple: drag & drop the files and wait for the results.

![ImageOptim](/assets/img/post/optimizing-raster-images-1.png)

## Optimizing using pinga and pingo

I know, I know, not everyone uses macOS. So what about other platforms? On Windows I remember `PNGSlim` for `PNG` files. The development of that solution has been stopped but the author published 2 other tools: [pinga](https://css-ig.net/pinga) and [pingo](https://css-ig.net/pingo) (both are also for `JPG` files).

![pinga](/assets/img/post/optimizing-raster-images-2.png)

## Examples

### Example No. 1

The first example will be the image which was used in the previous post but right now it is exported as a raster image. (after zooming in the edges of the image are not so sharp like in a vector one...)

![Example No. 1](/assets/img/post/optimizing-raster-images-3.png)

| Original file size  | ImageOptim   | pinga        | pingo        |
|---------------------|--------------|--------------|--------------|
| `11081 bytes`       | `5210 bytes` | `4973 bytes` | `3390 bytes` |

Quite significant improvement, more than `50%`!

### Example No. 2

The next example will be something from the web. Let's open some specific website like the wrong address, for example: [https://google.com/wrong_address](https://google.com/wrong_address). Google logo appears. Let's check what can we do with it.

![Example No. 2](/assets/img/post/optimizing-raster-images-4.png)

| Original file size | ImageOptim   | pinga        | pingo        |
|--------------------|--------------|--------------|--------------|
| `3170 bytes`       | `3170 bytes` | `3137 bytes` | `2281 bytes` |

So when you have already optimized image (using an old tool in the past), it can be still improved when you use different approach or newer version of the optimizer.

## Other tools?

Yes, there are a lot of other tools. You can use some other specific optimizing tool which are listed above (and find more and more), use cloud solution [TinyPNG](https://tinypng.com) or even a ready API service like [ImageOptim API](https://imageoptim.com/api/start).

Choose the right one which fits your needs.

## Conclusions

- Optimized images in a lossless way are better than default, non-optimized version: the same quality and smaller size.
- Tools with aggregated optimizers are doing good job for the common tasks.
- Users and their Internet providers will thank you for faster downloading the content.
