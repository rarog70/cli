<template>
  <div class="container pt1">
    <div class="card">
      <h2>Динамические и ассинхронные компоненты</h2>
      <app-button :color="oneColor" @action="active = 'one'">One</app-button>
      <app-button :color="twoColor" @action="active = 'two'">Two</app-button>
    </div>
    <keep-alive>
      <component :is="componentName"></component>
    </keep-alive>
  </div>
</template>

<script>
import AppTextOne from "./AppTextOne.vue";
import AppTextTwo from "./AppTextTwo.vue";
import AppButton from "./AppButton.vue";
export default {
  data() {
    return {
      active: "one",
    };
  },
  components: { AppTextOne, AppTextTwo, AppButton },
  methods: {},
  computed: {
    componentName() {
      return "app-text-" + this.active;
    },
    oneColor() {
      return this.active === "one" ? "primary" : "";
    },
    twoColor() {
      return this.active === "two" ? "primary" : "";
    },
  },
};
</script>
