<template>
  <div class="hello">
    <p>Light status -- {{ lightSensorMessage }}</p>
    <p>Light sensor topic -- {{ lightSensorTopic }}</p>
  </div>
</template>

<script>
//import io from 'socket.io-client';
export default {	
	name: "LightSensor",
	data() {
		return {
        lightSensorMessage: '',
        lightSensorTopic: ''	
			}
	},
	methods : {
    },
	beforeCreate() {
    let self = this;
    const ws = new WebSocket('ws://127.0.0.1:3000/');

    ws.addEventListener('open', function (event) {
      console.log('Socket is now open!');
        ws.send('Hello Server!');
    });

    ws.addEventListener('message', function incoming(data) {
        let message = JSON.parse(data.data);
        self.lightSensorMessage = message.message;
        self.lightSensorTopic = message.topic
    });

    ws.addEventListener('close', function close() {
    console.log('Socket disconnected!');
    });
  },
	props: {
		//msg: String
	}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
