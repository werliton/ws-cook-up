<script lang="ts">
import type { PropType } from "vue";

export default {
  props: {
    categoria: {
      type: Object as PropType<ICategory>,
      required: true,
    },
  },
};
</script>
<template>
  {{ categoria.nome }}
</template>
