<template>
    <div>
        Hello dear <b style="color:red">{{ getUserInfo.fullname }}</b> you're in
        profile page
        <hr />
        This is your information:
        <br /><br />
        <table class="table">
            <thead>
            <tr>
                <th scope="col">ID</th>
                <th scope="col">FullName</th>
                <th scope="col">Email</th>
            </tr>
            </thead>
            <tbody>
            <tr v-if="getUserInfo">
                <td>{{ getUserInfo.id }}</td>
                <td>{{ getUserInfo.name }}</td>
                <td>{{ getUserInfo.email }}</td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    middleware: 'auth',
    computed: {
        getUserInfo() {
            return this.$store.getters.getUserInfo;
        }
    }
};
</script>
