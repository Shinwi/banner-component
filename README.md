# banner-component

## Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Lints and fixes files

```
yarn lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

# Documentation

## Component props:

We accept 3 props. mode, items and carouselOnMobil.

Mode and items are obligatory, hence why `required: true`.

Mode only accepts one of 2 values: square or rectangle. Therefore, we added a custom validator to check if the given mod value is one of the two accepted values.

```
validator: function (value) {
    return ['square', 'rectangle'].includes(value.toLowerCase())
  }
```

## computed

- `isMobile` a computed property that returns a boolean value. Checks if we are in a mobile view or now.
- `getRectangleModeImage`: checks if we are in the rectangle mode. If yes, returns pictures with aspect ratio set to rectangle. Otherwise, returns pictures with aspect ratio set to square.
- `getRectangleModeCTA`: returns the item object that is of type cta.
