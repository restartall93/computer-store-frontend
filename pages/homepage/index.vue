<template>
    <div>
        <div class="body-app">
            <div class="menu-app">
                <Menu></Menu>
            </div>
            <!-- <div class="main-app">
                <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
                    <ol class="carousel-indicators">
                        <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
                        <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
                        <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
                    </ol>
                    <div class="carousel-inner">
                        <div class="carousel-item active">
                            <img class="d-block w-100" src="../../assets/img/slide_1.jpg" alt="First slide">
                        </div>
                        <div class="carousel-item">
                            <img class="d-block w-100" src="../../assets/img/slide_3.jpg" alt="Second slide">
                        </div>
                        <div class="carousel-item">
                            <img class="d-block w-100" src="../../assets/img/slide_4.jpg" alt="Third slide">
                        </div>
                    </div>
                    <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
                        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                        <span class="sr-only">Previous</span>
                    </a>
                    <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
                        <span class="carousel-control-next-icon" aria-hidden="true"></span>
                        <span class="sr-only">Next</span>
                    </a>
                </div>
            </div> -->
            <div class="slide-container px-5">
                <img v-if="i == 1" class="w-100 h-100" src='../../assets/img/slide_1.jpg'>
                <img v-if="i == 2" class="w-100 h-100" src='../../assets/img/slide_2.jpg'>
                <img v-if="i == 3" class="w-100 h-100" src='../../assets/img/slide_3.jpg'>
                <div class="button-list-slide">
                    <div @click="pickSlide(1)" id="button-slide-1" class="button-slide"></div>
                    <div @click="pickSlide(2)" id="button-slide-2" class="button-slide"></div>
                    <div @click="pickSlide(3)" id="button-slide-3" class="button-slide"></div>
                </div>
            </div>
        </div>
        <div class="product-content">
            <div class="title-product">
                laptop - phụ kiện
            </div>
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3" v-for="(product, index) in laptopList">
                    <div class="card-item">
                        <NuxtLink class="txt-details"
                            :to="{ name: 'productDetails', query: { 'productId': product.id } }">
                            <img class="img-1" v-bind:src="'https://localhost:7029' + product.image" alt="">
                            <div class="img-content">
                                {{ product.name }}
                            </div>
                        </NuxtLink>
                        <div class="status-product-homepage">
                            Liên hệ
                        </div>
                        <div class="prize-product">
                            {{ product.price.toLocaleString('vi-VN', { style: 'currency', currency: 'VND', }) }}
                            <div @click="addToCartOnclick(product.id)" class="icon-cast-product">
                                <font-awesome-icon icon="fa-solid fa-cart-shopping" />
                            </div>
                        </div>

                    </div>
                </div>
            </div>
            <div class="title-product">
                pc gaming - làm việc
            </div>
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3" v-for="(product, index) in computerList">
                    <div class="card-item">
                        <NuxtLink class="txt-details"
                            :to="{ name: 'productDetails', query: { 'productId': product.id } }">
                            <img class="img-1" v-bind:src="'https://localhost:7029' + product.image" alt="">
                            <div class="img-content">
                                {{ product.name }}
                            </div>
                        </NuxtLink>
                        <div class="status-product-homepage">
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
            <div class="title-product">
                cpu - bộ vi xử lý
            </div>
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3" v-for="(product, index) in cpuList">
                    <div class="card-item">
                        <NuxtLink class="txt-details"
                            :to="{ name: 'productDetails', query: { 'productId': product.id } }">
                            <img class="img-1" v-bind:src="'https://localhost:7029' + product.image" alt="">
                            <div class="img-content">
                                {{ product.name }}
                            </div>
                        </NuxtLink>
                        <div class="status-product-homepage">
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
            <div class="title-product">
                vga - card màn hình
            </div>
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
            </div>
            <div class="title-product">
                Màn hình máy tính
            </div>
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
            </div>
            <div class="title-product">
                phím chuột, ghế, gear
            </div>
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">
                        <div></div>
                        <div></div>
                        <div></div>
                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
                <div class="col-md-6 col-lg-4 col-xl-3">
                    <div class="card-item">

                    </div>
                </div>
            </div>
        </div>

    </div>
</template>
<script>
import Menu from '../../components/App/Menu.vue'
export default {
    components: { Menu },
    async beforeMount() {
        //Get laptop list
        var responseLaptop = await fetch('https://localhost:7029/api/Product/GetProductListByCategory?productType=Lap-top')
            .then(res => {
                return res.json()
            })
        this.laptopList = responseLaptop

        // get computer list
        var responseComputer = await fetch('https://localhost:7029/api/Product/GetProductListByCategory?productType=Computer')
            .then(res => {
                return res.json()
            })
        this.computerList = responseComputer

        // get cpu list
        var responseCPU = await fetch('https://localhost:7029/api/Product/GetProductListByCategory?productType=CPU')
            .then(res => {
                return res.json()
            })
        this.cpuList = responseCPU
        var elementA = document.getElementById("button-slide-1");
        elementA.classList.add("button-slide-active");
        setInterval(this.myTimer, 3000)
    },

    data() {
        return {
            laptopList: [],
            computerList: [],
            cpuList: [],
            backgroundList: [],
            backgroundCurrent: '',
            i: 1,
        }
    },

    methods: {
        myTimer() {
            if (this.i == 3) {
                this.changeColor(1)
                this.i = 1;
            }
            else {
                this.changeColor(this.i + 1)
                this.i++;
            }
        },

        pickSlide(value) {
            this.changeColor(value)
            this.i = value
        },

        changeColor(value) {
            var elementR = document.getElementById("button-slide-" + (this.i));
            elementR.classList.remove("button-slide-active");
            var elementA = document.getElementById("button-slide-" + value);
            elementA.classList.add("button-slide-active");
        },

        async addToCartOnclick(productId) {
            if (confirm('Bạn có muốn thêm sản phẩm vào giỏ hàng?')) {
                var user = JSON.parse(localStorage.getItem('user'))
                if (user) {
                    var addToCartRequest = {
                        productId: productId,
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
            } else {
                alert('Đã huỷ thêm vào giỏ hàng!');
            }
        }
    },
};
</script>
<style>
.title-product {
    font-size: 30px;
}

.product-content {
    width: 100%;
    min-height: 2200px;
    padding: 0 7%;
    font-size: 20px;
    font-weight: bold;
    text-transform: uppercase;
}

.menu-app {
    width: 250px;
    min-height: 500px;
}

.slide-container {
    width: calc(100% - 250px);
    height: 450px;
}

.card-item {
    width: 90%;
    margin-left: 5%;
    height: 300px;
    margin-bottom: 20px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.img-1 {
    width: 100%;
    height: 162px;
}

.img-content {
    width: 100%;
    font-size: 13px;
    padding: 0 3%;
    color: black;
    height: 80px;
}


.txt-details:hover {
    text-decoration: none;
}

.status-product-homepage {
    font-size: 15px;
    color: red;
    padding: 0 3%;
}

.prize-product {
    display: flex;
    justify-content: space-between;
    width: 100%;
    padding: 0 3%;
}

.icon-cast-product {
    font-size: 17px;
    border: 1px solid #0f5b9a;
    border-radius: 50%;
    width: 30px;
    height: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #0f5b9a;
    cursor: pointer;
}

.button-list-slide {
    display: flex;
    justify-content: center;
    width: 100%;
    height: 20px;
    align-items: center;
}

.button-slide {
    height: 15px;
    width: 15px;
    border-radius: 50%;
    background-color: #ccc;
    margin-right: 3px;
    cursor: pointer;
}

.button-slide-active {
    background-color: red;
}
</style>
