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

    // Métodos del componente
    methods: {
        // Método para manejar el evento keydown en el input
        handleKeyDown(e) {
            if (e.key === 'Enter') { // Verifica si se presionó la tecla Enter
                console.log('Enter'); // Muestra un mensaje en la consola
            }
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
                {{ tag }}
            </div>
        </div>
        <!-- Input controlado por v-model para actualizar 'currentValue' -->
        <input type="text" v-model="currentValue" @keydown="handleKeyDown" />
    </div>
</template>

<style scoped>
/* Estilos CSS específicos para este componente */
</style>
