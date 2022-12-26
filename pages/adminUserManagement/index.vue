<template>
    <div>
        <div class="table-responsive">
            <table class="table">
                <thead>
                    <tr>
                        <th scope="col">Mã Khách Hàng</th>
                        <th scope="col">Tên</th>
                        <th scope="col">Địa chỉ </th>
                        <th scope="col">Số Điện Thoại</th>
                        <th scope="col">Email đăng nhập</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(user, index) in userList">
                        <td>
                            <div class="admin-user-id">{{ user.id }}</div>   
                        </td>
                        <td>
                           <div class="admin-user-name">{{ user.name }}</div>
                        </td>
                        <td>
                            <div class="admin-user-address">{{ user.address }}</div>
                        </td>
                        <td>
                            <div class="admin-user-phoneNumber">{{ user.phoneNumber }}</div>
                        </td>
                        <td>
                            <div class="admin-user-username">{{ user.username }}</div>
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
        this.postUserList()
    },
    data() {
        return {
            userList: [],
        };
    },
    methods: {
        async postUserList() {
            var response = await fetch('https://localhost:7029/api/User/UserLogin')
                .then(res => {
                    return res.json()
                })
            this.userList = response
            console.log(JSON.stringify(this.userList))
        }
    },
}
</script>

<style>

</style>