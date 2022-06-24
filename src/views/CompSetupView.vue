<template>
  <div class="CompView">
    <div :style="{ backgroundColor: title.color }">{{ title.title }}</div>
    <div class="CompView">{{ num }}</div>

    <div v-for="item in items" :key="item.id">
      {{ item.name }}
    </div>

    <input v-model="itemName" @keydown.enter="addToDo(newToDo(itemName))" />
  </div>
</template>
<script lang="ts">
import { defineComponent, PropType } from "vue";
import { ToDo, titleInfo } from "@/types";

export default defineComponent({
  props: {
    title: {
      type: Object as PropType<titleInfo>,
      required: true,
    },
  },
  data() {
    return {
      num: 1,
      items: [] as ToDo[],
      itemName: "",
    };
  },
  created() {
    this.items.push({
      id: 1,
      name: "vue3",
      completed: false,
    });
  },
  methods: {
    newToDo(itemNme: string): ToDo {
      return {
        id: this.items.length + 1,
        name: itemNme,
        completed: false,
      };
    },
    addToDo(item: ToDo): void {
      this.items.push(item);
      this.itemName = "";
    },
  },
});
</script>
