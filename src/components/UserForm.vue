<template>
    <Form
        @submit="submitUser"
        :validation-schema="userFormSchema"
    >
        <div class="form-group">
            <label for="name"><b><i class="fa-solid fa-user"></i> Tên</b></label>
            <Field
                name="name"
                type="text"
                class="form-control"
                v-model="userLocal.name"
            />
            <ErrorMessage name="name" class="error-feedback" />
        </div>
        <div class="form-group">
            <label for="email"><b><i class="fa-solid fa-envelope"></i> E-mail</b></label>
            <Field
                name="email"
                type="email"
                class="form-control"
                v-model="userLocal.email"
            />
            <ErrorMessage name="email" class="error-feedback" />
        </div>
        <div class="form-group">
            <label for="address"><b><i class="fa-regular fa-address-card"></i> Địa chỉ</b></label>
            <Field
                name="address"
                type="text"
                class="form-control"
                v-model="userLocal.address"
            />
            <ErrorMessage name="address" class="error-feedback" />
        </div>
        <div class="form-group">
            <label for="phone"><b><i class="fa-brands fa-google-play"></i> Điện thoại</b></label>
            <Field
                name="phone"
                type="tel"
                class="form-control"
                v-model="userLocal.phone"
            />
            <ErrorMessage name="phone" class="error-feedback" />
        </div>

        <div class="form-group form-check">
            <input
                name="access"
                type="checkbox"
                class="form-check-input"
                v-model="userLocal.access"
            />
            <label for="access" class="form-check-label">
                <strong>Yêu thích</strong>
            </label>
        </div>

        <div class="form-group">
            <button class="btn btn-primary">Lưu</button>
            <button
                v-if="userLocal._id"
                type="button"
                class="ml-2 btn btn-danger"
                @click="deleteUser"
            >
                Xóa
            </button>
        </div>
    </Form>
</template>

<script>
import * as yup from "yup";
import { Form, Field, ErrorMessage } from "vee-validate";

export default {
    components: {
    Form,
    Field,
    ErrorMessage,
    },
    emits: ["submit:user", "delete:user"],
    props: {
        user: { type: Object, required: true }
    },
    data() {
        const userFormSchema = yup.object().shape({
            name: yup
                .string()
                .required("Tên phải có giá trị.")
                .min(2, "Tên phải ít nhất 2 ký tự.")
                .max(50, "Tên có nhiều nhất 50 ký tự."),
            email: yup
                .string()
                .email("E-mail không đúng.")
                .max(50, "E-mail tối đa 50 ký tự."),
            address: yup.string().max(100, "Địa chỉ tối đa 100 ký tự."),
            phone: yup
                .string()
                .matches(
                    /((09|03|07|08|05)+([0-9]{8})\b)/g,
                    "Số điện thoại không hợp lệ."
                ),
        });
        return {
            // Chúng ta sẽ không muốn hiệu chỉnh props, nên tạo biến cục bộ
            // userLocal để liên kết với các input trên form
            userLocal: this.user,
            userFormSchema,
        };
    },
    methods: {
        submitUser() {
            this.$emit("submit:user", this.userLocal);
        },
        deleteUser() {
            this.$emit("delete:user", this.userLocal.id);
        },
    },
};
</script>

<style scoped>
@import "@/assets/form.css";
</style>