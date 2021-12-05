<template>
    <h1>{{data.name}}</h1>
</template>
<script>
    export default {
        name: "Profile",

        data() {
            return {
                data: {},
                user:this.$route.params.id
            }
        },
        created() {
            fetch("https://jsonplaceholder.typicode.com/users/"+this.user)
                .then((res) => {
                    return res.json();
                })
                .then((data) => {
                    this.data = data;
                })
        }
    }
</script>
<style>

</style>