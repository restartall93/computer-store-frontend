<template>
    <div class="user-login-container">
        <div class="row">
            <div class="col-md-12 col-lg-6 col-xl-6">
                <form v-on:submit.prevent="logIn()">
                    <div class="control-login">
                        <div class="text-control-login">
                            Thông tin khách hàng đăng nhập hệ thống
                        </div>
                        <div class="control-item">
                            <div class="label-control">
                                Email đăng nhập:
                            </div>
                            <input type="text" class="form-control" placeholder="Email" v-model="userName"
                                required />
                        </div>
                        <div class="control-item">
                            <div class="label-control">
                                Mật khẩu:
                            </div>
                            <input type="password" class="form-control" placeholder="Mật khẩu" v-model="passWord"
                                required />
                        </div>
                        <div class="btn-login-container control-item">
                            <button class="btn-login" type="submit">
                                Đăng Nhập
                            </button>
                        </div>
                    </div>
                </form>
            </div>
            <div class="col-md-12 col-lg-6 col-xl-6">
                <div class="content-register">
                    <div class="text-control-register">
                        Bạn chưa là thành viên ?
                    </div>
                    <div class="text-control-register1">
                        Đăng ký là thành viên để hưởng nhiều lợi ích và đặt mua hàng dễ dàng hơn.
                    </div>
                    <NuxtLink class="btn-dang-ky" :to="{ name: 'userRegisterPage' }">Đăng ký tài khoản</NuxtLink>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    beforeMount() {

    },
    data() {
        return {
            userName: '',
            passWord: ''
        };
    },

    methods: {
        async logIn() {
            var userLoginRequest = {
                userName: this.userName,
                passWord: this.passWord
            }

            var repsonseLogin = await fetch('https://localhost:7029/api/User/UserLogin',
                {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(userLoginRequest)
                }
            ).then((res) => res.json())
            if (repsonseLogin.resultLogin == true) {
                alert(repsonseLogin.userInfor)
                localStorage.setItem('user', JSON.stringify(repsonseLogin.userInfor))
                // this.$router.push("/homepage").go()
                window.location="/homepage";
            }
            else{
                alert(repsonseLogin.description)
                return
            }
        }
    },

};
</script>
<style>
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
.btn-dang-ky:hover{
    text-decoration: none;
    color: #0c3175;
    cursor: pointer;
}

.btn-login-container {
    justify-content: center;
    margin-top: 15px;
}
.btn-login{
    background-color: #007bff;
}
</style>