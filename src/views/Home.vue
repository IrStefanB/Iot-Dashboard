<template>
  <div class="home">
    <img src="../assets/logo.png">
    <LightSensor />
  </div>
</template>

<script>
// @ is an alias to /src
import LightSensor from "@/components/LightSensor.vue";

export default {
  name: "home",
  components: {
    LightSensor
  }
};
</script>
