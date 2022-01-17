<template>
  <img alt="Vue logo" src="./assets/logo.png">
<div class="col">
  <textarea
    v-model="msg"
    placeholder="Write a message"
    rows="10"
    @keydown.enter.exact.prevent="sendMessage"
    @keydown.shift.enter.exact.prevent="addNewLine"
  ></textarea>

  <div>Message here: {{ msg }}</div>
</div>

</template>

<script>

export default {
  name: 'App',
  components: {
  },
  methods: {
    sendMessage() {
      console.log('Enter is clicked');
    },
    addNewLine() {
      console.log('Shift + Enter are clicked');
      this.msg += '\n';
    }
  },
  data() {
    return {
      msg: ''
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.col {
  display: flex;
  flex-direction: column;
}
</style>
