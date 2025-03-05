<template>
  <div class="card">
    <h3>{{ id }} {{ title }}</h3>
    <app-button @action="open">{{
      newIsOpen ? "Закрыть" : "Открыть"
    }}</app-button>
    <app-button color="danger" v-if="wasRead" @action="$emit('unmark', id)"
      >Отметить непрочитаной</app-button
    >
    <div v-if="newIsOpen">
      <hr />
      <p>
        {{ body }}
      </p>
      <app-button text="" v-if="!wasRead" color="primary" @action="mark"
        >Прочесть новость</app-button
      >
    </div>
  </div>
</template>

<script>
import AppButton from "./AppButton";
export default {
  props: {
    wasRead: {
      type: Boolean,
    },
    title: {
      type: String,
      required: true,
    },
    id: {
      type: Number,
      required: true,
    },
    isOpen: {
      type: Boolean,
    },
    body: {
      type: String,
    },
  },
  emits: {
    "open-news": null,
    "read-news"(id) {
      if (id) {
        return true;
      }
    },
    unmark: null,
  },
  data() {
    return {
      newIsOpen: this.isOpen,
    };
  },
  methods: {
    open() {
      this.newIsOpen = !this.newIsOpen;
      if (this.newIsOpen) {
        this.$emit("open-news");
      }
    },
    mark() {
      this.newIsOpen = false;
      this.$emit("read-news", this.id);
    },
    unmark() {
      this.$emit("unmark", this.id);
    },
  },
  components: {
    AppButton,
  },
};
</script>
