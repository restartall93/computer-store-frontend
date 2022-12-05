<template>
    <div class="user-login-container">
        <div class="row">
            <div class="col-md-12 col-lg-6 col-xl-6">
                <div class="control-login">
                    <div class="control-item">
                        <div class="label-control">
                            UserName: 
                        </div>
                        <input type="text" class="form-control" placeholder="Username"/>
                    </div>
                    <div class="control-item">
                        <div class="label-control">
                            Password: 
                        </div>
                        <input type="password" class="form-control" placeholder="Password"/>
                    </div>
                </div>
            </div>
            <div class="col-md-12 col-lg-6 col-xl-6"></div>
        </div>
    </div>
</template>
<script>
export default {
    beforeMount(){

    }

};
</script>
<style>
.user-login-container{
    width: 100%;
    min-height: 50px;
    padding: 0 8%;
}
.control-login{
    width: 100%;
    padding: 10px 5%;
}

.control-item{
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
}
.label-control{
    width: 200px;
}
</style>