<template>
    <div>
        <div class="w-100 d-flex justify-content-end">
            <NuxtLink class="mr-3 text-light p-3 bg-primary "
                :to="{ path: 'adminProduct/CreateEditProduct', query: { 'productId': 0 } }">
                <font-awesome-icon icon="fa-solid fa-plus" />
            </NuxtLink>
        </div>
        <div class="table-responsive">
            <table class="table">
                <thead>
                    <tr>
                        <th scope="col">Mã Sản Phẩm</th>
                        <th scope="col">Tên Sản Phẩm</th>
                        <th scope="col">Loại Sản Phẩm</th>
                        <th scope="col">Giá Tiền</th>
                        <th scope="col">Ảnh</th>
                        <th scope="col">Mô tả</th>
                        <th scope="col">Hành động</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(product, index) in productList">
                        <td>
                            <div class="admin-product-id">{{ product.id }}</div>
                        </td>
                        <td>
                            <div class="admin-product-name">{{ product.name }}</div>
                        </td>
                        <td>
                            <div class="admin-producttype">{{ product.producttype }}</div>
                        </td>
                        <td>
                            <div class="admin-product-price">{{ product.price }}</div>
                        </td>
                        <td>
                            <img class="img-product-detail" style="width: 60px"
                                v-bind:src="'https://localhost:7029' + product.image" alt="">
                        </td>
                        <td>
                            <div class="admin-product-content">{{ product.description }}</div>
                        </td>
                        <td>
                            <div class="w-100 d-flex">
                                <NuxtLink class="mr-3 text-primary"
                                    :to="{ path: 'adminProduct/CreateEditProduct', query: { 'productId': product.id } }">
                                    <font-awesome-icon icon="fa-solid fa-pen-to-square" />
                                </NuxtLink>
                                <div class="text-danger">
                                    <font-awesome-icon icon="fa-solid fa-trash-can" />
                                </div>
                            </div>
                        </td>
                    </tr>

                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    layout: "adminLayout",
    async beforeMount() {
        this.getProductList()
    },
    data() {
        return {
            productList: [],
        };
    },
    methods: {
        async getProductList() {

            var response = await fetch('https://localhost:7029/api/Product/GetProducts')
                .then(res => {
                    return res.json()
                })
            this.productList = response
            console.log(JSON.stringify(this.productList))
        }
    },
}
</script>

<style>

</style>