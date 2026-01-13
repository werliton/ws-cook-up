<script lang="ts">
import { getReceipts } from "@/http";
import ReceiptList from "./ReceiptList.vue";

export default {
  data() {
    return {
      receitas: [] as IReceipt[],
    };
  },
  methods: {
    gotohome() {
      this.$emit("alterar-page");
    },
  },
  async created() {
    this.receitas = await getReceipts();
  },
  components: { ReceiptList },
  emits: ["alterar-page"],
};
</script>
<template>
  <section class="view-receipts">
    <h2 class="cabecalho titulo-receita">Receitas</h2>
    <p>Resultados encontrados: {{ receitas.length }}</p>

    <ReceiptList v-if="receitas.length > 0" :receitas="receitas" />

    <p v-else>
      Ops! Não encontramos resultados para sua busca. Tente novamente.
    </p>
    <img src="@/assets/images/sem-receitas.png" alt="" />
  </section>
  <button class="botao" @:click="gotohome">Editar lista</button>
</template>

<style scoped>
.titulo-receita {
  color: var(--verde-medio, #3d6d4a);
}
.view-receipts {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 2rem;
  width: 100%;
}
.botao {
  width: 19.5rem;
  height: 3.5rem;
  padding: 0.5rem 1rem;
  border-radius: 2rem;
  font-weight: 700;
  color: var(--creme, #fffaf3);
  background: var(--coral, #f0633c);
  box-shadow: 4px 4px 15px 0px rgba(255, 115, 76, 0.25);
  cursor: pointer;
  transition: 0.2s;

  display: flex;
  justify-content: center;
  align-items: center;
}

.botao:hover {
  background: var(--ocre-hover, #d1451e);
}
</style>
