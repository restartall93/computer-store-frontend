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
                Hello, Admin
                <div class="ml-1">
                    <font-awesome-icon icon="fa-sharp fa-solid fa-caret-down" />
                </div>
                <div class="rounded-circle bg-light ml-3" style="height: 40px; width: 40px;">
                </div>
            </div>
        </div>
        <div id="body-admin" class="d-flex w-100 " style="">
            <div class="vh-100 bg-dark" style="width: 15%;">
                <a class="menu-item-admin" href="#">
                    <div class="">
                        <font-awesome-icon icon="fa-solid fa-gauge" />
                    </div>
                    <div class="p-2">
                        Bảng tin
                    </div>
                </a>
                <a class="menu-item-admin" href="#">
                    <div class="">
                        <font-awesome-icon icon="fa-solid fa-cube" />
                    </div>
                    <div class="p-2">
                        Sản phẩm
                    </div>
                </a>
                <a class="menu-item-admin" href="#">
                    <div>
                        <font-awesome-icon icon="fa-solid fa-users" />
                    </div>
                    <div class="p-2">
                        User
                    </div>
                </a>
                <a class="menu-item-admin" href="#">
                    <div class="">
                        <font-awesome-icon icon="fa-solid fa-box" />
                    </div>
                    <div class="p-2">
                        Đơn hàng
                    </div>
                </a>
            </div>
            <div id="main-admin" class="vh-100 p-4" style="width: 85%; background-color: #f2f2f2;">
                <Nuxt />
            </div>
        </div>
    </div>
</template>

<script>

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
    background-color: #004d7c;
    color: white;
    text-decoration: none;
}

.logo-admin {
    width: 80px;
    height: 80px;
}

.icon-home-page-admin{
    color: white;
    padding-right: 65%;
    font-size: 20px;
}

.icon-home-page-admin:hover {
    cursor: pointer;
}
</style>