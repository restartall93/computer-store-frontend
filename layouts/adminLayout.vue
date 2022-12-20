<template>
    <div>
        <div class="header-admin w-100 d-flex justify-content-between px-5 border-bottom border-secondary">
            <div class="logo-header-admin h-100 d-flex align-items-center">
                <img src="../assets/img/logo.png" alt="logo" height="50" />
                <div class="location-header-admin">
                    <font-awesome-icon icon="fa-solid fa-house" />
                </div>
            </div>
            <div class="d-flex justify-content-end align-items-center">
                <div class="mr-3">
                    Xin chào, Admin
                </div>
                <div class="avatar bg-dark rounded-circle" style="height: 30px; width: 30px;">
                </div>

            </div>
        </div>

        <div class="body-admin w-100 d-flex">
            <div class="menu-admin-container vh-100 bg-dark" style="width: 15%;">

            </div>
            <div class="Main">
                <Nuxt />
            </div>
        </div>

        <div class="footer-admin">

        </div>
    </div>


</template>

<script>

</script>

<style>
.header-admin {
    height: 50px;
    background-color: #f1f0e5;
}

.logo-header-admin {}
</style>