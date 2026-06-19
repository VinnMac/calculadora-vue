<script setup lang="ts">
    const props = defineProps<{
        numero1: number 
        numero2: number 
        operacao: string
        resultadoDaOperacao: number
    }>();

    const emit = defineEmits<{
        atualizaNumero1: [number] 
        atualizaNumero2: [number]
        atualizaOperacao: [string]
        }>();
</script>

<template>
    <div class="calc">
        <form>
            <input @input="evento => emit('atualizaNumero1', Number((evento.target as HTMLInputElement).value))" :value="props.numero1" type="number">
            <select @change="evento => emit('atualizaOperacao', (evento.target as HTMLSelectElement).value)" :value="props.operacao">
                <option value="adicao">+</option>
                <option value="subtracao">-</option>
                <option value="multiplicacao">*</option>
                <option value="divisao">/</option>
            </select>
            <input @input="evento => emit('atualizaNumero2', Number((evento.target as HTMLInputElement).value))" :value="props.numero2" type="number">
        </form>
        <p class="igual">=</p>
        <h2 class="resultadoDaOperacao">{{ props.resultadoDaOperacao }}</h2>
    </div>
</template>

<style scoped>
.calc {
    display: flex;
    align-items: center;
    }

input {
margin: .3rem;
max-width: 5rem;
}

.igual {
padding: 0 1rem;
}

.resultadoDaOperacao {
    font-size: 2.5rem;
    color: #e2e9f0;
}
</style>