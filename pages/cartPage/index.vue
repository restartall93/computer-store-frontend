<template>
    <div class="cart-container-details">
        <div class="test-3">
            Thông tin giỏ hàng
        </div>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">SP</th>
                    <th scope="col">Gia</th>
                    <th scope="col">SL</th>
                    <th scope="col">Money</th>
                    <th scope="col">Handle</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(cartDetail, index) in cartDetailList">
                    <td>
                        <div>{{ cartDetail.name }}</div>
                    </td>
                    <td>Otto</td>
                    <td>@mdo</td>
                    <td>@mdo</td>
                    <td>@mdo</td>
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
    background-color: red;
    padding: 0 8%;
}

.test-3 {
    background-color: yellow;
}

.test-4 {
    background-color: aqua;
}

.test-5 {
    background-color: black;
}
</style>