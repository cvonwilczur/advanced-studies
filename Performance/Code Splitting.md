#Code-Splitting

In order to use code-splitting, the import keyword is crucial. If we put import anywhere inside the file outside of the top, React knows that it is a dynamic import request and will only request it when the conditions for the code are met.

if(route === 'page2') {
  import('./components/Page2').then((page2) => {
    this.setState({route: route, component: Page2})
    });
}


##A Cleaner Version

What if we had an Async Component that we could wrap around something, and that component would be loaded in asynchronously?

With AsyncComponent, you can create a higher-order component, which is a component that returns another component.

Example:

export default function asyncComponent(importComponent){
  class AsyncComponent extends Component {
    constructor(props) {
      super(props);
      this.state = {
        component: null
      }
    }

    async componentDidMount(){
      const { default: component } = await importComponent();
      this.setState({
        component: component;
        })
    }

    render() {
      const Component = this.state.component;
      return Component ?< Component {...this.props} />
    }
  }
}
