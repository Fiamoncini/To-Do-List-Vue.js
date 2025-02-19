<script>
export default {
  data() {
    return {
      novaTarefa: "",
      tarefas: []
    };
  },
  methods: {
    adicionarTarefa() {
      if (this.novaTarefa.trim() !== "") {
        this.tarefas.push({ texto: this.novaTarefa, concluida: false });
        this.novaTarefa = "";
      }
    },
    removerTarefa(index) {
      this.tarefas.splice(index, 1);
    },
    alternarConclusao(index) {
      this.tarefas[index].concluida = !this.tarefas[index].concluida;
    }
  }
};
</script>

<template>
  <div class="container">
    <h1>📝 To-Do List</h1>

    <div class="input-container">
      <input v-model="novaTarefa" placeholder="Digite uma nova tarefa">
      <button class="adicionar" @click="adicionarTarefa">➕</button>
    </div>

    <ul>
      <li v-for="(tarefa, index) in tarefas" :key="index" class="tarefa">
        <span :class="{ concluida: tarefa.concluida }" @click="alternarConclusao(index)">
          {{ tarefa.texto }}
        </span>
        <div class="botoes">
          <button class="remover" @click="removerTarefa(index)">❌</button>
          <button class="finalizado" @click="alternarConclusao(index)">✅</button>
        </div>
      </li>
    </ul>
  </div>
</template>
