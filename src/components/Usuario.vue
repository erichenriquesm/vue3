<script setup lang="ts">
import {
    onBeforeMount,
    onMounted,
    onBeforeUpdate,
    onUpdated,
    computed,
    onBeforeUnmount,
    onUnmounted,
    reactive,
    ref 
} from 'vue';


interface IPerson {
    name: string,
    birth: number
}

const name = ref('Eric Motta');
const birth = ref(2000);

// const calcAge = function () : void {
//     age.value = 2024 - birth.value;
// }

const age = computed(() => {
    return 2024 - birth.value;
});



onBeforeMount(() => {
    console.log('componente criado');
});

onMounted(() => {
    console.log('componente montado');
});

onBeforeUpdate(() => {
    console.log('componente antes de atualizar');
});

onUpdated(() => {
    console.log('componente ao atualizar');
});

onBeforeUnmount(() => {
    console.log('componente antes de desmontar');
});

onUnmounted(() => {
    console.log('componente após desmontar');
});

// const person:IPerson = reactive({
//     name: '',
//     birth: 2000
// });

// birth.value = 2005;

</script>

<template>
    <div>
        <h1>{{ name }} tem {{ age }} anos</h1>


        <div>
            <div>
                <label for="name">Digite seu nome</label>
                <input type="text" id="name" v-model="name">
            </div>

            <div>
                <label for="name">Digite o ano do seu nascimento</label>
                <input type="number" id="name" v-model="birth">
            </div>
        </div>
    </div>
</template>

<style scoped>
label {
    font-size: 18px;
}
input {
    display: block;
    padding: 3px;
    margin-bottom: 10px;
}
</style>