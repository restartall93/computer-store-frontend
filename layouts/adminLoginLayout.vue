<template>
    <div class="admin-login-layout-containers">
        <div class="admin-login-layout-container">
            <div class="admin-login-layout w-100">
                <div class="admin-login-content1 d-flex justify-content-center">Đăng nhập quản trị</div>
                <div class="admin-login-content2 d-flex justify-content-center">Xin chào, vui lòng nhập thông tin đăng nhập</div>
            </div>
            <div class="row">
                <div class="log-in-admin col-md-12 col-lg-6 col-xl-6">
                    <div class="control-item  ">
                        <div class="label-control">
                            Email đăng nhập:
                        </div>
                        <input type="text" class="form-control" placeholder="Email" v-model="userName" required />
                    </div>
                    <div class="control-item ">
                        <div class="label-control">
                            Mật khẩu:
                        </div>
                        <input type="password" class="form-control" placeholder="Mật khẩu" v-model="passWord"
                            required />
                    </div>
                    <div class="btn-admin-login-container control-item">
                        <div class="btn-login" type="submit">
                            Đăng Nhập
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>

</script>

<style>
.admin-login-layout-containers {
    background-color: #e7ecf9;
    width: 100%;
    height: 650px;
    padding: 0 20%;
}

.admin-login-layout-container {
    background-color: #ffffff;
    border-radius: 30px;
    height: 650px;
}

.admin-login-content1 {
    font-weight: bold;
    font-size: 35px;
}

.admin-login-content2{
    color: #a3a3a3;
}

.admin-login-layout {
    padding-top: 20%;

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

.log-in-admin {
    margin-left: 200px;
    margin-top: 30px;
}

.btn-admin-login-container{
    display: flex;
    justify-content: center;
    width: 100%;
    height: 50px;
    background-color: #007be3;
    border-radius: 30px;
}

.btn-login{
    color: white;
    text-transform: upercase;
}
</style>