<script setup>
import { ref } from "vue";
import Item from "./Item.vue";
import {
  useSortable,
  moveArrayElement,
} from "@vueuse/integrations/useSortable";

const items = ref([
  { id: "0", name: "a" },
  { id: "1", name: "b" },
  { id: "2", name: "c" },
]);

useSortable("#card-wrapper-state-not-kept", items);

useSortable("#card-wrapper-state-kept", items, {
  onUpdate: (e) => {
    const newCards = items.value.slice();
    moveArrayElement(newCards, e.oldIndex, e.newIndex);
    items.value = newCards;
  },
});
</script>

<template>
  <div>state not kept</div>
  <div id="card-wrapper-state-not-kept">
    <Item
      v-for="card in items"
      :key="card.id"
      :id="card.id"
      :name="card.name"
    />
  </div>

  <div style="margin-top: 30px">state kept</div>
  <div id="card-wrapper-state-kept">
    <Item
      v-for="card in items"
      :key="card.id"
      :id="card.id"
      :name="card.name"
    />
  </div>
</template>
