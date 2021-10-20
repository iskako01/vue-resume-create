<template>
  <form class="card card-w30" @submit.prevent="submit">
    <div class="form-control">
      <label for="type">Type of block</label>
      <select id="type" v-model="type">
        <option value="title">Title</option>
        <option value="subtitle">Subtitle</option>
        <option value="avatar">Avatar</option>
        <option value="text">Text</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Value</label>
      <textarea id="value" rows="3" v-model="value"></textarea>
    </div>

    <button class="btn primary" :disabled="isValid">Add</button>
  </form>
</template>

<script>
export default {
  emits: ["add-block"],
  data() {
    return {
      type: "title",
      value: "",
    };
  },
  methods: {
    submit() {
      this.$emit("add-block", {
        type: this.type,
        value: this.value,
        id: Date.now(),
      });
      (this.type = "title"), (this.value = "");
    },
  },
  computed: {
    isValid() {
      return this.value <= 3;
    },
  },
};
</script>

<style>
</style>