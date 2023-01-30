<template>
    <div class="w-100" style="padding: 0 8%;">
        <div class="title-product-category text-uppercase font-weight-bold">
            {{ productType }}
        </div>
        <div class="row">
            <div class="col-md-6 col-lg-4 col-xl-3" v-for="(product, index) in productList">
                <div class="card-item">
                    <NuxtLink class="txt-details" :to="{ name: 'productDetails', query: { 'productId': product.id } }">
                        <img class="img-1" v-bind:src="'https://localhost:7029' + product.image" alt="">
                        <div class="img-content-category">
                            {{ product.name }}
                        </div>
                    </NuxtLink>
                    <div class="status-product ">
                        Liên hệ
                    </div>
                    <div class="prize-product">
                        {{ product.price }}
                        <div class="icon-cast-product">
                            <font-awesome-icon icon="fa-solid fa-cart-shopping" />
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
        this.productType = this.$route.query.productType
        this.init()
    },
    data() {
        return {
            productList: [],
            productType: '',
        }
    },
    methods: {
        async init() {
            var response = await fetch('https://localhost:7029/api/Product/GetProductListByCategory?productType=' + this.productType)
                .then(res => {
                    return res.json()
                })
            this.productList = response
        }
    },
    watch: {
        $route(to, from) {
            this.init()
            window.scrollTo(0, 0)
        }
    }
};
</script>
<style scoped>
.title-product-category {
    font-size: 25px;
    color: #0f5b9a;
}

.img-content-category{
    width: 100%;
    font-size: 13px;
    padding: 0 3%;
    color: black;
    height: 80px;
}

.prize-product{
    font-size: 20px;
    font-weight: bold;
    
}

.status-product{
    font-size: 15px;
    margin-top: 4px
}
</style>