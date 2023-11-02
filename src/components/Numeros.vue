<script setup>
    const props = defineProps(['estado', 'calc'])
</script>

<template>
    <form>
        <div class="row">
            <div class="col-md-5">
                <input v-model="props.estado.x" @input="props.calc" type="number" placeholder="Número 1" class="form-control">
            </div>
            <div class="col-md-2">
                <select v-model="props.estado.operacao" @change="props.calc" class="form-control">
                    <option value="add">+</option>
                    <option value="subtract">-</option>
                    <option value="multiply">x</option>
                    <option value="divide">/</option>
                </select>
            </div>
            <div class="col-md-5">
                <input v-model="props.estado.y" @input="props.calc" type="number" placeholder="Número 2" class="form-control">
            </div>
        </div>
    </form>
</template>