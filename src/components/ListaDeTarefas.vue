<script setup>
const props = defineProps(['tarefas', 'filtro'])
</script>

<template>
    <h5 class="mt-4 ms-2" v-if="props.filtro === 'pendentes' && props.tarefas.length === 0">
        Você não possui tarefas pendentes
    </h5>
    <ul class="list-group mt-4" v-else>
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizado = evento.target.checked" :checked="tarefa.finalizado"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizado }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>