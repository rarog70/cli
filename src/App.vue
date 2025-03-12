<template>
  <div class="container pt1">
    <div class="card">
      <h2>Динамические и ассинхронные компоненты</h2>
      <app-button
        :color="active === 'one' ? 'primary' : ''"
        @action="active = 'one'"
        >One</app-button
      >
      <app-button
        :color="active === 'two' ? 'primary' : ''"
        @action="active = 'two'"
        >Two</app-button
      >
    </div>
    <component
      :is="active === 'one' ? 'app-text-one' : 'app-text-two'"
    ></component>
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
};
</script>
