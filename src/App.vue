<template>
  <div class="contenedor">
    <h2 class="mt-4">To Do List</h2>
      <form class="mt-4" @submit.prevent="agregarNuevaTarea" > <!--- Agregar nueva tarea-->
        <div class="form-group agregar-tarea">
          <input 
            type="text" 
            class="tarea-input" 
            placeholder="Ingresa una nueva Tarea"
            required
            v-model ="nuevaTarea">
          
          <button type="submit" class="btn submit-tarea">
            <i class="fa-solid fa-circle-plus"></i>
          </button>
        </div>
      </form>

      <h3 class="titulo">Lista</h3>
      <ul class="list-group">
        <Supertarea  @tareaCompletada="borrarTarea($event)" v-for="(tarea, $index) of tareas" :key="$index" :elementoListado="tarea" :indexTarea="$index"/>  
      </ul>
  </div>
</template>
<script>
import  Supertarea from './components/Supertarea.vue'
export default {
  name: 'App',
  data: () =>({
    nuevaTarea: "",
    tareas: ["Estudiar VueJS", "Ver Los Simpsons"]
  }),
  components:{
    Supertarea
  },
  methods:{
    agregarNuevaTarea(){
      this.tareas.unshift(this.nuevaTarea);
      this.nuevaTarea = " ";
    },
    borrarTarea(key){
      this.tareas.splice(key, 1)
    }   
  }
};
</script>

<style>
body{
  font-family: Arial, Helvetica, sans-serif;
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgb(93,13,214);
  background: linear-gradient(0deg, rgba(93,13,214,1) 0%, rgba(250,19,255,1) 100%);
}
.contenedor{
  max-width: 100%;
  background-color: rgba(255,255,255,0.5);
  padding: 25px;
  border-radius: 25px;
  transition: 0.3s ease-in-out;
}

.contenedor:hover{
  -webkit-box-shadow: 0px 13px 31px -8px #770F99; 
  box-shadow: 0px 13px 31px -8px #770F99;
  
}

.titulo{
  margin-bottom: 25px;
}

.agregar-tarea{
  height: 40px;
  font-size: 16px;
  display: flex;
}
.submit-tarea{
  width: 32px;
}
.btn{
  border: none;
  background-color: transparent;
}

.btn > i:hover{
  color: rgb(93,13,214)
}

.tarea-input{
  width: auto;
  padding: 0 5px;
  outline: none;
  border: none;
  border-bottom: solid 1px #272727;
  background-color: transparent;
  margin-right: 15px;
}
.lista-tareas{
  background-color: rgba(255,255,255, 0.9);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px;
  border-radius: 35px;
  margin-bottom: 12px;
}
.list-group{
  padding: 0;
}

</style>