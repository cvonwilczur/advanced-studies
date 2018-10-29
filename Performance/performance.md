#Performance

Visitors expect a website to load in at least two seconds.

##Optimizing Network Transfer

###Shrink the Files

####Minimize Text
HTML, JS, and CSS can be minimized using tools like uglifyJS, which parse through code and reduce whitespace.

####Minimize Images
The primary way to change an image size is to change the file format.

SVG - SVGs use vector graphics, are small, great for 4K/retina displays and are customizable via CSS. Usually tend to be simplistic.
JPG - Usually used for photos, things with many colors, complex. Don't support transparency.
PNG - Usually only have a limited number of colors. Support transparency. Good for logos.
GIF - Reduced color count, which allows for smaller size files, ideal for animations.

Use tools like TinyPNG or JPEG-optimizer to reduce image sizes. Also try to use simple illustrations over highly detailed photographs. Also try to lower JPEG image quality by 30-60%. Also resize the image based on the size it will be displayed. Use CDNs like imigx. Remove image metdata.
##Critical Render Path