<script lang="ts">
import Tag from "./Tag.vue";

export default {
  components: { Tag },
  props: {
    ingrediente: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      selected: false,
    };
  },
};
</script>
<template>
  <button class="btn-ingrediente" v-on:click="selected = !selected">
    <Tag :texto="ingrediente" :ativa="selected" />
  </button>
</template>

<style scoped>
.btn-ingrediente {
  cursor: pointer;
}
</style>
