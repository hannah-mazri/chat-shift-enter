<template>
  <img alt="Vue logo" src="./assets/logo.png">
<div class="col">
  <textarea
    v-model="msg"
    placeholder="Write a message"
    rows="10"
    @keydown.enter.exact.prevent="sendMessage"
  ></textarea>

  <div>Message here: {{ msg }}</div>
  <div>Submitted messages:
    <ul>
      <li v-for="(message, index) in messages" :key="index" style="white-space: pre; text-align: left;">{{ message }}</li>
    </ul>
  </div>

  <button type="button" @click="sendNotification">Send browser notification</button>
</div>

</template>

<script>
export default {
  name: 'App',
  components: {
  },
  methods: {
    sendMessage() {
      console.log('Enter is clicked', this.msg);
      this.messages.push(this.msg);
      this.msg = '';
    },
    addNewLine() {
      console.log('Shift + Enter are clicked');
      this.msg += '\n';
    },
    sendNotification() {
      if  (!("Notification" in window)) {
        alert("This browser does not support desktop notification");
      }

      else if (Notification.permission === 'granted') {
        var notification = new Notification("Customer requests for assistance");
        console.log(notification);
      }

      else if (Notification.permission !== 'denied') {
        Notification.requestPermission().then(function (permission) {
          if (permission === 'granted') {
            var notification = new Notification("Permission granted");
            console.log(notification);
          }
        })
      }
    }
  },
  data() {
    return {
      msg: '',
      messages: []
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
