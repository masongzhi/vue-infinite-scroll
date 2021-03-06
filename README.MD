# vue-infinite-scroll

vue-infinite-scroll is an infinite scroll directive for vue.js.

# Install

```Bash
npm install vue-infinite-scroll --save
```

### CommonJS

You can use any build tool which supports `commonjs`:

```JavaScript
// register globally
var infiniteScroll =  require('vue-infinite-scroll');
Vue.use(infiniteScroll)

// or for a single instance
var infiniteScroll = require('vue-infinite-scroll');
new Vue({
  directives: {infiniteScroll}
})

```

Or in ES2015:

```JavaScript
// register globally
import infiniteScroll from 'vue-infinite-scroll'
Vue.use(infiniteScroll)

// or for a single instance
import infiniteScroll from 'vue-infinite-scroll'
new Vue({
  directives: {infiniteScroll}
})

```

### Direct include

You can use the CDN: https://unpkg.com/vue-infinite-scroll, `infiniteScroll` is exposed to `window` and will automatically install itself. Also you can use your local copy:

```HTML
<script src="../node_modules/vue-infinite-scroll/vue-infinite-scroll.js"></script>
```

## Usage

Use v-infinite-scroll to enable the infinite scroll, and use infinite-scroll-* attributes to define its options.

The method appointed as the value of v-infinite-scroll will be executed when the bottom of the element reaches the bottom of the viewport.

```HTML
<div v-infinite-scroll:loadMore="{disabledKey: 'busy', distance: 10}">
  ...
</div>
```

```JavaScript
var count = 0;

new Vue({
  el: '#app',
  data: {
    data: [],
    busy: false
  },
  methods: {
    loadMore: function() {
      this.busy = true;

      setTimeout(() => {
        for (var i = 0, j = 10; i < j; i++) {
          this.data.push({ name: count++ });
        }
        this.busy = false;
      }, 1000);
    }
  }
});
```

## if execute is a Promise
if execute is a Promise, it will be disabled when executing.
```js
if (window.Promise && this.vm[executeName] instanceof window.Promise) {
  this.config._disabled = true;
  this.vm[executeName]().finally(() => (this.config._disabled = false));
}
```

# Options

| Option | Description |
| ----- | ----- |
| disabledKey | infinite scroll will be disabled if the key of this vm.attribute is true. |
| distance | Number(default = 0) - the minimum distance between the bottom of the element and the bottom of the viewport before the v-infinite-scroll method is executed. |
| immediateCheck | Boolean(default = true) - indicates that the directive should check immediately after bind. Useful if it's possible that the content is not tall enough to fill up the scrollable container. |
| eventName | infinite scroll will check again when the event is emitted in Vue instance. |
| throttleDelay | Number(default = 200) - interval(ms) between next time checking and this time  |

## Development

|Command|Description|
|---|---|
|npm run build|Build in umd format|
|npm test|Lint code|

# License

MIT
