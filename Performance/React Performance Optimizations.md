#React Performance Optimizations

In localhost, add ?react_perf, which will enable additional performance features in Chrome dev tools. React_perf allows us to see our components and what they're doing in the performance tab. We'll specifically want to look at the CPU section, which reflects our JavaScript usage.

In the User Timing section, if you scroll in, you can see what each React component is doing. Whenever a component is updating, it's hogging the mainthread, and the timeline breaks down each step and what life-cycle each component is in.

This will be useful for testing to see where your bottlenecks are.

##Redux Benefits

We can directly connect child components using Redux's component to prompt updates to the State lower down the tree, which will be less of a CPU-drain. This is an architectural decision made on a team level, as it does complicate the overall benefit of Redux.


##React Developer tools
An additional plugin for ChromeDevTools. A useful element is component highlighting, which shows us which components are being changed and rerendered on a page. This is helpful for detecting unnecessary render cycle (for example, your header may be highlighted, which would usually be unnecessary).

##shouldComponentUpdate

Should component update is a React lifecycle hook that controls whether or not the component will update.

shouldComponentUpdate(nextProps, nextState) {
  return false;
}

Try to avoid overusing this, as the check itself is performance-inhibiting. Overusing shouldComponentUpdate, particularly with counters and checks if the counter has reached a certain number, may have a negative effect.

##PureComponent

React also has pureComponents, which means the component will only change if the props change. However, it uses shallow comparison of props, so deeply-nested objects may actually not show a change for pureComponent.
