# How to implement client-side routing in a React app that has been deployed to Github pages.

Have you set up a ``<BrowserRouter>`` in your application as you may normally do, tested it locally, but found that it no longer works when deployed to Github Pages?  The [create-react-app documentation](https://create-react-app.dev/docs/deployment#github-pages) covers this and explains why:

> GitHub Pages doesn’t support routers that use the HTML5 pushState history API under the hood (for example, React Router using browserHistory). This is because when there is a fresh page load for a url like ``http://user.github.io/todomvc/todos/42`` where ``/todos/42`` is a frontend route, the GitHub Pages server returns 404 because it knows nothing of ``/todos/42``.

So how do we get around this? Well, it turns our that ``react-router-dom`` has some alternatives to the ``<BrowserRouter>`` api, such as ``<StaticRouter>``, ``<MemoryRouter>``, and ``<HashRouter>``.  For our purposes we will be implementing a ``<HashRouter>``.

Without getting into too much detail, the main difference is that ``<HashRouter>`` takes the base url, in our case ``https://yourname.github.io/your-project`` and appends a ``/#/`` to the end to separate the base from the rest of the route url.  This would result in something like: 

``https://yourname.github.io/your-project/#/portfolio`` or ``https://yourname.github.io/your-project/#/resume`` depending on where in your application you would like to go.

---

