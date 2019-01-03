<template>
  <q-page padding class="bg-blue-grey-10 text-white">
    <hello-world />
  </q-page>
</template>


<script>
import HelloWorld from "@/components/HelloWorld.vue"; 

export default {
  name: "PageAbout",
  components: { 
    HelloWorld 
  }
};
</script>
