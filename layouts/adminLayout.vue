<template>
    <div>
        <div id="header-admin"
            class="bg-dark w-100 border-bottom border-secondary d-flex justify-content-between align-items-center px-5"
            style="height: 60px;">
            <div class="logo-admin-container">
                <img class="logo-admin" src="../assets/img/logo.png" alt="">
            </div>
            <div class="icon-home-page-admin">
                <font-awesome-icon icon="fa-solid fa-house" />
            </div>
            <div class="text-light d-flex align-items-center">
                Hello, {{ adminName }}
                <div class="ml-1">
                    <font-awesome-icon icon="fa-sharp fa-solid fa-caret-down" />
                </div>
                <div class="rounded-circle bg-light ml-3" style="height: 40px; width: 40px;">
                </div>
            </div>
        </div>
        <div id="body-admin" class="d-flex w-100 " style="min-height: 100vh;">
            <div class="bg-dark vh-100 d-sm-none d-xl-block d-lg-block d-md-none" style="width: 15%;">
                <NuxtLink class="menu-item-admin" :to="{ name: 'dashboardAdmin' }">
                    <div class="">
                        <font-awesome-icon icon="fa-solid fa-gauge" />
                    </div>
                    <div class="p-2">
                        Bảng tin
                    </div>
                </NuxtLink>
                <NuxtLink class="menu-item-admin" :to="{ name: 'adminProduct' }">
                    <div class="">
                        <font-awesome-icon icon="fa-solid fa-cube" />
                    </div>
                    <div class="p-2">
                        Sản phẩm
                    </div>
                </NuxtLink>
                <NuxtLink class="menu-item-admin" :to="{ name: 'adminUserManagement' }">
                    <div class=" ">
                        <font-awesome-icon icon="fa-solid fa-users" />
                    </div>
                    <div class="p-2">
                        User
                    </div>
                </NuxtLink>
                <NuxtLink class="menu-item-admin" :to="{ name: 'adminOrderManagement' }">
                    <div class="">
                        <font-awesome-icon icon="fa-solid fa-box" />
                    </div>
                    <div class="p-2">
                        Đơn Hàng
                    </div>
                </NuxtLink>
            </div>
            <div id="main-admin" class="vh-100 p-4" style="width: 85%; background-color: #f2f2f2;">
                <Nuxt />
            </div>
        </div>
        <div class="footer-container-1 px-xl-5 row mb-3">
                <div class="col-xl-6 col-md-6 col-sm-12 row">
                    <div class="footer-container-1-item col-6">
                        <font-awesome-icon icon="fa-solid fa-truck-fast" />
                        <div class="footer-content">
                            <div class="footer-container-1-content-1">
                                CHÍNH SÁCH GIAO HÀNG
                            </div>
                            <div class="footer-container-1-content-2">
                                Nhận hàng và thanh toán tại nhà
                            </div>
                        </div>
                    </div>
                    <div class="footer-container-1-item col-6">
                        <font-awesome-icon icon="fa-solid fa-rotate" />
                        <div class="footer-content">
                            <div class="footer-container-1-content-1">
                                ĐỔI TRẢ DỄ DÀNG
                            </div>
                            <div class="footer-container-1-content-2">
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-xl-6 col-md-6 col-sm-12 row">
                    <div class="footer-container-1-item col-6">
                        <font-awesome-icon icon="fa-regular fa-credit-card" />
                        <div class="footer-content">
                            <div class="footer-container-1-content-1">
                                THANH TOÁN TIỆN LỢI
                            </div>
                            <div class="footer-container-1-content-2">
                                Trả tiền mặt, CK, trả góp 0%
                            </div>
                        </div>
                    </div>
                    <div class="footer-container-1-item col-6">
                        <font-awesome-icon icon="fa-solid fa-comments" />
                        <div class="footer-content">
                            <div class="footer-container-1-content-1">
                                HỖ TRỢ NHIỆT TÌNH
                            </div>
                            <div class="footer-container-1-content-2">
                                Tư vấn, giải đáp mọi thắc mắc
                            </div>
                        </div>
                    </div>
                </div>
            </div>
    </div>
    
</template>

<script>
export default {
    async beforeMount() {
        var admin = JSON.parse(localStorage.getItem('admin'))
        if (admin) {
            this.adminName = admin.name;
        }
        else {
            this.$router.push("/adminLogin")
        }
    },
    data() {
        return {
            adminName: ''
        }
    },
}
</script>

<style>
.logo-admin:hover {
    cursor: pointer;
}

.menu-item-admin {
    width: 100%;
    height: 44px;
    display: flex;
    align-items: center;
    color: white;
    padding-left: 30px;
    font-size: 17px;
    cursor: pointer;
}

.menu-item-admin:hover {
    background-color: #1d2124;
    color: white;
    text-decoration: none;
}

.logo-admin {
    width: 80px;
    height: 80px;
}

.icon-home-page-admin {
    color: white;
    padding-right: 65%;
    font-size: 20px;
}

.icon-home-page-admin:hover {
    cursor: pointer;
}

.btn-admin-general {
    color: white;
}

.btn-admin-general:hover {
    text-decoration: none;
    color: white;
}
</style>