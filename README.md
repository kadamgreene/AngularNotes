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

### @SkipSelf
Start looking at this components parent for DI resolution (skip self)

### @Optional
The specified constructor parameter can be undefined (not exist in the DI chain used to instantiate the component)

### @Inject
For cases when Angular cannot figure out the expected types for the constructor parameters, you can explicity specify it. (example:  @Inject(ConsoleLogger) logger: Logger)

## ContentChildren cannot cross <ng-content> boundary
When you use @ContentChildren(type, { descendents: true }), it won't look inside any <ng-content></ng-content>.  The "descendents" must be defined in the page that contains the component, so this will work:

```HTML
<div wrapperComponent>
    <Panel>
        <Header></Header>
    </Panel>
</div>
```

when used with:

```Typescript
@ContentChildren(HeaderCompoonent, { descendents: true }) public headers: QueryList<HeaderComponent>
```
