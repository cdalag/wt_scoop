# Scoop Main

Core manifests for [Scoop](https://scoop.sh), the Windows command-line installer.

How do I install these manifests?
---------------------------------

Just `scoop install <manifest>`. This is the default bucket for Scoop and is added by default.

# ImageMagick
## Overview
Images often account for most of the downloaded bytes on a page. As a result, optimizing images can often yield some of the largest byte savings and performance improvements: the fewer bytes the browser has to download, the less competition there is for the client's bandwidth and the faster the browser can download and render content on the screen.

Recommendations
Finding the optimal format and optimization strategy for your image assets requires careful analysis across many dimensions: type of data being encoded, image format capabilities, quality settings, resolution, and more. In addition, you need to consider whether some images are best served in a vector format, if the desired effects can be achieved via CSS, and how to deliver appropriately scaled assets for each type of device.

Optimizations for all types of images
Follow the best practices for serving responsive images
Follow the image optimization checklist for individual images
Optimizations for GIF, PNG, and JPEG images
GIF, PNG, and JPEG formats make 96% of the entire Internet’s image traffic. Because of their popularity, PageSpeed Insights provides specific optimization recommendations. For your convenience, you can download the optimized images directly from PageSpeed Insights (which is using image optimization library from modpagespeed.com).

You can also use tools such as the convert binary made by ImageMagick which can apply similar optimizations - see example instructions below.

If you use third party tools, please be aware that the transformation might make your images larger, if yours were already very well optimized. If that happens, please use your originals.

GIF and PNG are lossless formats, in that the compression process does not make any visual modification to the images. For still images, PNG achieves better compression ratio with better visual quality. For animated images, consider using video element instead of a GIF, to achieve better compression.

Always convert GIF to PNG unless the original is animated or tiny (less than a few hundred bytes).
For both GIF and PNG, remove alpha channel if all of the pixels are opaque.
For example, you can use convert binary to optimize your GIF and PNG images with the following command (parameters inside brackets are optional):

convert INPUT.gif_or_png -strip [-resize WxH] [-alpha Remove] OUTPUT.png

cuppa.png
cuppa.png (1,763 Bytes)
convert cuppa.png -strip cuppa_converted.png

cuppa_converted.png
cuppa_converted.png (856 Bytes)
JPEG is a lossy format. The compression process removes visual details of the image, but the compression ratio can be 10x larger than GIF or PNG.

Reduce quality to 85 if it was higher. With quality larger than 85, the image becomes larger quickly, while the visual improvement is little.
Reduce Chroma sampling to 4:2:0, because human visual system is less sensitive to colors as compared to luminance.
Use progressive format for images over 10k bytes. Progressive JPEG usually has higher compression ratio than baseline JPEG for large image, and has the benefits of progressively rendering.
Use grayscale color space if the image is black and white.
For example, you can use convert binary to optimize your JPEG images with the following command (parameters inside brackets are optional):

convert INPUT.jpg -sampling-factor 4:2:0 -strip [-resize WxH] [-quality N] [-interlace JPEG] [-colorspace Gray/sRGB] OUTPUT.jpg

puzzle.jpg
puzzle.jpg (13,501 Bytes)
convert puzzle.jpg -sampling-factor 4:2:0 -strip -quality 85 -interlace JPEG -colorspace sRGB puzzle_converted.jpg

puzzle_converted.jpg
puzzle_converted.jpg (4,599 Bytes)

# End
