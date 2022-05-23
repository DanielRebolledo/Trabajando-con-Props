<template>
    <div class="tarea">
        <li class="lista-tareas">
            {{ elementoListado}}
            <!-- {{ $index + 1 }} - {{ tarea }} -->
            <button type="submit" class="btn" @click="eliminarTarea($index)">
            <i class="fa-solid fa-trash-can"></i>
        </button>
    </li>
    </div>
</template>

<script>
    export default {
        name: 'Supertarea', 
        props: {
             elementoListado : String,
             indexTarea: Number
         },
        methods: {
            eliminarTarea(){
                this.$emit('tareaCompletada', this.indexTarea)
            },
        },
         
    }

</script>
<style>
    
</style>