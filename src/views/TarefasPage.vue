<script setup lang="ts">
import { useTarefas } from "../composables/useTarefas";
import CardTarefa from "../components/CardTarefa.vue";
const {
  tarefas,
  busca,
  filtroAtivo,
  filtradas,
  totalPendentes,
  adicionar,
  remover,
  concluir,
} = useTarefas();
const novaTarefa = ref("");
function adicionarNova() {
  adicionar(novaTarefa.value);
  novaTarefa.value = "";
}
</script>

