<template>
    <div>
        <div id="home-page-contact">
            <div class="row w-100">
                <div class=" home-page-contact-container col-9 col-md-9 col-lg-9 col-xl-9 d-flex">
                    <div class="">
                        <div class="contact-container contact-child d-flex">
                            <a class="contact-details d-flex align-items-center" href="#he-thong">
                                <font-awesome-icon icon="fa-solid fa-location-dot" />
                                <div class="d-none d-md-none d-lg-block ml-1">
                                    Hệ thống showroom
                                </div>
                            </a>

                            <!-- <div class="">
                                <div id="xmas-popup" class="popup" href="#">
                                    <div class="popup-content">
                                        fwefweffffew
                                        fewjfhuewifh
                                        fwefh
                                        <a href="#" class="close">x</a>
                                    </div>
                                </div>
                                <div class="contact-details">
                                    <a href="#xmas-popup" class="contact-details-button d-flex align-items-center">
                                        <font-awesome-icon icon="fa-solid fa-headset" />
                                        <div class="d-none d-md-none d-lg-block ml-1">
                                            Khách Cá Nhân
                                        </div>
                                    </a>
                                </div>
                            </div> -->

                            <a href="#xmas-popup" class="contact-details d-flex align-items-center">
                                <font-awesome-icon icon="fa-solid fa-headset" />
                                <div class="d-none d-md-none d-lg-block ml-1">
                                    Khách Cá Nhân
                                </div>
                            </a>


                            <a class="contact-details d-flex align-items-center">
                                <font-awesome-icon icon="fa-solid fa-headset" />
                                <div class="d-none d-md-none d-lg-block ml-1">
                                    Khách Doanh Nghiệp
                                </div>
                            </a>
                            <a class="contact-details d-flex align-items-center">
                                <font-awesome-icon icon="fa-solid fa-newspaper" />
                                <div class="d-none d-md-none d-lg-block ml-1">
                                    Tin Công Nghệ
                                </div>
                            </a>
                            <a class="contact-details d-flex align-items-center">
                                <font-awesome-icon icon="fa-solid fa-bullhorn" />
                                <div class="d-none d-md-none d-lg-block ml-1">
                                    Tuyển Dụng
                                </div>
                            </a>
                        </div>
                    </div>
                </div>
                <div class="authen-container col-3 col-md-3 col-lg-3 col-xl-3 d-flex justify-content-end">
                    <div v-if=isLogin class="contact-child d-flex align-items-center">
                        <div class="authen-icon">
                            <font-awesome-icon icon="fa-solid fa-user" />
                        </div>
                        <div class="btn-dang-nhap" @click="logout()">Đăng Xuất</div>
                    </div>
                    <div v-else class="contact-child d-flex align-items-center">
                        <div class="authen-icon ">
                            <font-awesome-icon icon="fa-solid fa-user" />
                        </div>
                        <NuxtLink class="btn-dang-nhap" :to="{ name: 'userLoginPage' }">Đăng Nhập</NuxtLink>/
                        <NuxtLink class="btn-dang-nhap" :to="{ name: 'userRegisterPage' }">Đăng Ký</NuxtLink>
                    </div>
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
                            placeholder="Nhập tên sản phẩm, từ khoá cần tìm kiếm ..." v-model="keySearch">
                        <NuxtLink class="button-search"
                            :to="{ name: 'resultSearch', query: { 'keySearch': keySearch } }">
                            <font-awesome-icon icon="fa-solid fa-magnifying-glass" />
                        </NuxtLink>
                    </div>
                </div>
                <div class="homepage-header-more">
                    <div class="Build-PC-container cart-container">
                        <div class="icon-cart-container">
                            <font-awesome-icon icon="fa-solid fa-computer" />
                        </div>
                        <div class="Build-PC-content cart-content">
                            <NuxtLink class="btn-cart-content" :to="{ name: 'buildPcPage' }">Xây dựng cấu hình
                            </NuxtLink>
                        </div>
                    </div>
                    <div @click="cartOnClick()" class="cart-container">
                        <div class="icon-cart-container">
                            <div class="icon-cart-container">
                                <font-awesome-icon icon="fa-solid fa-cart-shopping" />
                            </div>
                            <div v-if="isLogin" class="num-cart">{{ numberCartDetail }}</div>
                        </div>
                        <div class="btn-cart-content">Giỏ hàng</div>
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
    async beforeMount() {
        this.checkLogin()
    },
    data() {
        return {
            isLogin: false,
            keySearch: '',
            cartDetailList: [],
            numberCartDetail: 0
        };
    },

    methods: {
        async checkLogin() {
            var user = JSON.parse(localStorage.getItem('user'))
            if (user) {
                var response = await fetch('https://localhost:7029/api/ProductHandle/GetCartDetailList?userID=' + user.id)
                    .then(res => {
                        return res.json()
                    })
                this.numberCartDetail = response.length
                this.isLogin = true
            }
            else {
                this.isLogin = false
            }
        },
        logout() {
            localStorage.clear()
            location.reload()
        },

        cartOnClick() {
            var user = JSON.parse(localStorage.getItem('user'))
            if (user) {
                alert('Oke')
                this.$router.push("/cartPage")
            }
            else {
                alert('BẠN CẦN ĐĂNG NHẬP!')
                return
            }
        }
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
    background: #0f5b9a;
}


.home-page-contact-container {
    height: 80px;
    width: 100%;
    padding: 0 0 0 8%;
    align-items: center;

}

/* .contact-child {
    height: 100%;
    display: flex;
    align-items: center;
} */

/* .contact-container {
    width: 80%;
    justify-content: left;
} */

.authen-container {
    color: white;
    font-size: 16px;
    align-items: center;
    padding-right: 8%;
}

@media screen and (max-width: 500px) {
    .authen-container {
        padding: 0;
    }
}

.contact-details {
    background: #0C3175;
    margin-right: 10px;
    color: white;
    font-size: 15px;
    padding: 8px 15px;
    border-radius: 15px;
    border: #0C3175;
    height: 40px;
}

.contact-details:hover {
    text-decoration: none;
    cursor: pointer;
    color: white;
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

.btn-dang-nhap {
    color: white;
}

.btn-dang-nhap:hover {
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

.icon-cart-container:hover {
    cursor: pointer;
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

.btn-cart-content:hover {
    color: black;
    text-decoration: none;
    cursor: pointer;
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

.wrapper {
    max-width: 960px;
    margin: 10% auto;
    text-align: center;
    line-height: 2em;
}

.contact-details-button:hover {
    text-decoration: none;
    color: white;
}


.popup {
    position: fixed;
    width: 300px;
    height: 300px;
    background: rgba(0, 0, 0, 0.6);
    display: none;
    z-index: 5;
}

#xmas-popup .popup-content {
    width: 600px;
    height: 800px;
    background: #bbb;
    margin: 100px auto;
    position: relative;
    border: 5px solid #fff;
}

.close {
    position: absolute;
    top: 5px;
    right: 5px;
    border-radius: 50%;
    background: #222;
    border: 3px solid #fff;
    color: #fff;
    text-decoration: none;
    line-height: 0;
    padding: 9px 0 11px;
    width: 20px;
    text-align: center;
}

.popup:target {
    display: block;
}

.Build-PC-content {
    margin-top: 4px;
}
</style>
