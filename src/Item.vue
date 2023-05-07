<script setup>
import { ref } from "vue";

const props = defineProps(["id", "name"]);

const showRedBox = ref(false);
</script>

<template>
  <div>
    {{ `id${props.id}: ${props.name}` }}
    <button @click="showRedBox = !showRedBox">show / hide red box</button>
    <div
      v-if="showRedBox"
      style="background-color: red; width: 50px; height: 50px"
    ></div>
  </div>
</template>
