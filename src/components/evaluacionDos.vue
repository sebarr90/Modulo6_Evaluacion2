<template>
    <div class="tareas">
        <p v-show="tareas.length===0">No tienes tareas pendientes!!</p>
    <ul v-for="(tarea, index) in tareas" :key="index">
        
        <li> {{ index+1 }} =  {{ tarea }} <input type="checkbox" v-model="selection[index]"></li>
    </ul>
    
</div>
<div>
    <label for="tarea">Ingresa o Modifica una Tarea:</label>
    <br>
    <textarea v-model="tarea" id="tarea"></textarea>
    <br>
    
</div>
<button type="button" @click="agregarTarea">Agregar Tarea</button>

<button type="button" @click="modificarTarea" v-show="tareas.length!==0">Modificar</button>
<button type="button" class="eliminar" @click="eliminarTarea" v-show="tareas.length!==0">Eliminar Tarea </button>

</template>

<script>
export default {
  name: 'ejercicioDos',
  data() {
    return {
      tareas: [],
      tarea: '',
      selection: [] 
    }
  },
  methods: {
    agregarTarea() {
      if (this.tarea.trim() !== '') { 
        this.tareas.push(this.tarea);
        this.selection.push(false); 
        this.tarea = ''; 
      }
    },
    modificarTarea() {
      this.selection.forEach((isSelected, index) => {
        if (isSelected) {
          this.tareas[index] = this.tarea; 
          this.selection[index] = false; 
        }
      });
      this.tarea = '';
    },
    eliminarTarea() {
        this.selection.forEach((isSelected, index) => {
        if (isSelected) {
        this.tareas.splice(index, 1);
          this.selection[index] = false; 
        }
      }); 
    }
  }
}

</script>

<style scoped>
/* Estilos generales */
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 10px;
    padding: 20px;
}

/* Contenedor principal */
div {
    margin-bottom: 20px;
}

/* Estilo para la lista de tareas */
ul {
    list-style-type: none; /* Elimina los puntos de la lista */
    padding: 0; /* Elimina el padding por defecto */
}

p{ padding: 10px; 
    color: grey;
    border-bottom: 1px solid #ccc;
    cursor: pointer;
    font-size: x-large;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    background: #fff; /* Fondo blanco */
    margin: 5px 0; /* Espaciado entre tareas */
    padding: 10px; /* Espaciado interno */
    border-radius: 5px; /* Bordes redondeados */
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Sombra suave */
    display: flex; /* Flexbox para alinear checkbox y texto */
    align-items: center;  
}
/* Estilo para cada tarea */
li {
    padding: 10px; 
    color: grey;
    border-bottom: 1px solid #ccc;
    
    font-size: x-large;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    background: #fff; /* Fondo blanco */
    margin: 5px 0; /* Espaciado entre tareas */
    padding: 10px; /* Espaciado interno */
    border-radius: 5px; /* Bordes redondeados */
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Sombra suave */
    display: flex; /* Flexbox para alinear checkbox y texto */
    align-items: center; /* Centra verticalmente */
}
input{
    cursor: pointer;
}

/* Estilo para el textarea */
textarea {
    margin-bottom: 20px;
    width: 80%; /* Ancho completo */
    height: 100px; /* Altura fija */
    padding: 10px; /* Espaciado interno */
    border: 1px solid #ccc; /* Borde gris claro */
    border-radius: 5px; /* Bordes redondeados */
    resize: none; /* Deshabilita el redimensionamiento */
}

.tareas{
    width: 80%;
    padding: 10px;
}
/* Estilo para los botones */
button {
    background-color: #28a745; /* Color verde */
    color: white; /* Texto blanco */
    border: none; /* Sin borde */
    padding: 10px 15px; /* Espaciado interno */
    border-radius: 5px; /* Bordes redondeados */
    cursor: pointer; /* Cambia el cursor al pasar */
    margin-right: 10px; /* Espaciado entre botones */
    transition: background-color 0.3s; /* Transición suave para el color */
}

.eliminar {
    background-color: #dc3545;
    color: white; /* Texto blanco */
    border: none; /* Sin borde */
    padding: 10px 15px; /* Espaciado interno */
    border-radius: 5px; /* Bordes redondeados */
    cursor: pointer; /* Cambia el cursor al pasar */
    margin-right: 10px; /* Espaciado entre botones */
    transition: background-color 0.3s; 
}

/* Estilo para los botones al pasar el mouse */
button:hover {
    background-color: #218838; /* Color verde más oscuro al pasar el mouse */
}

.eliminar:hover{
    background-color: #b71c1c; 
}

/* Estilo para el label */
label {
    font-weight: bold; /* Texto en negrita */
}
</style>