<template>
    <div class="page t-edit my-3">
        <h4 class="text-center">Đăng Nhập</h4>
        <LoginForm
        @submit:login="login"
        />
    </div>
</template>

<script>
import LoginForm from "@/components/LoginForm.vue";
//import { parseStringStyle } from "@vue/shared";

export default {
    components: {
        LoginForm,
    },
    // data() {
    //     const FixedUser = {
    //         email: "thuyb1910151@gmail.com",
    //         password: "12345"
    //     }
    // },
    // methods: {
    //     async login(data) {
    //         const user = FixedUser
    //         if (email==user.email && password==user.password){
    //             try{
    //                 this.$router.push({ name: "postbook" });
    //             }  
    //             catch (error) {
    //                 console.log(error);
    //             }
    //         }
    //     },
    // },
}
</script>
