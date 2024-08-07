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
    birth: number,
    avatar: string,
    email: string
}

interface IPersonRequestData {
    id: number,
    first_name: string,
    last_name: string,
    avatar: string,
    email: string
}

// const name = ref('Eric Motta');
// const birth = ref(2000);

// const calcAge = function () : void {
//     age.value = 2024 - birth.value;
// }


const person:IPerson = reactive({
    name: '',
    birth: 2000,
    avatar: '',
    email: ''
});

const age = computed(() => {
    return 2024 - person.birth;
});

const fetchPerson = async function () {
    const request = await fetch(`https://reqres.in/api/users/${1}`); 
    const personData:IPersonRequestData = (await request.json()).data;

    person.name = personData.first_name + personData.last_name;
    person.avatar = personData.avatar;
    person.email = personData.email;
}

onBeforeMount(() => {
    console.log('componente criado');
});

onMounted(() => {
    console.log('componente montado');
    fetchPerson();
    person.name = 'Eric Motta';
    person.birth = 2005;
    person.avatar = 'https://img.freepik.com/fotos-gratis/reflexo-das-luzes-e-da-montanha-em-um-lago-capturado-em-parco-ciani-lugano-suica_181624-24209.jpg?t=st=1722993613~exp=1722997213~hmac=22e37a40f9c0f18aff76d9b96bacaf241817cd9103639c5d6b843f2594b78bda&w=1380';
    person.email = 'eric@greenn.com.br';
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

// birth.value = 2005;

</script>

<template>
    <div>

        <div class="profile">
            <img class="avatar" :src="person.avatar" alt="avatar">
            <h1>{{ person.name }}</h1>
            <h2>{{ person.email }}</h2>
        </div>
        <!-- <h1>{{ person.name }} tem {{ age }} anos</h1>


        <div>
            <div>
                <label for="name">Digite seu nome</label>
                <input type="text" id="name" v-model="person.name">
            </div>

            <div>
                <label for="name">Digite o ano do seu nascimento</label>
                <input type="number" id="name" v-model="person.birth">
            </div>
        </div> -->
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
.profile {
    display: grid;
    gap: 10px;
    width: fit-content;
    padding: 20px 60px;
    justify-items: center;
}
.avatar {
    width: 200px;
    height: 200px;
    border-radius: 15px;
}
</style>