<template>
    <div class="user-login-container">
        <div class="row">
            <div class="col-md-12 col-lg-12 col-xl-8">
                <form v-on:submit.prevent="userRegister()">
                    <div class="control-login">
                        <div class="text-control-login">
                            Thông tin khách hàng đăng nhập hệ thống
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Email đăng ký:
                            </div>
                            <input type="email" class="form-control"
                                placeholder="Email" v-model="email" required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Tên:
                            </div>
                            <input type="text" class="form-control" placeholder="Tên" v-model="name" required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Số điện thoại:
                            </div>
                            <input pattern="[0]{1}[3-9]{1}[0-9]{8}" class="form-control" placeholder="Số điện thoại"
                                v-model="phonenumber" required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Mật khẩu:
                            </div>
                            <input type="password" class="form-control" placeholder="Mật khẩu" v-model="password"
                                required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Xác nhận mật khẩu:
                            </div>
                            <input type="password" class="form-control" placeholder="Nhập lại mật khẩu"
                                v-model="confirmPassword" required />
                        </div>
                        <div class="btn-login-container control-item">
                            <button class="btn-login" type="submit">
                                Đăng Ký
                            </button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    befroeMount() {

    },
    data() {
        return {
            email: '',
            name: '',
            phonenumber: '',
            password: '',
            confirmPassword: ''
        };
    },

    methods: {
        async userRegister() {
            if (this.password != this.confirmPassword) {
                alert("k giong")
                return
            }
            var userRegisterRequest = {
                email: this.email,
                name: this.name,
                phonenumber: this.phonenumber,
                password: this.password,
                confirmPassword: this.confirmPassword
            }
            var repsonseRegister = await fetch('https://localhost:7029/api/User/UserRegister',
                {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(userRegisterRequest)
                }
            ).then((res) => res.json())
            if (repsonseRegister.resultRegister == true) {
                alert(repsonseRegister.description)
                localStorage.setItem('user', JSON.stringify(repsonseRegister.userInfor))
                window.location = "/homepage";
            }
            else {
                alert(repsonseRegister.description)
                return
            }
        },

    }
}
</script>
<style>
.user-register-container {
    width: 100%;
    min-height: 50px;
    padding: 0 8%;
}

.control-item-register {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
    padding-left: 10%;
}

.user-login-container {
    width: 100%;
    min-height: 50px;
    padding: 0 8%;
}

.control-login {
    width: 100%;
    padding: 10px 5%;
}

.control-item {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
}

.label-control {
    width: 200px;
}

.content-register {
    width: 100%;
    padding: 10px 5%;
}

.text-control-login {
    font-weight: bold;
    font-size: 20px;
}

.text-control-register {
    font-size: 20px;
    font-weight: bold;
}

.text-control-register1 {
    font-size: 14px;
}

.btn-dang-ky {
    font-size: 14px;
    color: #0f5b9a;
    font-weight: bold;
}

.btn-dang-ky:hover {
    text-decoration: none;
    color: #0c3175;
    cursor: pointer;
}

.btn-login-container {
    justify-content: center;
    margin-top: 15px;
}
</style> 