<script setup>
    const props = defineProps(['numero1', 'numero2', 'operacao', 'resultadoDaOperacao']);
</script>

<template>
    <div class="calc">
        <form>
            <input v-model.number="props.numero1" type="number">
            <select v-model="props.operacao">
                <option value="adicao">+</option>
                <option value="subtracao">-</option>
                <option value="multiplicacao">*</option>
                <option value="divisao">/</option>
            </select>
            <input v-model.number="props.numero2" type="number">
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