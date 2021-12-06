<template>
    <div class=" row justify-content-center">
        <ul>
            <li>
                <NuxtLink to="/">Index</NuxtLink>
            </li>
            <li v-if="!isAuthenticated">
                <NuxtLink to="/login">Login</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/profile">Profile</NuxtLink>
            </li>
            <li v-if="isAuthenticated" >
                <span style="cursor: pointer" @click="logout()">Logout</span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "TheHeader",
    methods: {
        async logout() {
            await this.$auth.logout();
        }
    },
    computed: {
        isAuthenticated() {
            return this.$store.state.auth.loggedIn;
        }
    }
}
</script>

<style scoped>

ul {
    display: contents;
    list-style: none;
    padding: 0;
}

ul li {
    padding: 10px;
}

</style>
