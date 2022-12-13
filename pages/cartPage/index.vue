<template>
    <div class="cart-container-details">
        <div class="test-3">
            Thông tin giỏ hàng
        </div>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">
                        <div class="info-cart">
                            Sản phẩm
                        </div>
                    </th>
                    <th scope="col"></th>
                    <th scope="col">
                        <div class="info-cart-general">
                            Đơn giá
                        </div>
                    </th>
                    <th scope="col">Số lượng</th>
                    <th scope="col">Số tiền</th>
                    <th scope="col">Thao tác</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(cartDetail, index) in cartDetailList">
                    <td>
                        <div class="cart-detail-name">{{ cartDetail.name }}</div>
                    </td>
                    <td>
                        <img class="img-cart-detail" v-bind:src="'https://localhost:7029'+cartDetail.image" alt="">
                    </td>
                    <td>
                        <div class="cart-detail-general">{{ cartDetail.price }}</div>
                    </td>
                    <td>
                        <div class="cart-detail-general">{{ cartDetail.quantity }}</div>
                    </td>
                    <td>
                        <div class="cart-detail-general">{{ cartDetail.quantity }}</div>
                    </td>
                    <td>
                        <div class="cart-detail-general">{{ cartDetail.price }}</div>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

export default {
    async beforeMount() {
        this.getCartDetailList()
    },
    data() {
        return {
            cartDetailList: [],
        };
    },

    methods: {
        async getCartDetailList() {
            var user = JSON.parse(localStorage.getItem('user'))
            console.log(user.id)
            var response = await fetch('https://localhost:7029/api/ProductHandle/GetCartDetailList?userID=' + user.id)
                .then(res => {
                    return res.json()
                })
            this.cartDetailList = response
            console.log(JSON.stringify(this.cartDetailList))
        }
    },

};
</script>

<style>
.cart-container-details {
    width: 100%;
    height: 500px;
    padding: 0 8%;
}

.test-3 {
    background-color: yellow;
}

.cart-detail-name {
    width: 400px;
    height: 70px;
    overflow: hidden;
    text-overflow: ellipsis;
}

.info-cart {}

.cart-detail-general {
    width: 10%;
}

.img-cart-detail{
    height: 70px;
}
</style>