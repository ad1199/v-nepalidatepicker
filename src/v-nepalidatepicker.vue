<template>
  <div class="datepicker" @click.stop>
    <input
      type="text"
      :class="this.classValue"
      v-model="formatedValue"
      @focus="show()"
      :placeholder="this.placeholder"
    />
    <v-nepalidatepicker-inline
      v-if="visible"
      v-bind="$attrs"
      v-model="formatedValue"
      @select="hide"
    ></v-nepalidatepicker-inline>
  </div>
</template>

<script>
import DatepickerInline from "./v-nepalidatepicker-inline.vue";
export default {
  components: {
    "v-nepalidatepicker-inline": DatepickerInline,
  },
  props: {
    classValue: { type: String, default: "" },
    value: { type: String, default: "" },
    placeholder: { type: String, default: "" },
  },
  data() {
    return {
      visible: false,
      formatedValue: this.value,
    };
  },
  methods: {
    show() {
      this.visible = true;
      setTimeout(() => document.addEventListener("click", this.hide), 200);
    },
    hide() {
      this.visible = false;
      document.removeEventListener("click", this.hide);
    },
  },

  watch: {
    formatedValue(formatedValue) {
      this.$emit("input", formatedValue);
    },
    value(value) {
      this.formatedValue = value;
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  box-sizing: border-box;
  font-family: "Open Sans", sans-serif;
}
.datepicker {
  position: relative;
}
</style>
