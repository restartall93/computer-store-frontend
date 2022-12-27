<template>
    <div class="header-product-details-container">
        <div class="header-product">
            {{product.name}}
        </div>
        <div class="product-details">
            <div class="row">
                <div class="col-md-12 col-lg-5 col-xl-5">
                    <div class="img-product">
                        <img class="img-product-details"
                        v-bind:src="'https://localhost:7029'+product.image" alt="">
                    </div>
                </div>
                <div class="col-md-12 col-lg-7 col-xl-7">
                    <div class="product-information">
                        <div class="product-general">
                            Thông số sản phẩm
                        </div>
                        <div class="product-details-content">
                            <li>CPU: {{product.cpu}}</li>
                        </div>
                        <div class="product-details-content">
                            <li>RAM: {{product.ram}}</li>
                        </div>
                        <div class="product-details-content">
                            <li>Ổ cứng: {{product.drive}}</li>
                        </div>
                        <div class="product-details-content">
                            <li>VGA: {{product.vga}}</li>
                        </div>
                        <div class="product-details-content">
                            <li>Màn hình: {{product.monitor}}</li>
                        </div>
                        <div class="product-details-content">
                            <li>Bàn phím: có đèn led</li>
                        </div>
                        <div class="product-details-content">
                            <li>HĐH: Win 11</li>
                        </div>
                        <div class="product-details-content">
                            <li>Màu: Đen</li>
                        </div>
                        <div class="status">
                            <div class="status-content">
                                Tình trạng:
                            </div>
                            <div class="YESorNO">
                                Liên hệ
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
                                21.000.000đ
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
        <div class="product-detail-read">
            <div class="row">
                <div class="col-md-12 col-lg-7 col-xl-7">
                    <div class="test-1">
                        <div class="title-detail-des">
                            Đặc Điểm VIDEO BÌNH LUẬN
                        </div>
                        <div class="title">
                            Giới thiệu Laptop Gigabyte Gaming G5 MD 51S1123SO ( i5-11400H/ 16GB/ 512GB SSD/ 15.6" FHD/
                            RTX3050Ti 4Gb/ Win11)
                        </div>
                        <div class="des-content">
                            <p>Sức mạnh vượt bậc, chiến game cực đã</p>
                            <p>Laptop được trang bị con chip Intel Core i thế hệ 11 trên công nghệ Turbo Boost cho hiệu
                                suất tăng 20% so với các thế hệ trước, không chỉ chơi game tốt mà nó còn đem đến sức
                                mạnh vượt trội xử lý nhanh gọn các phần mềm văn phòng trên Word, Excel, PowerPoint,...
                                hay thiết kế poster, chỉnh sửa hình ảnh, render video,... mượt mà.</p>
                            <p>RAM DDR4 2 khe có tốc độ Bus RAM 3200 MHz cho khả năng đa nhiệm vượt trội, bạn có thể mở
                                cùng lúc nhiều ứng dụng nền việc vừa chơi game vừa phát sóng trực tiếp vẫn không có vấn
                                đề gì. Hay vừa thiết kế banner trên Photoshop vừa bật YouTube nghe nhạc. Ngoài ra, bạn
                                có thể nâng cấp tối đa lên đến 64 GB đáp ứng tối đa mọi nhu cầu của bạn.</p>
                            <p>Card đồ họa rời NVIDIA GeForce RTX 3000 cải thiện khả năng hiển thị hình ảnh khi chơi
                                game, làm đồ họa. Bạn có thể chơi các tựa game phổ biến hiện nay như: GTA V, LOL, CS:GO,
                                Cyberpunk 2077,... hay thỏa sức sáng tại trên các phần mềm như: Photoshop, AI,
                                Lightroom, Pr, Figma,...</p>
                            <p>Sử dụng ổ cứng SSD NVMe PCIe cho thời gian phản hồi nhanh chóng, nếu bạn thấy ổ đi kèm
                                không đủ dùng thì bạn có thể thay thanh SSD có sẵn ra và lắp thanh khác vào với dung
                                lượng tối đa là 1 TB.</p>
                            <p> <img class="img-read" src="../../assets/img/61677_laptop_gigabyte_gaming_g5_5.png"
                                    alt=""></p>
                            <p>Không dừng lại ở đây, máy còn được trang bị thêm khe cắm SSD M.2 PCIe mở rộng (nâng cấp
                                tối đa 1 TB) và khe cắm HDD SATA (nâng cấp tối đa 2 TB) để bạn dễ dàng mở rộng không
                                gian lưu trữ, bạn có thể thả ga lưu trữ mà không lo máy bị hết dung lượng.</p>
                            <p>Laptop GIGABYTE được trang bị hệ thống tản nhiệt hiện đại với 2 quạt có 71 cánh giúp
                                không khí được lưu thông nhanh chóng, đảm bảo máy tính không bị nóng khi hoạt động ở
                                công suất cao. Duy trì sự mượt mà khi chơi game hay làm đồ họa hàng giờ liền.</p>
                            <p>Có một điểm khá đặc biệt ở GIGABYTE Gaming G5 chính là pin rời. Hiện tại rất ít hãng nào
                                dùng pin rời cho laptop của mình, bạn có thể dự trữ nhiều thanh pin để thay thế khi hết
                                một cách dễ dàng mà không cần dậy sạc rườm rà. Tuy nhiên, pin rời sẽ chiếm đi vị trí khe
                                thoát nhiệt phía sau của máy và giảm bớt đi phần nào khả năng thoát nhiệt khi máy vận
                                hành những tác vụ nặng.</p>
                            <p>Vẻ ngoài tối giản nhưng vẫn đậm chất riêng</p>
                            <p>Lớp vỏ của chiếc laptop GIGABYTE này được làm từ nhựa để thoát nhiệt tốt hơn và sở hữu
                                gam màu đen cực mạnh mẽ, logo kim loại sáng bóng nằm giữa mặt lưng thu hút từ ánh nhìn
                                đầu tiên. Máy có trọng lượng 2.2 kg và có độ dày 24.9 mm đáp ứng khá tốt nhu cầu di
                                chuyển của người dùng cùng với một chiếc laptop gaming.</p>
                            <p>Bàn phím laptop được thiết kế rộng rãi, hạn chế tối đa tình trạng nhấn nhầm khi chơi
                                game, làm việc. Được tích hợp thêm dải đèn LED phía dưới các phím tạo sự nổi bật, giúp
                                bạn xác định vị trí các phím nhanh chóng khi chơi game hay đang sử dụng trong môi trường
                                thiếu sáng.</p>
                            <p><img class="img-read" src="../../assets/img/61677_laptop_gigabyte_gaming_g5_3.png"
                                    alt=""></p>
                            <p>Bên phải của bàn phím được trang bị các phím số hỗ trợ tốt nhất cho công việc của bạn,
                                khi bạn gõ thì tiếng phát ra không quá lớn sẽ tránh làm ảnh hưởng đến người xung quanh
                                mà bạn cũng tập trung hơn.</p>
                            <p>Kết nối dễ dàng với các thiết bị khác nhờ các cổng được trang bị xung quanh laptop như:
                                USB 3.2, HDMI, Jack tai nghe 3.5 mm, LAN (RJ45), Mini DisplayPort, USB 2.0, Type-C.</p>
                            <p>Chuẩn kết nối không dây Bluetooth 5.2 và Wi-Fi 6 (802.11ax) cho kết nối ổn định, liên kết
                                và truyền xuất đến các thiết bị khác nhanh chóng không cần dùng dây cáp, tốc độ truy cập
                                mạng nhanh chóng.</p>
                            <p>Trải nghiệm chân thật với màn hình sắc nét</p>
                            <p>Laptop được trang bị màn hình 15.6 inch độ phân giải Full HD (1920 x 1080) thể hiện hình
                                ảnh sắc nét từng chi tiết, cho bạn thưởng thức trọn vẹn trò chơi và bộ phim yêu thích.
                            </p>
                            <p>Cùng với đó là tấm nền IPS cho góc nhìn 178 độ không gian hiển thị thêm phần mở rộng,
                                hình ảnh không bị biến đổi khi bạn nhìn từ góc nghiêng tạo cảm giác thoải mái. Lớp chống
                                chói Anti Glare đem đến những hình ảnh sắc nét với màu sắc chính xác dù bạn sử dụng ở
                                nơi có cường độ sáng cao như ngoài trời mà không lo mắt bị mỏi hay lóa.</p>
                            <p><img class="img-read" src="../../assets/img/61677_laptop_gigabyte_gaming_g5_2.png" alt=""></p>
                            <p>Không dùng lại ở đó, laptop sở hữu tần số quét màn hình 144 Hz có khả năng tái tạo khung
                                hình cực nhanh, hạn chế tối đa tình trạng giật lag, lưu bóng hay xé hình khi nhân vật có
                                các chuyển động nhanh. Giúp bạn phản ứng nhanh chóng khi chơi game hay chỉnh sửa video.
                            </p>
                            <p>Tận hưởng không gian âm nhạc thật thư giãn với công nghệ âm thanh DTS:X Ultra có khả năng
                                tái tạo âm thanh 3D sống động bạn có thể nghe rõ cả tiếng gió khi chơi game, những âm
                                bass được phát ra cực đã.</p>
                        </div>
                    </div>
                </div>
                <div class="col-md-12 col-lg-5 col-xl-5">
                    <div class="test-2">
                        <div class="box-spec">
                            <div class="title-box">
                                THÔNG SỐ KỸ THUẬT
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    Hãng sản xuất
                                </div>
                                <div class="device-product-content-details">
                                    Gigabyte
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    Chủng loại
                                </div>
                                <div class="device-product-content-details">
                                    G5
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    Part Number
                                </div>
                                <div class="device-product-content-details">
                                    MD-5 51S1123SO
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    Màu sắc
                                </div>
                                <div class="device-product-content-details">
                                    Đen
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    CPU
                                </div>
                                <div class="device-product-content-details">
                                    Intel i5 11400H (2.7Ghz, upto 4.5Ghz)
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    Chipset
                                </div>
                                <div class="device-product-content-details">
                                    Intel HM570
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    RAM
                                </div>
                                <div class="device-product-content-details">
                                    16GB DDR4 3200Mhz (8GB * 2)
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    Số khe cắm
                                </div>
                                <div class="device-product-content-details">
                                    2
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    Dung lượng tối đa
                                </div>
                                <div class="device-product-content-details">
                                    64GB
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    VGA
                                </div>
                                <div class="device-product-content-details">
                                    NVIDIA GeForce RTX 3050Ti 4GB GDDR6
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    Ổ cứng
                                </div>
                                <div class="device-product-content-details">
                                    512GB SSD
                                </div>
                            </div>
                            <div class="content-spec">
                                <div class="device-product-content">
                                    Màn hình
                                </div>
                                <div class="device-product-content-details">
                                    15.6 inch FHD 1920x1080 IPS, Anti-glare LCD (144Hz, 72% NTSC), 100% srgb
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    async beforeMount() {
        this.productId = this.$route.query.productId
        this.init()
    },
    data() {
        return {
            product: {},
            productId: 0,
        }
    },

    methods: {
        async init(){
            var response = await fetch('https://localhost:7029/api/Product/GetDetail?id='+ this.productId)
                .then((res) => res.json())
            this.product = response
        },

        addToCart(){
            alert("OK!")
        }
    },

    watch: {
        $route(to, from){
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
    font-size: 15px;
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
    background-color: red;
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