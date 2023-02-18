<template>
    <div class="header-product-details-container">
        <div class="header-product">
            {{ product.name }}
        </div>
        <div class="product-details">
            <div class="row">
                <div class="col-md-12 col-lg-5 col-xl-5">
                    <div class="img-product">
                        <img class="img-product-details" v-bind:src="'https://localhost:7029' + product.image" alt="">
                    </div>
                </div>
                <div class="col-md-12 col-lg-7 col-xl-7">
                    <div class="product-information">
                        <div class="product-general text-uppercase">
                            Thông số sản phẩm
                        </div>
                        <div v-if="product.cpu != 'none'" class="product-details-content">
                            <li>CPU: {{ product.cpu }}</li>
                        </div>
                        <div v-if="product.ram != 'none'" class="product-details-content">
                            <li>RAM: {{ product.ram }}</li>
                        </div>
                        <div v-if="product.drive != 'none'" class="product-details-content">
                            <li>Ổ cứng: {{ product.drive }}</li>
                        </div>
                        <div v-if="product.vga != 'none'" class="product-details-content">
                            <li>VGA: {{ product.vga }}</li>
                        </div>
                        <div v-if="product.monitor != 'none'" class="product-details-content">
                            <li>Màn hình: {{ product.monitor }}</li>
                        </div>
                        <div v-if="product.details != 'none'" class="product-details-content">
                            <li v-for="(detail, index) in getDetailsList(product.details + ' ')">{{ detail }}</li>
                        </div>

                        <div class="status">
                            <div class="status-content">
                                Tình trạng:
                            </div>
                            <div class="YESorNO">
                                Còn Hàng
                            </div>
                            <div class="status-content-1">
                                Bảo hành:
                            </div>
                            <div class="time-insurance">
                                24 Tháng
                            </div>
                        </div>
                        <div class="prize-product-details">
                            <div class="prize-product-content">
                                Giá bán:
                            </div>
                            <div class="money-buy-product">
                                {{ priceByFormat }}
                            </div>
                        </div>
                        <div class:="repost-product">
                            <div class="icon-repost-product">
                                <div class="icon-repost-product-content">
                                    <font-awesome-icon icon="fa-solid fa-gift" />
                                    Khuyến mại
                                </div>
                            </div>
                            <div class="offer-tiltle">
                                <div class="repost-product-details">
                                    + Túi/Balo laptop trị giá : 390.000đ
                                </div>
                                <div class="repost-product-details">
                                    + Chuột không dây trị giá: 150.000đ
                                </div>
                                <div class="repost-product-details">
                                    + Bàn di chuột trị giá: 50.000đ
                                </div>
                                <div class="repost-product-details">
                                    + Bộ vệ sinh Laptop trị giá: 40.000đ
                                </div>
                                <div class="repost-product-details">
                                    + Vệ sinh bảo dưỡng Laptop miễn phí trọn đời trị giá: 1 triệu đồng
                                </div>
                                <div class="repost-product-details">
                                    + Giảm 10% khi mua thêm RAM, HDD laptop
                                </div>
                                <div class="repost-product-details">
                                    + Giảm 5% khi mua kèm Gear, Đế tản nhiệt Laptop
                                </div>
                            </div>
                        </div>
                        <div @click="addToCart()" class="btn-buy">
                            ĐẶT MUA NGAY
                            <br>
                            Giao hàng tận nơi nhanh chóng
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="product-detail-read mt-3">
            <div class="test-1">
                <div class="title-detail-des h4" style="font-weight: bold;">
                    Đặc Điểm
                </div>
                <div class="h5" v-for="(des, index) in getDetailsList(product.description + ' ')">{{ des }}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    async beforeMount() {
        this.productId = this.$route.query.productId
        await this.init()
    },
    data() {
        return {
            product: {},
            productId: 0,
            priceByFormat: '0'
        }
    },

    methods: {
        async init() {
            var response = await fetch('https://localhost:7029/api/Product/GetDetail?id=' + this.productId)
                .then((res) => res.json())
            this.product = response
            this.priceByFormat = this.product.price.toLocaleString('vi-VN', { style: 'currency', currency: 'VND', })
        },

        getDetailsList(details) {
            //details='1950 MHz (Chế độ GAMING & SILENT) / 21 Gbps@24 GB GDDR6X@DisplayPort x 3 (v1.4a)@HDMI x 1 (2.1) (Hỗ trợ 4K 120Hz HDR, 8K 60Hz HDR và ​​Tốc độ làm mới có thể thay đổi như được chỉ định trong HDMI 2.1)'
            return details.split("@")
        },

        async addToCart() {
            var user = JSON.parse(localStorage.getItem('user'))
            if (user) {
                var addToCartRequest = {
                    productId: this.productId,
                    userId: user.id
                }
                var repsonseAddToCart = await fetch('https://localhost:7029/api/ProductHandle/AddToCart',
                    {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json'
                        },
                        body: JSON.stringify(addToCartRequest)
                    }
                ).then((res) => res.json())
                if (repsonseAddToCart.id != 0) {
                    alert("Thêm thành công")
                    this.$router.push("/cartPage")
                }

            }
            else {
                alert('BẠN CẦN ĐĂNG NHẬP!')
                return
            }
        },

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
.header-product-details-container {
    width: 100%;
    height: 4500px;
    padding: 0 5%;
}

