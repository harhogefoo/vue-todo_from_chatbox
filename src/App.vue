<template>
  <div id="app">
    <app-message :message="parentMessage"></app-message>
    <input type="text" v-model="task">
    <p>{{ count }} / 20</p>
    <p class="text-alert" v-if="task.length === 0">テキストを入力してください。</p>
    <a @click="add">追加</a>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
    <a :href="url">click me!</a>
  </div>
</template>

<script>
import AppMessage from './Message.vue'

export default {
  components: {
    AppMessage
  },
  name: 'app',
  data () {
    return {
      parentMessage: "this is parent message",
      task: '',
      items: ['本を買う', '牛乳を買う'],
      url: "http://google.com"
    }
  },
  computed: {
    count () {
      return this.task.length
    }
  },
  methods: {
    add () {
      this.items.push(this.task)
      this.task = ''
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
