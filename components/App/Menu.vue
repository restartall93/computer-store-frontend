<template>
    <div class="menu-left mt-2">
        <NuxtLink class="menu-item" :to="{ name: 'category', query: {'productType': 'Lap-top'} }">
            <font-awesome-icon icon="fa-solid fa-laptop icon-menu" />
            <div class="menu-item-content">
                Laptop - Phụ Kiện
            </div>
        </NuxtLink>
        <NuxtLink class="menu-item" :to="{ name: 'category', query: {'productType': 'Computer'} }">
            <font-awesome-icon icon="fa-solid fa-computer" />
            <div class="menu-item-content">
                pc gaming - làm việc
            </div>
        </NuxtLink>
        <NuxtLink class="menu-item" :to="{ name: 'category', query: {'productType': 'CPU'} }">
            <font-awesome-icon icon="fa-solid fa-microchip" />
            <div class="menu-item-content">
                linh kiện máy tính
            </div>
        </NuxtLink>
        <NuxtLink class="menu-item" :to="{ name: 'category', query: {'productType': 'Drive'} }">
            <font-awesome-icon icon="fa-solid fa-hard-drive" />
            <div class="menu-item-content">
                thiết bị lưu trữ
            </div>
        </NuxtLink>
        <NuxtLink class="menu-item" :to="{ name: 'category', query: {'productType': 'Screen'} }">
            <font-awesome-icon icon="fa-solid fa-desktop" />
            <div class="menu-item-content">
                màn hình máy tính
            </div>
        </NuxtLink>
        <NuxtLink class="menu-item" :to="{ name: 'category', query: {'productType': 'Gear'} }">
            <font-awesome-icon icon="fa-solid fa-gamepad" />
            <div class="menu-item-content">
                phím chuột,ghế,gear
            </div>
        </NuxtLink>
        <NuxtLink class="menu-item" :to="{ name: 'category', query: {'productType': 'Fan'} }">
            <font-awesome-icon icon="fa-solid fa-fan" />
            <div class="menu-item-content">
                tản nhiệt pc, cooling
            </div>
        </NuxtLink>
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
    color: black;
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
    text-decoration: none;
}

.menu-item:hover .icon-menu {
    color: #ccc;
}


.wrapper {
    max-width: 960px;
    margin: 10% auto;
    text-align: center;
    line-height: 2em;
}

.button {
    border: 3px solid #111;
    adding: 10px;
    color: #111;
    text-decoration: none;
}


.popup {
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background: rgba(0, 0, 0, 0.6);
    display: none;
}

#xmas-popup .popup-content {
    width: 600px;
    height: 600px;
    background: #bbb;
    margin: 100px auto;
    position: relative;
    border: 5px solid #fff;
}

.close {
    position: absolute;
    top: 5px;
    right: 5px;
    border-radius: 50%;
    background: #222;
    border: 3px solid #fff;
    color: #fff;
    text-decoration: none;
    line-height: 0;
    padding: 9px 0 11px;
    width: 20px;
    text-align: center;
}

.popup:target {
    display: block;
}
</style>
