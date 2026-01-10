<script lang="ts">
import { getCategories } from "@/http";

export default {
  data() {
    return {
      categorias: getCategories(),
    };
  },
};
</script>

<template>
  <section class="selecionar-ingredientes">
    <h2 class="cabecalho titulo-ingredientes">Ingredientes</h2>

    <p class="paragrafo-lg instrucoes">
      Selecione abaixo os ingredientes que você tem em casa para que possamos
      sugerir receitas que você pode fazer com eles.
    </p>

    <div class="categorias">
      <ul v-for="item in categorias">
        <li>{{ item.nome }}</li>

        <ul v-for="ingrediente in item.ingredientes">
          <li>{{ ingrediente }}</li>
        </ul>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.selecionar-ingredientes {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.titulo-ingredientes {
  color: var(--verde-medio, #3d6d4a);
  display: block;
  margin-bottom: 1.5rem;
}

.instrucoes {
  margin-bottom: 2rem;
}

.categorias {
  margin-bottom: 1rem;
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.dica {
  align-self: flex-start;
  margin-bottom: 3.5rem;
}

@media only screen and (max-width: 767px) {
  .dica {
    margin-bottom: 2.5rem;
  }
}
</style>
