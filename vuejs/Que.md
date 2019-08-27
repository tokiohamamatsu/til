# Que

```js
<template>
  <div class="container">
    <button type="button" @click="dojob()">Que</button>
    <span>{{list}}</span>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      running: false,
      list: []
    };
  },

  methods: {
    dojob() {
      this.enqueue({
        job: function() {
          //
          console.log("a");
        }
      });
    },
    run: function() {
      if (this.running) return;
      this.running = true;
      try {
        var queue = this.list.pop();
        if (queue) {
          console.log(queue);
          queue.job();
        } else {
          return;
        }
      } finally {
        this.running = false;
      }
      this.run();
    },
    enqueue: function(queue) {
      console.log(this);
      this.list.push(queue);
      this.run();
    }
  }
};
</script>
```

`job: function()`の処理を長くするとlistの中身が見れるはず