<template>
  <div class="home">
    <PhoneFrame src="https://www.cbpc.ltd/public/topic/201809/?_simulate=1" />
  </div>
</template>

<script>
// @ is an alias to /src
import PhoneFrame from "@/components/PhoneFrame.vue";

export default {
  name: "home",
  components: {
    PhoneFrame
  }
};
</script>
