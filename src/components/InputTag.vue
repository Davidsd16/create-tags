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
        // Verifica si se presionó la tecla Enter y el valor actual no está vacío
        if (e.key === 'Enter' && this.currentValue !== "") { 
            // Agrega el valor actual (etiqueta) al array 'tags'
            this.tags.push(this.currentValue);
        }
    },

    // Método para manejar el envío del formulario (submit)
    handleSubmit() {
        // Verifica si el valor actual no está vacío
        if (this.currentValue !== "") { 
            // Agrega el valor actual (etiqueta) al array 'tags'
            this.tags.push(this.currentValue);
            // Reinicia el valor actual a una cadena vacía después de agregar la etiqueta
            this.currentValue = "";
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
            <input type="text" v-model="currentValue" />
        </form>
    </div>
</template>

<style scoped>
/* Estilos CSS específicos para este componente */
</style>
