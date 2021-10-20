<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        :is="'app-' + block.type"
        v-bind="{ value: block.value }"
      ></component>
    </template>
    <h3 v-else>Add the first block to see the result</h3>
  </div>
</template>

<script>
import AppTitle from "./select/AppTitle.vue";
import AppSubtitle from "./select/AppSubtitle.vue";
import AppAvatar from "./select/AppAvatar.vue";
import AppText from "./select/AppText.vue";
export default {
  props: ["blocks"],

  components: { AppTitle, AppSubtitle, AppAvatar, AppText },
};
</script>

<style>
</style>