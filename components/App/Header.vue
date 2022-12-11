<template>
    <div>
        <div id="home-page-contact">
            <div class="home-page-contact-container">
                <div class="contact-container contact-child">
                    <div class="contact-details">
                        <font-awesome-icon icon="fa-solid fa-location-dot" />
                        Hệ thống showroom
                    </div>
                    <div class="contact-details">
                        <font-awesome-icon icon="fa-solid fa-headset" />
                        Khách Cá Nhân
                    </div>
                    <div class="contact-details">
                        <font-awesome-icon icon="fa-solid fa-headset" />
                        Khách Doanh Nghiệp
                    </div>
                    <div class="contact-details">
                        <font-awesome-icon icon="fa-solid fa-newspaper" />
                        Tin Công Nghệ
                    </div>
                    <div class="contact-details">
                        <font-awesome-icon icon="fa-solid fa-bullhorn" />
                        Tuyển Dụng
                    </div>
                </div>
                <div class="authen-container contact-child">
                    <div class="authen-icon">
                        <font-awesome-icon icon="fa-solid fa-user" />
                    </div>
                    <NuxtLink class="btn-dang-nhap" :to="{ name: 'userLoginPage'}">Đăng Nhập</NuxtLink>/
                    <NuxtLink class="btn-dang-nhap" :to="{ name: 'userRegisterPage'}">Đăng Ký</NuxtLink>
                </div>
            </div>
        </div>
        <div id="homepage-header">
            <div class="home-page-header-container">
                <NuxtLink class="" :to="{ name: 'homepage' }">
                    <div class="homepage-icon">
                        <img src="../../assets/img/logo.png" alt="logo" height="120">
                    </div>
                </NuxtLink>

                <div class="homepage-header-search">
                    <div class="header-search-container">
                        <input class="input-search" type="text"
                            placeholder="Nhập tên sản phẩm, từ khoá cần tìm kiếm ...">
                        <div class="button-search">
                            <font-awesome-icon icon="fa-solid fa-magnifying-glass" />
                        </div>
                    </div>
                </div>
                <div class="homepage-header-more">
                    <div class="Build-PC-container cart-container">
                        <div class="Build-PC-icon-container icon-cart-container">
                            <font-awesome-icon icon="fa-solid fa-computer" />
                        </div>
                        <div class="Build-PC-content cart-content">
                            Xây dựng cấu hình
                        </div>
                    </div>
                    <div class="cart-container">
                        <div class="icon-cart-container">
                            <font-awesome-icon icon="fa-solid fa-cart-shopping" />
                            <div class="num-cart">23</div>
                        </div>
                        <NuxtLink class="btn-cart-content" :to="{ name: 'cartPage' }">Giỏ hàng</NuxtLink>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    components: {
    },
    data() {
        return {
        };
    },

    methods: {
    },
}
</script>
<style>
* {
    padding: 0;
    margin: 0;
    font-family: 'Mulish', sans-serif;
}

#home-page-contact {
    width: 100%;
    height: 46px;
    background: #0f5b9a;
    display: flex;
    align-items: center;
    justify-content: center;
}

.home-page-contact-container {
    height: 100%;
    width: 80%;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.contact-child {
    height: 100%;
    display: flex;
    align-items: center;
}

.contact-container {
    width: 80%;
    justify-content: left;
}

.authen-container {
    width: 20%;
    justify-content: right;
    color: white;
    font-size: 15px;
}

.contact-details {
    background: #0C3175;
    margin-right: 10px;
    color: white;
    font-size: 15px;
    padding: 8px 15px;
    border-radius: 16px;
}

.authen-icon {
    width: 25px;
    height: 25px;
    background-color: white;
    color: #0f5b9a;
    border-radius: 50%;
    margin-right: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.btn-dang-nhap{
    color: white;
}

.btn-dang-nhap:hover{
    color: #CCC;
    cursor: pointer;
    text-decoration: none;
}

#homepage-header {
    height: 120px;
    width: 100%;
    display: flex;
    justify-content: center;
}

.home-page-header-container {
    height: 100%;
    width: 80%;
    display: flex;
    justify-content: center;
}

.homepage-header-search {
    height: 100%;
    width: calc(100% - 360px);
    display: flex;
    justify-content: center;
    align-items: center;
}

.homepage-header-more {
    height: 100%;
    width: 240px;
    display: flex;
    align-items: center;
    justify-content: right;
}

.header-search-container {
    height: 50px;
    width: 80%;
    padding-left: 10px;
    background-color: white;
    border-radius: 10px;
    display: flex;
    -moz-box-shadow: 0 0 3px #000;
    -webkit-box-shadow: 0 0 3px #000;
    box-shadow: 0 0 3px #000;
}

.input-search {
    height: 100%;
    width: calc(100% - 60px);
    border: none;
    outline: none;
}

.button-search {
    height: 100%;
    width: 60px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #FF9F00;
    border-radius: 0 5px 5px 0;
}

.cart-container {
    width: 80px;
    height: 72px;
}

.icon-cart-container {
    width: 100%;
    height: 38px;
    font-size: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #0f5b9a;
}

.btn-cart-content {
    width: 100%;
    height: 30px;
    margin-top: 4px;
    /* display: flex;
    justify-content: center;
    align-items: center; */
    text-align: center;
    font-weight: bold;
    color: black;
}

.btn-cart-content :hover{
    background-color: black;
    cursor: pointer;
    text-decoration: none;
    
}

.num-cart {
    height: 20px;
    width: 20px;
    font-size: 15px;
    font-weight: bold;
    background-color: #FF9F00;
    border-radius: 50%;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    margin-left: 30px;
    margin-bottom: 30px;
}

.Build-PC-container {
    width: 150px;
}
</style>
  