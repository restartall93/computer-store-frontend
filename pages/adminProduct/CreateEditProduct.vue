<template>
    <div class="user-login-container">
        <div class="row">
            <div class="col-md-12 col-lg-12 col-xl-8">
                <form v-on:submit.prevent="submit()">
                    <div class="control-login">
                        <div class="text-control-login">
                            {{ title }}
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Tên sản phẩm
                            </div>
                            <input type="text" class="form-control" placeholder="Tên sản phẩm" v-model="product.name"
                                required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Loại Sản Phẩm
                            </div>
                            <input type="text" class="form-control" placeholder="Loại Sản Phẩm"
                                v-model="product.productType" required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Giá tiền
                            </div>
                            <input class="form-control" placeholder="Giá tiền" v-model="product.price" required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Mô tả
                            </div>
                            <input type="text" class="form-control" placeholder="Mô tả" v-model="product.decription"
                                required />
                        </div>
                        <div class="w-100 d-flex justify-content-center mt-5">
                            <button type="submit" class="btn btn-primary">Primary</button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    layout: "adminLayout",
    async beforeMount() {
        this.productId = this.$route.query.productId
        this.init()
    },
    data() {
        return {
            product: {},
            productId: 0,
            title: ''
        }
    },

    methods: {
        async init() {
            if(this.productId == 0){
                this.title = 'Thêm Mới Sản Phẩm'
            }
            else{
                this.title = 'Sửa Sản Phẩm'
            }
            var response = await fetch('https://localhost:7029/api/Product/GetDetail?id=' + this.productId)
                .then((res) => res.json())
            this.product = response
        }
    },

    watch: {
        $route(to, from) {
            this.init()
            window.scrollTo(0, 0)
        }
    }
}
</script>
<style>
.user-register-container {
    width: 100%;
    min-height: 50px;
    padding: 0 8%;
}

.control-item-register {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
    padding-left: 10%;
}


.user-login-container {
    width: 100%;
    min-height: 50px;
    padding: 0 8%;
}

.control-login {
    width: 100%;
    padding: 10px 5%;
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

.content-register {
    width: 100%;
    padding: 10px 5%;
}

.text-control-login {
    font-weight: bold;
    font-size: 20px;
}

.text-control-register {
    font-size: 20px;
    font-weight: bold;
}

.text-control-register1 {
    font-size: 14px;
}
</style> 