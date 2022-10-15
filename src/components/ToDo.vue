<template>
    <div>
        <hr>
        <div>
            <h3>{{ title }}</h3>
        <form @submit.prevent='agregarTarea'>
            <input type="text" v-model="nuevaTarea">
            <button>Agregar Tarea</button>
        </form>
            <div class="listado-tareas">
                <ul>
                    <li v-for="tarea in tareasFiltradas" :key="tarea.id">
                        <input type="checkbox" v-model="tarea.hecho">
                        <span :class="{ 'tarea-completada' : tarea.hecho }">{{ tarea.desc }}</span>
                        <button @click="eliminarTarea(tarea)" class="btn-eliminar">X</button>
                    </li>
                </ul>
                <button @click="ocultarCompletadas = !ocultarCompletadas">
                    {{ ocultarCompletadas ? 'Mostrar' : 'Ocultar' }} completadas</button>
            </div>
        </div>
    </div>
</template>

<script>
let id = 0;
export default {
    props: {
        title: String,
    },
    data() {
        return {
            nuevaTarea: '',
            listadoDeTareas: [
                {id: id++, desc: 'Tarea 1', hecho: true},
                {id: id++, desc: 'Tarea 2', hecho: false},
                {id: id++, desc: 'Tarea 3', hecho: false}
            ],
            ocultarCompletadas: true
        }
    },
    methods: {
        agregarTarea() {
            this.listadoDeTareas.push({id: id++, desc: this.nuevaTarea, hecho: false})
            this.nuevaTarea = ''
        },
        eliminarTarea(tarea_a_eliminar) {
            this.listadoDeTareas = this.listadoDeTareas.filter((t) => t !== tarea_a_eliminar)
        }
    },
    computed: {
        tareasFiltradas() {
            return this.ocultarCompletadas
                ? this.listadoDeTareas.filter((t) => !t.hecho)
                : this.listadoDeTareas
        }
    }
}
</script>

<style>
    .listado-tareas {
        text-align: left;
    }
    .tarea-completada {
        text-decoration: line-through;
    }
    .btn-eliminar {
        margin-left: 7px;
    }
</style>