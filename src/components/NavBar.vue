
<script setup lang="ts">

</script>
<template>
    <nav>
        <span>Tutorial</span>

        <ul>
            <li><a href="#">Home</a></li>
            <li><a href="#">Ajuda</a></li>
            <li><a href="#">Veja mais</a></li>
        </ul>
    </nav>
</template>

<style scoped>
nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    align-items: center;
}
span {
    font-size: 26px;
}
ul {
    display: flex;
    gap: 25px;
    list-style: none;
}
a{
    text-decoration: none;
    color: black;
}
</style>