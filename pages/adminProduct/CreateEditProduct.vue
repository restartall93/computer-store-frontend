<template>
    <div class="user-login-container">
        <div class="text-control-login">
            {{ title }}
        </div>
        <form v-on:submit.prevent="submit()">
            <div class="row">
                <div class="col-md-12 col-lg-12 col-xl-8">

                    <div class="control-login">
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
                            <select v-model="product.productType" class="form-control">
                                <option v-for="category in productTypeList">{{ category }}</option>
                            </select>
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Danh mục sản phẩm
                            </div>
                            <select v-model="product.category" class="form-control">
                                <option v-for="category in categoryList">{{ category }}</option>
                            </select>
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Giá tiền
                            </div>
                            <input class="form-control" placeholder="Giá tiền" v-model="product.price" required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                CPU
                            </div>
                            <input type="text" class="form-control" placeholder="CPU" v-model="product.cpu" required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                RAM
                            </div>
                            <input type="text" class="form-control" placeholder="RAM" v-model="product.ram" required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Drive
                            </div>
                            <input type="text" class="form-control" placeholder="Drive" v-model="product.drive"
                                required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                VGA
                            </div>
                            <input type="text" class="form-control" placeholder="VGA" v-model="product.vga" required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Monitor
                            </div>
                            <input type="text" class="form-control" placeholder="Monitor" v-model="product.monitor"
                                required />
                        </div>
                        <div class="control-item-register">
                            <div class="label-control">
                                Mô tả
                            </div>
                            <input type="text" class="form-control" placeholder="Mô tả" v-model="product.description"
                                required />
                        </div>
                    </div>
                </div>
                <div class="col-md-12 col-lg-12 col-xl-4">
                    <div v-if="productId == 0">
                        <input class="input-control-admin mt-2" @change="getFile($event)" type="file"
                            accept=".jpg, .jpeg, .png">
                    </div>
                    <div v-else class="w-100 mt-2" style="min-height: 100px;">
                        <img class="w-100" v-bind:src="'https://localhost:7029' + product.image" alt="">
                    </div>
                </div>
            </div>
            <div class="w-100 d-flex justify-content-center mt-4">
                <button type="submit" class="btn btn-primary">Thêm Mới</button>
            </div>
        </form>
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
            title: '',
            file: '',
            imageFile: null,
            productTypeList: ['Computer', 'Lap-top', 'Screen', 'CPU', 'Drive', 'VGA', 'Gear', 'Fan'],
            categoryList: ['Computer', 'Item'],
        }
    },

    methods: {
        async init() {
            if (this.productId == 0) {
                this.title = 'Thêm Mới Sản Phẩm'
            }
            else {
                this.title = 'Sửa Sản Phẩm'
            }
            var response = await fetch('https://localhost:7029/api/Product/GetDetail?id=' + this.productId)
                .then((res) => res.json())
            this.product = response
        },

        getFile(e) {
            this.imageFile = e.target.files[0]
            console.log(this.imageFile.name)
        },

        async submit() {
            if (this.productId == 0) {
                const imgFile = this.imageFile
                if (imgFile == null) {
                    alert("Input file, please!")
                    return
                }

                var productRequest = {
                    name: this.product.name,
                    image: imgFile.name,
                    price: this.product.price,
                    category: this.product.category,
                    productType: this.product.productType,
                    description: this.product.description,
                    cpu: this.product.cpu,
                    ram: this.product.ram,
                    drive: this.product.drive,
                    vga: this.product.vga,
                    monitor: this.product.monitor,
                }

                const formData = new FormData()
                formData.append('image', imgFile, imgFile.name);
                console.log(formData.append)

                var responseUpLoad = await fetch('https://localhost:7029/api/Product/PostImage', {
                    method: 'POST',
                    header: {
                        'Content-Type': 'm  ultipart/form-data'
                    },
                    body: formData
                })
                if (responseUpLoad == false) {
                    alert('Post image fail!')
                    console.log('responseUpLoad: ' + responseUpLoad)
                    return
                }
                alert(JSON.stringify(responseUpLoad))

                var responseCreate = await fetch('https://localhost:7029/api/Product/AddProduct',
                    {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json'
                        },
                        body: JSON.stringify(productRequest)
                    }
                ).then((res) => res.json())
                alert(JSON.stringify(responseCreate))
                if (responseCreate.code == 'error') {
                    this.notify = responseCreate.des
                    return
                }
                alert('Create product successful!')
                this.$router.push({
                    name: 'adminProduct',
                })
            }
            else {
                try {
                    var hotelRequest = {
                        name: this.hotel.name,
                        address: this.hotel.address,
                        status: this.hotel.status,
                        area: this.hotel.area,
                        hotelType: this.hotel.hotelType,
                        price: this.hotel.price,
                    }
                    var responseUpdate = {}
                    await postDataWithToken(baseApi + '/api/HotelMangement/UpdateHotel?hotelId=' + this.hotelId.id, hotelRequest, token)
                        .then(data => {
                            responseUpdate = data
                            console.log(responseUpdate)
                        })
                    if (responseUpdate.code == 'error') {
                        this.notify = responseUpdate.des
                        return
                    }
                    alert('Update product successful!')
                    this.$router.push({
                        name: 'hotel',
                    })

                }
                catch (e) {
                    throw e
                }
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