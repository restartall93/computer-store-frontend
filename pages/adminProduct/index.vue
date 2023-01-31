<template>
    <div>
        <div class="w-100 d-flex justify-content-between">
            <div style="display: flex; align-items: center;">
                Total: {{ total }} Products, Page:
                <div v-for="(room, index) in totalPage">
                    <div class="item-page" :id="'page-' + (index)" @click="chooesPage(index)">
                        {{ index + 1 }}
                    </div>
                </div>
            </div>
            <NuxtLink class="add-product d-flex mr-3 text-light p-3 bg-primary "
                :to="{ path: 'adminProduct/CreateEditProduct', query: { 'productId': 0 } }">
                <div class=""><font-awesome-icon icon="fa-solid fa-plus" /> </div>
                <div class="add-product-content ml-2">Thêm SP</div>
            </NuxtLink>
        </div>
        <div class="table-responsive">
            <table class="table table-bordered">
                <thead style="background-color: #0f5b9a; color: white;">
                    <tr>
                        <th scope="col">Mã SP</th>
                        <th scope="col">Tên SP</th>
                        <th scope="col">Loại SP</th>
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
                            <div class="admin-product-price">{{ product.price.toLocaleString('vi-VN', { style: 'currency', currency: 'VND',}) }}</div>
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
        this.currentPage = 1
        this.getProductList()
    },
    data() {
        return {
            productList: [],
            total: 0,
            totalPage: 0,
            currentPage: 0,
        };
    },
    methods: {
        async getProductList() {

            var response = await fetch('https://localhost:7029/api/Product/GetProducts?limit=6&page=' + this.currentPage)
                .then(res => {
                    return res.json()
                })
            this.productList = response.productList
            this.total = response.total
            this.totalPage = response.totalPage
            console.log(JSON.stringify(this.productList))
        },

        chooesPage(index) {
            if (this.currentPage != 0) {
                var element = document.getElementById("page-" + (this.currentPage - 1));
                element.classList.remove("page-item-choose");
            }
            var element = document.getElementById("page-" + index);
            element.classList.add("page-item-choose");
            this.currentPage = index + 1
            this.getProductList()
        },
    },
}
</script>

<style scoped>
.admin-product-name{
    
}

.add-product:hover {
    text-decoration: none;
}

.item-page {
    height: 30px;
    width: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 15px;
    border: 1px solid #CCC;
    margin-left: 3px;
    cursor: pointer;
}

.page-item-choose {
    color: #321FDB;
    border: 1px solid #321FDB;
}
</style>