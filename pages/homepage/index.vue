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
        </div>
        <div class="product-content">
            <div class="title-product">
                laptop - phụ kiện
            </div>
            <div class="row">
                <div class="col-md-6 col-lg-4 col-xl-3" v-for="(product, index) in laptopList">
                    <div class="card-item">
                        <NuxtLink class="txt-details" :to="{ name: 'productDetails', query: {'productId': product.id} }">
                            <img class="img-1" v-bind:src="'https://localhost:7029'+product.image" alt="">
                            <div class="img-content">
                                {{ product.name }}
                            </div>
                        </NuxtLink>
                        <div class="status-product">
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
                pc đồ hoạ - làm việc
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
                pc gaming
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
                cpu - bộ vi xử lý
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
        var response = await fetch('https://localhost:7029/api/Product/GetProducts')
            .then(res => 
                { 
                    return res.json()
                })
        this.laptopList = response
    },

    data() {
        return {
            laptopList: []
        }
    }


};
</script>
<style>
.product-content {
    width: 100%;
    height: 2500px;
    padding: 0 7%;
    font-size: 20px;
    font-weight: bold;
    text-transform: uppercase;
}

.card-item {
    width: 90%;
    margin-left: 5%;
    height: 300px;
    margin-bottom: 20px;
    background-color: yellow;

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
}

.txt-details:hover {
    text-decoration: none;
}

.status-product {
    font-size: 10px;
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
}
</style>
