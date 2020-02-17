# How to implement client-side routing in a React app that has been deployed to Github pages.

Have you set up a ``<BrowserRouter>`` in your application as you may normally do, tested it locally, but found that it no longer works when deployed to Github Pages?  The [create-react-app documentation](https://create-react-app.dev/docs/deployment#github-pages) covers this and explains why:

> GitHub Pages doesn’t support routers that use the HTML5 pushState history API under the hood (for example, React Router using browserHistory). This is because when there is a fresh page load for a url like ``http://user.github.io/todomvc/todos/42`` where ``/todos/42`` is a frontend route, the GitHub Pages server returns 404 because it knows nothing of ``/todos/42``.

So how do we get around this? Well, it turns our that ``react-router-dom`` has some alternatives to the ``<BrowserRouter>`` api, for our purposes we will be implementing a ``<HashRouter>``.

Without getting into too much detail, the main difference is that ``<HashRouter>`` takes the base url, in our case ``https://yourname.github.io/your-project`` and appends a ``/#/`` to the end to separate the base from the rest of the route url.  This would result in something like: ``https://.../#/portfolio``.

---

## Setting up the ``<HashRouter>``:

The ``<HashRouter>`` is basically a replacement for ``<BrowserRouter>`` and you should be able to drop it into your ``<App />`` component in the same manner. You will need to import it:

```javascript
import { HashRouter, Route } from 'react-router-dom';
```

and you will use it as a wrapper for all of your ``<Route>`` components:

```javascript
const RouterComponent = () => {
  return (
    <HashRouter basename='/'>
      <Route exact path="/" component={Home} />
      <Route path="/blog" component={Blog} />
      <Route path="/projects" component={Projects} />
    </HashRouter>
  )
}
```

That's it for this one!  If you would like a full-on walkthrough of setting up a single-page React application with client-side routing, please refer to [How to build a React App with client-side routing](./react-app-routing)