<script lang="ts">
import type { PropType } from "vue";
import ReceiptCard from "./ReceiptCard.vue";

export default {
  name: "ReceiptList",
  props: {
    receitas: {
      type: Array as PropType<IReceipt[]>,
      required: true,
    },
  },
  components: {
    ReceiptCard,
  },
};
</script>

<template>
  <p class="paragrafo-lg instrucoes">
    Veja as opções de receitas que encontramos com os ingredientes que voce tem
    por aí.
  </p>

  <ul class="receitas">
    <li v-for="receita in receitas" v-bind:key="receita.nome">
      <ReceiptCard :receita="receita" />
    </li>
  </ul>
</template>

<style scoped>
.receitas {
  margin-bottom: 1rem;
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}
</style>
