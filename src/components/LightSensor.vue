<template>
  <q-card inline style="width: 500px;background:rgb(44, 62, 80)">
    <q-card-media>
      <img style="max-width:200px;margin:auto" src="../assets/bulb.png" />
    </q-card-media>
    <q-card-separator style="height:2px" />
    <q-card-title>
      Office
    </q-card-title>
    <q-card-main>
      <p>Light status -- {{ lightSensorMessage }}</p>
      <p>Light sensor topic -- {{ lightSensorTopic }}</p>
    </q-card-main>
    <q-card-separator style="height:2px" />
    <!-- <q-card-actions>
      <q-btn flat round dense icon="event" />
      <q-btn flat label="5:30PM" />
      <q-btn flat label="7:30PM" />
      <q-btn flat label="9:00PM" />
      <q-btn flat color="primary" label="Reserve" />
    </q-card-actions> -->
  </q-card>
</template>

<script>
export default {
  name: "LightSensor",
  data() {
    return {
      lightSensorMessage: "",
      lightSensorTopic: ""
    };
  },
  methods: {},
  beforeCreate() {
    let self = this;
    const ws = new WebSocket("ws://192.168.0.103:3000/");

    ws.addEventListener("open", function() {
      console.log("Socket is now open!");
      ws.send("Hello Server!");
    });

    ws.addEventListener("message", function incoming(data) {
      let message = JSON.parse(data.data);
      self.lightSensorMessage = message.message;
      self.lightSensorTopic = message.topic;
    });

    ws.addEventListener("error", function() {
      console.log("Socket error!");
    });

    ws.addEventListener("close", function close() {
      console.log("Socket disconnected!");
      ws.send("Socket disconnected!");
    });
  },
  props: {
    //msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
