# vue-blur-loader
A Vue.js component to load images with a blur animation like the site Medium

![Gif](https://i.giphy.com/3GBOL9mk46VgdW816r.gif)

## Installation

```bash
npm install vue-blur-loader --save

#or

yarn add vue-blur-loader

```

## Usage

```javascript
import BlurLoader from 'vue-blur-loader'

export default {
  ...,
  components: { BlurLoader }
}
```

```html
<BlurLoader src='myImagePath.jpg' smallSrc='mySmallImagePath.jpg' />
```

```src``` and ```smallSrc``` can either be an url or a local path or even require with your module bundler

```html
<BlurLoader :src='require("myImagePath.jpg")' :smallSrc='require("mySmallImagePath.jpg")' />
```


You can also provide an element which will be showing before the small image load if the internet connexion is really slow (like a loader gif)

```html
<BlurLoader src='myImagePath.jpg' smallSrc='mySmallImagePath.jpg'>
  <img src='myLoader.gif'>
</BlurLoader>
```