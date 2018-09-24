<template>
  <div class="row" style="flex-direction:column;">
    <ChartHeader/>
    <VQuestions/>
    <!-- <PhoneFrame src="https://www.cbpc.ltd/public/topic/201809/?_simulate=1" autoLoad="600" /> -->
  </div>
</template>

<script>
// @ is an alias to /src
// import PhoneFrame from "@/components/PhoneFrame.vue";
import ChartHeader from "@/components/ChartHeader.vue";
import VQuestions from "@/components/VQuestions.vue";
export default {
  name: "home",
  components: {
    // PhoneFrame,
    ChartHeader,
    VQuestions
  }
};
</script>

