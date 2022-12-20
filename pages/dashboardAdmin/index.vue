<template>
    <div>
        <div class="dashboard-container">
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3 mb-3">
                    <div class="statistical p-4">
                        <div class="d-flex w-100 justify-content-between">
                            <div class="h3">100</div>
                            <font-awesome-icon icon="fa-solid fa-gauge" />
                        </div>
                        <div class="mt-5">
                            Total users
                        </div>
                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3 mb-3">
                    <div class="statistical">
                        Product
                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3 mb-3">
                    <div class="statistical">
                        Tổng đơn hàng
                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3 mb-3">
                    <div class="statistical">
                        Số sp bán được
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    layout: "adminLayout",
}
</script>

<style>
.statistical{
    background-color: red;
    height: 250px;
}
</style>