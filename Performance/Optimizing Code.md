#Optimizing code

Once a file is downloaded, one of JavaScript's heaviest costs is parsing and compiling the code into a Render Tree.

We can use Chrome Tools to analyze the parse and compile using the Performance tab. The yellow Scripting parts are the JavaScript that is running when a page loads. The more javascript you send, the longer it will take to parse and compile.

JavaScript execution happens on the main thread, which can be blocking with heavy JavaScript.

Animations require a lot of processing power, so be sure to avoid going overboard with them. One of the biggest culprits is triggering animations via scrolling events. Don't overload smartphones, which tend to have slower processors.
