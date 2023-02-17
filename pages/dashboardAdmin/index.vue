<template>
    <div>
        <div class="dashboard-container">
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3 mb-3">
                    <div class="statistical text-light rounded p-4 w-100 bg-primary">
                        <div class="d-flex w-100 justify-content-between">
                            <div class="h2">
                                {{ totalUser }}
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
                                {{ totalProduct }}
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
                                {{ totalOrder }}
                            </div>
                            <div class="h2">
                                <font-awesome-icon icon="fa-solid fa-receipt" />
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
                                {{totalProductSold}}
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

        <div class="w-100 mt-5">
            <ChartLine :chartData="numberOrder" class="chart-line" />
        </div>
    </div>
</template>
<script>
import ChartLine from './ChartLine.vue'
export default {
    components: { ChartLine },
    layout: "adminLayout",
    async beforeMount() {
        this.getProductList()
    },
    data() {
        return {
            totalUser: 0,
            totalOrder: 0,
            totalProduct: 0,
            totalProductSold: 0,
            numberOrder: [10, 5, 8, 9, 2, 15, 13]
        };
    },
    methods: {
        async getProductList() {

            var response = await fetch('https://localhost:7029/api/Static/Dashboard')
                .then(res => {
                    return res.json()
                })
            this.totalUser = response.totalUser
            this.totalOrder = response.totalOrder
            this.totalProduct = response.totalProduct
            this.totalProductSold= response.totalProductSold
            this.numberOrder= response.numberOrderDetail
            console.log(JSON.stringify(response))
        },
    }
}
</script>
<style>
.statistical {
    height: 150px;
}
</style>