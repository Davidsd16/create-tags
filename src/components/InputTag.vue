<script>
// Definición del componente Vue
export default {
    // Método data que retorna el estado inicial del componente
    data() {
        return {
            currentValue: "", // Estado para almacenar el valor actual del input
            tags: [], // Estado para almacenar las etiquetas ingresadas
        };
    },

    methods: {
        // Método para manejar el evento keydown en el input
        handleKeyDown(e) {
        // Verifica si se presionó la tecla Backspace y el valor actual está vacío
        if (e.key === 'Backspace' && this.currentValue === "") { 
            // Elimina la última etiqueta del array 'tags' si el input está vacío
            this.tags.pop();
        }        
    },

    // Método para manejar el envío del formulario (submit)
    handleSubmit() {
        if (this.currentValue !== "") {
            const exist = this.tags.some(item => item === this.currentValue);
            if (!exist) {
                // La etiqueta no existe, agregarla al array 'tags'
                this.tags.push(this.currentValue);
                // Reiniciar el valor actual a una cadena vacía después de agregar la etiqueta
                this.currentValue = "";
            } else {
                // La etiqueta ya existe, mostrar un mensaje de alerta
                alert('La etiqueta ya existe en la lista.');
            }
        }
    },

    // Método para eliminar una etiqueta específica
    deleteTag(tag) {
        // Filtra el array 'tags' para eliminar la etiqueta seleccionada
        this.tags = this.tags.filter(item => item !== tag);
    }
}

}
</script>

<template>
    <!-- Template del componente -->
    <div class="InputTag">
        <div class="tags">
            <!-- Iteración sobre las etiquetas para mostrarlas -->
            <div class="tag" v-for="(tag, index) in tags" :key="index">
                {{ tag }}   <button @click="deleteTag(tag)">
                                Delete Tag
                            </button>
            </div>
        </div>
        <form @submit.prevent="handleSubmit">
            <input class="input"
                type="text" 
                v-model="currentValue" 
                @keydown="handleKeyDown" 
            />
        </form>
    </div>
</template>

<style scoped>
.inputTag {
    display: inline-flex;
    border: solid 1px black;
    min-height: 43px;
}

.tags {
    display: flex;
    gap: 3px;
    padding: 5px;
}

.tags .tag {
    display: flex;
    padding: 5px;
    border: solid 1px #ccc;
    border-radius: 3px;
    gap: 5px;
    align-items: center;
}

.inputTag input {
    border: none;
    outline: none;
    padding: 0 5px;
}

.inputTag button {
    background-color: transparent;
    border: none;
    border-radius: 3px;
}
.inputTag button:hover {
    background-color: #ccc;
}

</style>