.header-product {
    font-size: 23px;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    display: flex;

}

.product-general {
    font-size: 18px;
    font-weight: bold;
}

.product-details {
    width: 100%;
    padding: 0 8%;
}

.product-details-content {
    font-size: 17px;
    margin-left: 10px;
}

.img-product {
    width: 100%;
    height: 290px;
}

.img-product-details {
    width: 100%;
    height: 290px;
}

.product-information {
    width: 100%;
    height: 720x;
    background-color: yellow;
}

.status {
    display: flex;
    padding-top: 65px;
}

.YESorNO {
    margin-left: 4px;
}

.status-content-1 {
    margin-left: 25px;
}

.time-insurance {
    margin-left: 4px;
}

.prize-product-details {
    display: flex;
    border: 1px dashed #4267b2;
    width: 100%;
    border-radius: 10px;
}

.prize-product-content {
    padding-top: 15px;
    font-size: 15px;
}

.money-buy-product {
    padding-left: 30px;
    font-size: 30px;
    color: #0f5b9a;
}

.repost-product {
    width: 100%;
    height: 205px;

}

.offer-tiltle {
    border: 1px solid red;
    border-radius: 15px;
    padding-left: 20px;

}


.icon-repost-product {
    width: 35%;
    height: 40px;
    margin-left: 20px;
    display: flex;
    margin-top: 20px;
    background-color: #ed1b24;
    color: #fffafa;
    align-items: center;
    justify-content: center;
    border-radius: 10px;
}

.icon-repost-product-content {
    font-size: 18px;
    color: #fffafa;

}

.btn-buy {
    margin-top: 20px;
    width: 100%;
    height: 80px;
    background-color: #ed1b24;
    text-align: center;
    padding-top: 15px;
    color: #fffafa;
    font-weight: bold;
    border-radius: 10px;
}

.btn-buy:hover {
    cursor: pointer;
}

.product-detail-read {
    width: 100%;
    height: 700px;
    padding: 0 8%;
}

.img-read {
    width: 100%;
}

.test-1 {
    height: 3750px;
    width: 100%;

}

.test-2 {
    background-color: aqua;
    width: 100%;
}

.title-box {
    font-size: 20px;
    font-weight: bold;
}

.content-spec {
    display: flex;
}

.device-product-content {
    border: 1px solid black;
    width: 31%;
    padding: 3%;
    font-size: 15px;
}

.device-product-content-details {
    width: 65%;
    border: 1px solid black;
    padding: 3%;
    font-size: 15px;
}
</style>