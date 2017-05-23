# react_perf_widget

<!-- <img src="https://s3-us-west-2.amazonaws.com/sia-generic-bucket/perf.gif" alt="Perf widget in action screenshare" width="80%"> -->

<img src="https://s3.amazonaws.com/viking_education/web_development/web_app_eng/perf.gif" alt="Perf widget in action screenshare" width="80%">


The nice people at Facebook created a package called `react-addons-perf` that allows us to profile our development build to identify the worst performance offenders. To use it, install it first as a development dependency:

```language-bash
$ npm install react-addons-perf --save-dev
```

Here are the most useful functions available in `Perf`, but you can check them all out in the [docs](https://facebook.github.io/react/docs/perf.html):

- `Perf.start()` - start recording performance.
- `Perf.stop()` - stop recording performance.
- `Perf.getLastMeasurements()` - obtains the measurements from the last start-stop cycle.
- `Perf.printWasted(measurements)` - prints out the time wasted rendering and performing virtual DOM comparisons for components that did not result in a change in the DOM.
- `Perf.printOperations(measurements)` - provides the list of all operations performed on the underlying DOM. Missing or bad keys set on a list will not show up in the `printWasted` list, so check this one too to make it doesn't have operations that it shouldn't have.

A good strategy is to focus more on `printWasted`, and use `printOperations` or the other functions only if you need more insight. After optimizing `printWasted`, you will probably get more bang for your buck by using DevTools to optimize your core code (using the production build). Remember that our target rendering time is 10 ms, but when using Perf render time is artificially worse since we are using the development build.

You can run the `Perf` functions from individual lines in your code, or you can use this nifty component which overlays the top right of your app, adapted from [this blog post](https://auth0.com/blog/optimizing-react/) by Alex Sears. Just remember to remove it when in production.

And for the styling, add the CSS in **style.css** to your styles.

