# Vue NesBox Emulator
this is a port of [nesbox/emulator](https://github.com/nesbox/emulator) to vuejs.
## Installation
1. Install using npm
```
  npm install diaaeddin/vue-nesbox-emulator --save-dev
```
2. copy `node_modules/vue-nesbox-emulator/public/flash` to your public directory.

then you can use 'vue-nesbox-emulator' component anywhere in your vue application

## Documenation

the component needs the following attributes
- `url` : the url of your game

## Usage

``` html
<div id="app">
    <vue-nesbox-emulator :url="game"></vue-nesbox-emulator>
</div>
```
``` javascript
import Vue from "vue";
import VueNesboxEmulator from "vue-nesbox-emulator";

var app = new Vue({
    el: "#app",
    components: {
        VueNesboxEmulator
    },
    data: {
        game: "your game url"
    }
});

```

## License
MIT
