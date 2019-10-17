<template>
    <header>
        <h1><router-link to="/">{{ title }}</router-link></h1>
    </header>
</template>

<script>
    export default {
        name: 'Header',
        props: {
            title: String
        },
        data() {
            return {
                show: false,
                name: "Jeff"
            };
        },
    };
</script>

<style lang="scss" scoped>
    header {
        background-color: #111;
        padding: 20px;
        color: white;
    }

    h1 {
        margin: 0;
    }
    a, a:visited {
    color: inherit;
    text-decoration: none;
}
 a:hover{
    color: red;
}

</style>