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
  methods: {
    toggleSelected() {
      this.selected = !this.selected;

      if (this.selected) {
        this.$emit("selecionarIngrediente", this.ingrediente);
      } else {
        this.$emit("removerIngrediente", this.ingrediente);
      }
    },
  },
  emits: ["selecionarIngrediente", "removerIngrediente"],
};
</script>
<template>
  <button class="btn-ingrediente" @:click="toggleSelected">
    <Tag :texto="ingrediente" :ativa="selected" />
  </button>
</template>

<style scoped>
.btn-ingrediente {
  cursor: pointer;
}
</style>
