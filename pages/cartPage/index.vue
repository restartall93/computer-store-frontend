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
                        <div class="cart-detail-general">{{
                            cartDetail.price.toLocaleString('vi-VN', {
                                style:
                                    'currency', currency: 'VND',
                            })
                        }}</div>
                    </td>
                    <td>
                        <div class="cart-detail-general">{{ cartDetail.quantity }}</div>
                    </td>
                    <td>
                        <div class="cart-detail-general">{{ (cartDetail.quantity *
                        cartDetail.price).toLocaleString('vi-VN', { style: 'currency', currency: 'VND', }) }}</div>
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
                {{ totalPrice.toLocaleString('vi-VN', { style: 'currency', currency: 'VND', }) }}
            </div>
        </div>
        <div class="user-login-container">
            <form v-on:submit.prevent="order()">
                <div class="row">
                    <div class="col-md-12 col-lg-6 col-xl-6">

                        <div class="control-login">
                            <div class="text-control-login">
                                Thông tin giao hàng
                            </div>
                            <div class="control-item">
                                <div class="label-control">
                                    Họ và tên:
                                </div>
                                <input type="text" class="form-control" placeholder="Họ và tên" v-model="name" required />
                            </div>
                            <div class="control-item">
                                <div class="label-control">
                                    Địa chỉ:
                                </div>
                                <input type="text" class="form-control" placeholder="Địa chỉ" v-model="address"
                                    required />
                            </div>
                            <div class="control-item">
                                <div class="label-control">
                                    Số điện thoại:
                                </div>
                                <input class="form-control" placeholder="Số điện thoại" v-model="phoneNumber" required />
                            </div>
                        </div>

                    </div>
                    <div class="col-md-12 col-lg-6 col-xl-6">
                        <button type="submit" class="btn btn-danger">Thanh toán</button>
                    </div>
                </div>
            </form>
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
            name: '',
            address: '',
            phoneNumber: ''
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
        },

        async order() {
            var user = JSON.parse(localStorage.getItem('user'))
            if (user) {
                var repsonse = await fetch('https://localhost:7029/api/ProductHandle/OrderProduct?UserId='+user.id+'&address='+this.address+'&name=Ha&phoneNumber='+ this.phoneNumber,
                    {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json'
                        },
                    }
                ).then((res) => res.json())
                if (repsonse == true) {
                    alert('Đặt hàng thành công')
                }
                else {
                    alert('Đặt hàng thành công')
                }
            }
            else {
                alert('Bạn phải login trước khi thanh toán!')
            }
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

.btn-dang-ky {
    font-size: 14px;
    color: #0f5b9a;
    font-weight: bold;
}

.btn-dang-ky:hover {
    text-decoration: none;
    color: #0c3175;
    cursor: pointer;
}

.btn-login-container {
    justify-content: center;
    margin-top: 15px;
}

.btn-login {
    background-color: #4267b2;
    color: white;
    border: white 1px solid;
    width: 111px;
    height: 39px;
    font-weight: bold;
    transform: uppercase;
}
</style>