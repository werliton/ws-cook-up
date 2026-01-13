<script lang="ts">
import IngredientList from "./IngredientList.vue";
import Receitas from "./Receitas.vue";

import YourList from "./YourList.vue";

type Page = "main" | "receitas";

export default {
  data() {
    return {
      ingredientes: [] as string[],
      page: "main" as Page,
    };
  },
  components: { IngredientList, YourList, Receitas },
  methods: {
    adicionaringrediente(ingrediente: string) {
      this.ingredientes.push(ingrediente);
    },
    removerIngrediente(ingrediente: string) {
      console.log(ingrediente, this.ingredientes);

      this.ingredientes = this.ingredientes.filter(
        (item) => item != ingrediente
      );
    },
    alterarPage() {
      this.page = this.page == "receitas" ? "main" : "receitas";
    },
  },
};
</script>
<template>
  <main class="conteudo-principal">
    <YourList :ingredientes="ingredientes" />
    <KeepAlive include="IngredientList">
      <IngredientList
        v-if="page == 'main'"
        @selecionar-ingrediente="adicionaringrediente"
        @remover-ingrediente="removerIngrediente"
        @alterar-page="alterarPage"
      />
      <Receitas
        v-else-if="page == 'receitas'"
        @alterar-page="alterarPage"
        :ingredientes="ingredientes"
      />
    </KeepAlive>
  </main>
</template>

<style scoped>
.conteudo-principal {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #fffaf3);
  color: var(--cinza, #444);

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}

@media only screen and (max-width: 1300px) {
  .conteudo-principal {
    padding: 5rem 3.75rem;
    gap: 3.5rem;
  }
}

@media only screen and (max-width: 767px) {
  .conteudo-principal {
    padding: 4rem 1.5rem;
    gap: 4rem;
  }
}
</style>
