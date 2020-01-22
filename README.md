# $emit && $on

`vm.$on( event, callback )`

`vm.$emit( event, […args] )`

```js
var bus = new Vue()
// 触发组件 A 中的事件
bus.$emit('id-selected', 1)
// 在组件 B 创建的钩子中监听事件
bus.$on('id-selected', function(id) {
  // ...
})
```

```html
<html>
  <head>
    <title>$emit 和 $on</title>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  </head>
  <body>
    <div id="root">
      <button @click="boost">触发事件</button>
    </div>
    <script>
      new Vue({
        el: '#root',
        data() {
          return {
            message: 'hello vue'
          }
        },
        created() {
          this.$on('my_events', this.handleEvents)
        },
        methods: {
          handleEvents(e) {
            console.log(this.message, e)
          },
          boost() {
            this.$emit('my_events', 'my params')
          }
        }
      })
    </script>
  </body>
</html>
```
