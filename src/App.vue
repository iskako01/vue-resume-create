<template>
  <div class="container column">
    <app-form @add-block="addData"></app-form>
    <app-view :blocks="blocks"></app-view>
  </div>
  <app-load v-if="loading"></app-load>
  <app-comments
    :comments="comments"
    @load-comment="loadingComents"
    @remove-comment="removeComment"
    :show="show"
  ></app-comments>
</template>

<script>
import AppForm from "./components/AppForm.vue";
import AppLoad from "./components/AppLoad.vue";
import AppView from "./components/AppView.vue";
import AppComments from "./components/AppComments.vue";
export default {
  data() {
    return {
      blocks: [],
      comments: [],
      loading: false,
      show: false,
    };
  },
  methods: {
    async loadingComents() {
      this.show = true;
      this.loading = true;
      const res = await fetch(
        "https://jsonplaceholder.typicode.com/comments?_limit=42"
      );
      this.comments = await res.json();
      this.loading = false;
    },
    removeComment() {
      this.show = false;
    },
    addData(block) {
      this.blocks.push(block);
    },
  },
  components: { AppForm, AppLoad, AppView, AppComments },
};
</script>
