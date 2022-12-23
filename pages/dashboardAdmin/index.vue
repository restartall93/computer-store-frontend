<template>
    <div>
        <div class="dashboard-container">
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3 mb-3">
                    <div class="statistical text-light rounded p-4 w-100 bg-primary">
                        <div class="d-flex w-100 justify-content-between">
                            <div class="h2">
                                100
                            </div>
                            <div class="h2">
                                <font-awesome-icon icon="fa-solid fa-users" />
                            </div>
                        </div>
                        <div class="mt-5 text-uppercase">
                            tổng số người dùng
                        </div>
                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3 mb-3">
                    <div class="statistical text-light rounded p-4 w-100 bg-success">
                        <div class="d-flex w-100 justify-content-between">
                            <div class="h2">
                                1000
                            </div>
                            <div class="h2">
                                <font-awesome-icon icon="fa-solid fa-cubes" />
                            </div>
                        </div>
                        <div class="mt-5 text-uppercase">
                            tổng sản phẩm
                        </div>
                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3 mb-3">
                    <div class="statistical text-light rounded p-4 w-100 bg-danger">
                        <div class="d-flex w-100 justify-content-between">
                            <div class="h2">
                                1000
                            </div>
                            <div class="h2">
                                <font-awesome-icon icon="fa-solid fa-boxes-stacked" />
                            </div>
                        </div>
                        <div class="mt-5 text-uppercase">
                            Tổng đơn hàng
                        </div>
                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3 mb-3">
                    <div class="statistical text-light rounded p-4 w-100 bg-warning">
                        <div class="d-flex w-100 justify-content-between">
                            <div class="h2">
                                1000
                            </div>
                            <div class="h2">
                                <font-awesome-icon icon="fa-solid fa-cubes-stacked" />
                            </div>
                        </div>
                        <div class="mt-5 text-uppercase">
                            số sản phẩm bán được
                        </div>
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
.statistical {
    height: 150px;
}
</style>