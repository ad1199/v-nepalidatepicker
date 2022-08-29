<script>
import Vue from "vue";
import VNepalidatepicker from "@/v-nepalidatepicker.vue";

export default Vue.extend({
  name: "ServeDev",
  components: {
    VNepalidatepicker,
  },
  data() {
    return {
      formatedDate: "",
    };
  },
});
</script>

<template>
  <div id="app">
    <v-nepalidatepicker v-model="formatedDate" />
  </div>
</template>
