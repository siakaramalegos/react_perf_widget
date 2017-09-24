# React Perf Widget
The nice people at Facebook created a package called `react-addons-perf` that allows us to profile our development build to identify the worst performance offenders. This package contains a React Component you can use to add a GUI widget while in development to profile your applications:

<!-- <img src="https://s3-us-west-2.amazonaws.com/sia-generic-bucket/perf.gif" alt="Perf widget in action screenshare" width="80%"> -->

<img src="https://s3.amazonaws.com/viking_education/web_development/web_app_eng/perf.gif" alt="Perf widget in action screenshare" width="80%">

If you attended my talk on **Lightning Fast React Apps**, links to the slides and resources can be found [below](#lightning-fast-react-apps)!

## Installation
To use this widget, install the perf package first as a development dependency:

```language-bash
$ npm install react-addons-perf --save-dev
```

## About Perf
Here are the most useful functions available in `Perf`, but you can check them all out in the [docs](https://facebook.github.io/react/docs/perf.html):

- `Perf.start()` - start recording performance.
- `Perf.stop()` - stop recording performance.
- `Perf.getLastMeasurements()` - obtains the measurements from the last start-stop cycle.
- `Perf.printWasted(measurements)` - prints out the time wasted rendering and performing virtual DOM comparisons for components that did not result in a change in the DOM.
- `Perf.printOperations(measurements)` - provides the list of all operations performed on the underlying DOM. Missing or bad keys set on a list will not show up in the `printWasted` list, so check this one too to make it doesn't have operations that it shouldn't have.

A good strategy is to focus more on `printWasted`, and use `printOperations` or the other functions only if you need more insight. After optimizing `printWasted`, you will probably get more bang for your buck by using DevTools to optimize your core code (using the production build). Remember that our target rendering time is 10 ms, but when using Perf render time is artificially worse since we are using the development build.

## How to use this widget
You can run the `Perf` functions from individual lines in your code, or you can use this nifty component which overlays the top right of your app, adapted from [this blog post](https://auth0.com/blog/optimizing-react/) by Alex Sears. Just remember to remove it when in production.

And for the styling, add the CSS in **style.css** to your styles.

## Lightning Fast React Apps
If you attended my talk, and want to find the slides, you can check them out [here](https://speakerdeck.com/siakaramalegos/lightning-fast-react-apps). Here are all the extra resources I shared in that presentation:

**Slide resources and extra reading**

- [The need for mobile speed: How mobile latency impacts publisher revenue](https://www.doubleclickbygoogle.com/articles/mobile-speed-matters/) by DoubleClick
- [Spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator) documentation by MDN
- [Immutable.js](https://facebook.github.io/immutable-js/)
- [What are the benefits of immutability?](http://redux.js.org/docs/faq/ImmutableData.html#benefits-of-immutability)
- [Pros and Cons of using immutability with React.js](http://reactkungfu.com/2015/08/pros-and-cons-of-using-immutability-with-react-js/)

**Chrome DevTools**

- [Real time performance audit with Chrome DevTools](https://forwardcourses.com/lectures/91), lecture and demo by Jon Kuperman
- [Chrome DevTools docs](https://developers.google.com/web/tools/chrome-devtools/) by Google
- [Analyzing Network Performance](https://developers.google.com/web/tools/chrome-devtools/network-performance/) by Kayce Basques at Google
- [Analyzing Runtime Performance](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/) by Kayce Basques at Google

**React + Redux Performance**

- [Optimizing Performance](https://facebook.github.io/react/docs/optimizing-performance.html), [Reconciliation](https://facebook.github.io/react/docs/reconciliation.html), [Performance Tools](https://facebook.github.io/react/docs/perf.html), [PureComponent](https://facebook.github.io/react/docs/react-api.html#react.purecomponent) official docs by Facebook
- [Never Bind in Render](https://ryanfunduk.com/articles/never-bind-in-render/) by Ryan Funduk
- [Don't Use Bind When Passing Props](https://daveceddia.com/avoid-bind-when-passing-props/) by Dave Ceddia
- [9 things every React.js beginner should know](https://camjackson.net/post/9-things-every-reactjs-beginner-should-know) by Cam Jackson - opinionated but some great tips
- [Optimizing the Performance of Your React Application](https://auth0.com/blog/optimizing-react/) by Alex Sears, includes a tutorial
- [How to Benchmark React Components: The Quick and Dirty Guide](https://engineering.musefind.com/how-to-benchmark-react-components-the-quick-and-dirty-guide-f595baf1014c) by Scott Domes
- [Performance Engineering With React](https://benchling.engineering/performance-engineering-with-react-e03013e53285) and [A Deep Dive Into React Perf Debugging](https://benchling.engineering/a-deep-dive-into-react-perf-debugging-fd2063f5a667) by Saif Hakim
- [Reselect npm package](https://github.com/reactjs/reselect), by the React Community 
- [React/Redux Performance Tuning Tips](https://medium.com/@arikmaor/react-redux-performance-tuning-tips-cef1a6c50759) by Arik Maor




