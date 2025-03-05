<template>
  <button class="btn" :class="color" @click="$emit('action')">
    <slot>Кнопка без имени</slot>
  </button>
</template>

<script>
export default {
  emits: ["action"],
  props: {
    color: {
      type: String,
      default: "",
      validator(value) {
        return ["primary", "", "danger"].includes(value);
      },
    },
  },
};
</script>
