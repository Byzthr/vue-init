<template>
    <header>
        <img alt="Vue logo" src="../assets/logo_tiempo_200.png">
        <div>
            <h1>Tamed Project</h1>
            <h2>{{ desc }}</h2>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        desc: String,
    },
}
</script>

<style>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>