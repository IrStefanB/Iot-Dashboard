<template>
  <q-page class="flex flex-center bg-blue-grey-10 text-white">
    <!-- <img alt="Quasar logo" src="../assets/logo.png"> -->
    <keep-alive>
      <LightSensor />
    </keep-alive>
  </q-page>
</template>

<style></style>

<script>
import LightSensor from "@/components/LightSensor.vue";
export default {
  name: "PageHome",
  components: {
    LightSensor
  }
};
</script>
