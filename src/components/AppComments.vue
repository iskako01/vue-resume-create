<template>
  <div class="container">
    <p>
      <button class="btn primary" @click="$emit('load-comment')" v-if="!show">
        Upload Comments
      </button>
      <button class="btn danger" @click="$emit('remove-comment')" v-else>
        Remove Comments
      </button>
      {{ show }}
    </p>
    <div class="card" v-if="show">
      <h2>Comments</h2>
      <ul class="list">
        <li class="list-item" v-for="comment in comments" :key="comment.id">
          <div>
            <p>
              <strong>{{ comment.email }}</strong>
            </p>
            <small>{{ comment.body }}</small>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  emits: ["load-comment", "remove-comment"],
  props: ["comments", "show"],
};
</script>

<style>
</style>