# motley-render
res.render() middleware for serving auto-compiled handlebars/markdown templates in Motley

```
module.exports = function container (get, set) {
  var handlebars = get('vendor.handlebars').create();
  set('@middleware.render.handlebars', handlebars);
  var options = get('conf.middleware.render');
  options.handlebars = handlebars;
  var Downer = get('vendor.downer').Downer;
  var downer = new Downer(get('conf.middleware.render.paths'), options);
  set('@middleware.render.downer', downer);
  return downer.middleware(options);
};
```
