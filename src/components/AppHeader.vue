<script>

export default {
    name: 'AppHeader',
}

</script>


<template>

    <header>
        <div class="header-container">
            <img src="src/assets/img/logo.jpg" alt="Logo" class="logo">
            <h1>Yu-Gi-Oh Api</h1>
        </div>
    </header>

</template>


<style lang="scss" scoped>

.header-container{
    display: flex;
    align-items: center;
    height: 100px;
    padding-left: 20px;

    .logo{
    height: 20px;
    width: auto;
    padding-right: 15px;
    }

    h1{
    font-weight: lighter;
    }
}

</style>