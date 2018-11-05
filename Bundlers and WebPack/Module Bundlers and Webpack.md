#Bundling

There are a number of tools for bundling, such as webpack, Parcel and rollup.js. These tools help take our files and spit out a smaller, optimized file that can be sent to the browser. Webpack is used in create-react-app. Parcel advertises itself as a zero configuration web bundler.

##Webpack

Webpack has four main ideas:

1) Entry - where does Webpack enter into the project? Usually at index.js. 
2) Output - where should Webpack output all of these files? Usually a build folder.
3) Loaders - Tools that compile or transpile our code.
4) Plugins - Play vital roles in outputting our code