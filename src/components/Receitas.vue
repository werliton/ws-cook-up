<script lang="ts">
import { getReceipts } from "@/http";
import ReceiptList from "./ReceiptList.vue";
import type { PropType } from "vue";

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
    const response = await getReceipts();
    const receitasMatch = response.filter((receita) =>
      this.ingredientes.every((ingrediente) =>
        receita.ingredientes.includes(ingrediente)
      )
    );
    this.receitas = receitasMatch;
  },
  props: {
    ingredientes: {
      type: Array as PropType<string[]>,
      required: true,
    },
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
      <img src="@/assets/images/sem-receitas.png" alt="" />
    </p>
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
