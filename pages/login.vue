<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-8">
                <form @submit.prevent="login">
                    <div class="mb-3">
                        <label for="email" class="form-label">Email address</label>
                        <input
                            type="email"
                            class="form-control"
                            id="email"
                            v-model="loginData.email"
                            aria-describedby="emailHelp"
                        />
                    </div>
                    <div class="mb-3">
                        <label for="password" class="form-label">Password</label>
                        <input
                            type="password"
                            v-model="loginData.password"
                            class="form-control"
                            id="password"
                        />
                    </div>
                    <button type="submit" class="btn btn-primary w-100">login</button>
                </form>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            loginData: {
                email: "",
                password: ""
            }
        };
    },
    methods: {
        async login() {
            try {
                let response = await this.$auth.loginWith("laravelJWT", {
                    data: this.loginData
                });
                this.$router.push("/profile");
            } catch (err) {
                console.log(err);
            }
        }
    }
};
</script>
