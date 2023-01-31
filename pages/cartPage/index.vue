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
                        <img class="img-cart-detail" v-bind:src="'https://localhost:7029' + cartDetail.image" alt="">
                    </td>
                    <td>
                        <div class="cart-detail-general">{{ cartDetail.price.toLocaleString('vi-VN', { style: 'currency', currency: 'VND',}) }}</div>
                    </td>
                    <td>
                        <div class="cart-detail-general">{{ cartDetail.quantity }}</div>
                    </td>
                    <td>
                        <div class="cart-detail-general">{{ (cartDetail.quantity * cartDetail.price).toLocaleString('vi-VN', { style: 'currency', currency: 'VND',}) }}</div>
                    </td>
                    <td>
                        <div class="cart-detail-general">Xoá</div>
                    </td>
                </tr>
            </tbody>
        </table>
        <div class="w-100 bg-dark my-3" style="height: 1px;">
        </div>
        <div class="w-100 my-3 px-5 d-flex justify-content-between">
            <div>
                Tổng tiền:
            </div>
            <div>
                {{ totalPrice.toLocaleString('vi-VN', { style: 'currency', currency: 'VND',})}}
            </div>
        </div>
        <div class="pay">
            <div class="pay-content">Thanh Toán</div>
        </div>
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
            totalPrice: 0,
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
            this.totalPrice = this.cartDetailList.reduce((total, cartDetail) => total + (cartDetail.price) * cartDetail.quantity, 0)
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

.img-cart-detail {
    height: 70px;
}

.pay {
    width: 400px;
    height: 50px;
    margin-left: 700px;
    background-color: #ed1b24;
}

.pay-content {
    font-size: 20px;
    font-weight: bold;
    text-transform: uppercase;
    align-items: center;
    justify-content: center;
    display: flex;
    padding-top: 10px;
    color: white;
}

.pay-content:hover,
.pay:hover {
    cursor: pointer;
}
</style>