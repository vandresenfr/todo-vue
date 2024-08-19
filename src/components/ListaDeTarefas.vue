<script setup>
    const props = defineProps(['tarefas', 'tarefasPendentes' ]);
</script>

<template>
    <ul v-if="props.tarefasPendentes > 0" class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada === true }" :for="tarefa.titulo" class="ms-3">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
    <h3 v-else class="mt-5">
        Voce não possui tarefas pendentes
    </h3>
</template>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>