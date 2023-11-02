<script setup>
    const props = defineProps(['resultado'])
</script>

<template>
    <div class="col-md-12 text-center pt-5">
        <h3>Resultado:</h3>
        <h3 class="resultado">{{ props.resultado }}</h3>
    </div>
</template>