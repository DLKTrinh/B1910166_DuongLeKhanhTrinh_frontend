<template>
    <div class="page">
        <h4>Thêm liên hệ</h4>
        <Form
            @submit.prevent="addContact($data)"
        >
            <div class="form-group">
                <label for="name">Tên</label>
                <input
                    required
                    name="name"
                    type="text"
                    class="form-control"
                    v-model="name"
                />
                <ErrorMessage name="name" class="error-feedback" />
            </div>
            <div class="form-group">
                <label for="email">E-mail</label>
                <input
                    required
                    name="email"
                    type="email"
                    class="form-control"
                    v-model="email"
                />
                <ErrorMessage name="email" class="error-feedback" />
            </div>
            <div class="form-group">
                <label for="address">Địa chỉ</label>
                <input
                    name="address"
                    type="text"
                    class="form-control"
                    v-model="address"
                />
                <ErrorMessage name="address" class="error-feedback" />
            </div>
            <div class="form-group">
                <label for="phone">Điện thoại</label>
                <input
                    name="phone"
                    type="tel"
                    class="form-control"
                    v-model="phone"
                />
                <ErrorMessage name="phone" class="error-feedback" />
            </div>
            <div class="form-group form-check">
                <input
                    name="favorite"
                    type="checkbox"
                    class="form-check-input"
                    v-model="favorite"
                />
                <label for="favorite" class="form-check-label">
                    <strong>Liên hệ yêu thích</strong>
                </label>
            </div>
            <div class="form-group submit">
                <button class="btn btn-primary"><font-awesome-icon icon="floppy-disk" /> Lưu</button>
            </div>
        </Form>
    </div>
</template>

<script>
import ContactService from "../services/contact.service";

export default {
    data() {
        return{
            name: '',
            email: '',
            address: '',
            phone: '',
            favorite: false,
        };
    },
    methods: {
        async addContact($data) {
            try {
                await ContactService.create($data);
                this.message = "Liên hệ được tạo.";
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script>

<style scoped>
    label {
        display: block;
        margin-top: 10px;
    }

    .card-container.card {
        max-width: 400px !important;
        padding: 40px 40px;
    }

    .card {
        background-color: #f7f7f7;
        padding: 20px 25px 30px;
        margin: 0 auto 25px;
        margin-top: 50px;
        -moz-border-radius: 2px;
        -webkit-border-radius: 2px;
        border-radius: 2px;
        -moz-box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.3);
        -webkit-box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.3);
        box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.3);
    }

    .profile-img-card {
        width: 96px;
        height: 96px;
        margin: 0 auto 10px;
        display: block;
        -moz-border-radius: 50%;
        -webkit-border-radius: 50%;
        border-radius: 50%;
    }

    .error-feedback {
        color: red;
    }
</style>