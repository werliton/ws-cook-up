<script lang="ts">
import IngredientList from "./IngredientList.vue";
import MainButton from "./MainButton.vue";

import YourList from "./YourList.vue";

export default {
  data() {
    return {
      ingredientes: [] as string[],
    };
  },
  components: { IngredientList, YourList, MainButton },
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
  },
};
</script>
<template>
  <main class="conteudo-principal">
    <YourList :ingredientes="ingredientes" />
    <IngredientList
      @selecionar-ingrediente="adicionaringrediente"
      @remover-ingrediente="removerIngrediente"
    />
    <div class="pre-footer">
      <p>*Atenção: consideramos que você tem em casa sal, pimenta e água.</p>

      <div class="button-container">
        <MainButton text="Buscar receitas" />
      </div>
    </div>
  </main>
</template>

<style scoped>
.pre-footer {
  padding: 0rem 80px;
  width: 100%;
  display: flex;
  gap: 3.5rem;
  justify-content: start;
  flex-direction: column;
}

.button-container {
  display: flex;
  justify-content: center;
}

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
