<template>
    <div class="menu-left">
        <div class="menu-item">
            <i class="fa-solid fa-laptop icon-menu"></i>
            <div class="menu-item-content">
                Laptop - Phụ Kiện
            </div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-computer"></i>
            <div class="menu-item-content">
                pc đồ hoạ - làm việc
            </div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-computer"></i>
            <div class="menu-item-content">
                pc gaming
            </div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-microchip"></i>
            <div class="menu-item-content">
                linh kiện máy tính
            </div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-hard-drive"></i>
            <div class="menu-item-content">
                thiết bị lưu trữ
            </div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-desktop"></i>
            <div class="menu-item-content">
                màn hình máy tính
            </div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-gamepad"></i>
            <div class="menu-item-content">
                phím chuột,ghế,gear
            </div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-fan"></i>
            <div class="menu-item-content">
                tản nhiệt pc, cooling
            </div>
        </div>
    </div>
</template>

<style>
.menu-left {
    width: 100%;
    min-height: 200px;
    background-color: white;
    border-radius: 15px;
}

.menu-item {
    width: 100%;
    height: 45px;
    display: flex;
    align-items: center;
    padding: 0 15px;
    font-size: 20px;
}

.menu-item-content {
    margin-left: 10px;
    text-transform: uppercase;
    font-size: 15px;
}

.menu-item:hover {
    color: white;
    background-color: #0f5b9a;
    cursor: pointer;
}

.menu-item:hover .icon-menu {
    color: #ccc;
}
</style>
