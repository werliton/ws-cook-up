<script lang="ts">
import type { PropType } from "vue";
import Tag from "./Tag.vue";
import SelectedIngredient from "./SelectedIngredient.vue";

export default {
  props: {
    receita: {
      type: Object as PropType<IReceipt>,
      required: true,
    },
  },
  components: {
    Tag,
    SelectedIngredient,
  },
};
</script>
<template>
  <article class="receita">
    <header class="receita__cabecalho">
      <img
        :src="`/imagens/receitas/${receita.imagem}`"
        :alt="`{{ receita.nome }}`"
        class="receita__imagem"
      />
      <h2 class="paragrafo-lg receita__nome">{{ receita.nome }}</h2>
    </header>
  </article>
</template>

<style scoped>
.receita {
  width: 19.5rem;
  border-radius: 1rem;
  background: var(--branco, #fff);
  box-shadow: 4px 4px 10px 0px rgba(68, 68, 68, 0.05);
  height: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.receita__cabecalho {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  width: 100%;
}

.receita__imagem {
  width: 100%;
  border-top-left-radius: 1rem;
  border-top-right-radius: 1rem;
  object-fit: cover;
  box-shadow: 0px 4px 15px 0px rgba(61, 109, 74, 0.25);
}

.receita__nome {
  text-align: center;
  color: var(--verde-medio, #3d6d4a);
  font-weight: 700;
}

.receita__ingredientes {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}
</style>
