<template>
  <div class="CompView">{{ num }}</div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  data() {
    return {
      num: 1,
    };
  },
});
</script>
