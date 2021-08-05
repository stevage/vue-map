# Community map template

This is a simple template for Maplibre/Mapbox based map using VueJS.

## Project setup

1. `yarn install`
2. Change the project name in package.json
3. Get an account on Mapbox, and replace the public token in Map.vue with your public token. Or use a non-Mapbox source for your tiles.

## Running locally
```
npm run serve
```

## Publishing to Github
1. Set up a Github repo (or fork the original source)
2. Push an initial commit
3. Run `yarn run deploy`
4. Now configure Github Pages to use `docs` directory

### Customising

There aren't many components.

* App.vue: Overall structure of the site
* FeatureInfo.vue: Information shown when you click on something
* Map.vue: Initialises the map and adds stuff to it.