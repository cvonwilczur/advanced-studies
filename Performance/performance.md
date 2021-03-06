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

###Reduce Number of Files
Reduce reliance on external libraries; reduce number of images. The browser will only download a set number of files at a time, so reducing this burden improves speed.

##Critical Render Path
The browser receives the HTML file, which begins to build the DOM. As it parses the HTML file, it receives the CSS, which pauses the creation of the DOM to pull the CSS file. Once this completes, it continues moving forward, building the DOM until it reaches the JS file and reads it.

Once all of this is done, the browser compiles the DOM and CSSOM into a render tree, knowing exactly what to render onto the page.

DOM -> CSSOM -> Render Tree -> Layout -> Paint

Load styles as soon as possible and scripts as late as possible. Get the CSS to the browser as soon as possible; JavaScript requires CSS and HTML parsing to be finished before it can run. 

General Tips:

HTML
- Load style tag in the < head >
- Load script right before < /body >

CSS
- Only load whatever is needed
- Above the fold loading
- Media attributes
- Less specificity

JS
- Load scripts asynchronously 
    - use script for critical scripts
    - use async for third party scripts that don't affect DOM
    - any third party scripts unimportant for above the fold items can be defered
- Defer loading of scripts
- Minimize DOM manipulation
- Avoid long running JavaScript


Modern browsers are only smart enough to conduct a partial redraw, so when we use JavaScript to manipulate the DOM, we have to do so sparingly to minimize performance impacts.

###HTTP/2

HTTP/2 may change how we consider resources. Physically combining files may no longer be necssary with HTTP/2, as server requests are faster with HTTP/2.