<template>
  <v-select
    :value="value"
    v-bind="options"
    @change="onChange"
    @input="onInput"
    data-test="c-select"
  >
    <slot />
  </v-select>
</template>

<script>
import CustomComponentMixin from "../mixins/CustomComponentMixin";
export default {
  name: "c-select",
  mixins: [CustomComponentMixin],
  props: {
    value: {
      type: [Number, String, Object],
      default: ""
    }
  }
};
</script>
