<template>
  <div class="home">
    <template v-for="data in data" :key="data">
      <router-link :to="'/user/'+data.id" ><h2>{{data.name}}</h2></router-link>
    </template>

<Profile />
</div>
</template>
<script>
    import Profile from "./Profile.vue"
    export default {

        name: "Home",
        components: {
            Profile
        },
        data() {
            return {
                data: {},
                user:"this.${this.params.id}"
            }

        },
        mounted() {
            fetch("https://jsonplaceholder.typicode.com/users")
                .then((res) => {
                    return res.json()
                })
                .then((data) => this.data = data)

        },
        computed: {
            profileLink() {
                return `/user/${this.data.id}`
            }
        }
    };
</script>