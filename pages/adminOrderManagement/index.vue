<template>
    <div>
        <div class="mb-3" style="display: flex; align-items: center;">
            Total: {{ total }} Products, Page:
            <div v-for="(room, index) in totalPage">
                <div class="item-page" :id="'page-' + (index)" @click="chooesPage(index)">
                    {{ index + 1 }}
                </div>
            </div>
        </div>
        <div class="table-responsive">
            <table class="table table-bordered">
                <thead style="background-color: #0f5b9a; color: white;">
                    <tr>
                        <th scope="col">Mã Đơn Hàng</th>
                        <th scope="col">Mã Khách Hàng</th>
                        <th scope="col">Tên</th>
                        <th scope="col">Địa chỉ </th>
                        <th scope="col">Số Điện Thoại</th>
                        <th scope="col">Số Lượng</th>
                        <th scope="col">Tổng Tiền</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(order, index) in orderList">
                        <td>
                            {{ order.id}}
                        </td>
                        <td>
                            {{ order.userId }}
                        </td>
                        <td>
                            {{ order.name }}
                        </td>
                        <td>
                            {{ order.address }}
                        </td>
                        <td>
                            {{ order.phoneNumber }}
                        </td>
                        <td>
                            {{ order.quantity }}
                        </td>
                        <td>
                            {{ order.totalPrice }}
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
        this.getOrderList()
    },
    data() {
        return {
            orderList: [],
            total: 0,
            totalPage: 0,
            currentPage: 0,
        };
    },
    methods: {
        async getOrderList() {
            var response = await fetch('https://localhost:7029/api/Order/GetOrders?limit=5&page=' + this.currentPage)
                .then(res => {
                    return res.json()
                })
            this.orderList = response.orderList
            this.total = response.total
            this.totalPage = response.totalPage
            console.log(JSON.stringify(this.orderList))
        },
        chooesPage(index) {
            if (this.currentPage != 0) {
                var element = document.getElementById("page-" + (this.currentPage - 1));
                element.classList.remove("page-item-choose");
            }
            var element = document.getElementById("page-" + index);
            element.classList.add("page-item-choose");
            this.currentPage = index + 1
            this.getOrderList()
        },
    },
}
</script>

<style scoped>
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