<template>
    <Form>
        <div class="form-group">
            <label for="email"><b><i class="fa-solid fa-envelope"></i> Email</b></label>
            <input type="email" name="email" value="thuyb1910151@gmail.com" class="form-control">
            <ErrorMessage name="email" class="error-feedback" />
        </div>
        <div class="form-group">
            <label for="password"><b><i class="fa-solid fa-plus"></i> Password</b></label>
            <input type="password" name="password" value="12345" class="form-control">
            <ErrorMessage name="password" class="error-feedback" />
        </div>
        

        <div class="form-group">
            <router-link :to="{ name: 'userbook' }" class="nav-link">
                <button class="t-btn btn btn-info ">Đăng Nhập</button>
            </router-link>
        </div>
    </Form>
</template>



<style scoped>
@import "@/assets/form.css";
</style>