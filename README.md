# AngularNotes
This is where I keep all my notes about Angular 4/5

## Using Tsconfig Paths in Webpack

```JavaScript
{
  "compilerOptions": {
    "baseUrl": "./src",
    "paths": {
      "@datorama/utils/*": ["app/utils/*"],
      "@datorama/pipes/*": ["app/pipes/*"]
    }
  }
}
```
and in Webpack do:

```JavaScript
const { TsConfigPathsPlugin } = require('awesome-typescript-loader');

resolve: {
  plugins: [
     new TsConfigPathsPlugin()
  ]
}
```
## Constructor Parameter Decorators

### @Host
Will search up the component tree to find an ancestor of the given type and inject it.

### @Attribute
An alternative to @Input that allows you to constructor inject the attribute rather than have it as a property (because properties need to be public).

### @Self
Only look in the current components injector for a resolution.  If not found will throw.

### @Optional
The specified constructor parameter can be undefined (not exist in the DI chain used to instantiate the component)