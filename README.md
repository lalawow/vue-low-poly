# Vue-Low-Poly

> An low-poly image generator component for Vue.js.

## Installation

### yarn
```bash
$ yarn add vue-low-poly
```

### npm

```bash
$ npm install vue-low-poly
```

## Using the component

```vue
<template>
 <div id="app">
  <vue-low-poly src="./sample.png"/>
 </div>
</template>

<script>
import VueLowPoly from "vue-low-poly";

export default {
  name: "App",
  data() {
    return {
    };
  },
  components: {
    VueLowPoly
  }
};
</script>
```

## API
### Attributes
| Attr. Name | Description | Type | Default Value | Accepted Values
|-----|-----|-----|-----|-----|
| src | original image's src | string | "" | - |
| width | image width(px) | number | 800 | - |
|height | image height(px) | number | 600 | - |
| points | amount of points for triangles | number | 7500 | - |
|accuracy | portion of points on the special postion(%) | number | 75 | - |
| grayscale | whether output the image in grayscale style | boolean | false | true/false |









