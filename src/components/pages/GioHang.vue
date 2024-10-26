<template>
    <div class="gh">
        <div class=" " v-if="cart && cart.length > 0" >
            <div class="empty">
                <div class="cart-item" v-for="(item, index) in cart" :key="index">
                    <img :src="getImageSrc(item.thum)" alt="">
                    <div class="cart-item-details">
                        <h4>{{ item.name }}</h4>
                        <p><span>{{ formatPrice(item.price) }}</span><sup>đ</sup></p>
                        <button class="btn-xoa" @click="removeFromCart(index)">Xóa</button>
                    </div>
                </div>
            </div>                
                <div class="d-flex done">
                    <h3>Tổng tiền: {{ totalCartPrice() }} đ</h3>
                    <button class="btn-thanhtoan">Thanh toán</button>
                </div>

        </div>
        <div class="troongs" v-else>
            <p>Giỏ hàng của bạn đang trống.</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        cart: Array,
    },
    name: 'GioHang',
    methods: {
        removeFromCart(index) {
            this.$emit('removeFromCart', index); // Phát sự kiện để xóa sản phẩm khỏi giỏ hàng
        },
        totalCartPrice() {
            return this.cart.reduce((total, item) => {
                const priceNumber = parseFloat(item.price.replace(/\./g, '').replace(/,/g, ''));

                return total + priceNumber;
            }, 0).toLocaleString();
        },
        getImageSrc(thum) {
            return require(`@/assets/pic/${thum}`);
        },
        formatPrice(price) {
            return price.replace(/\B(?=(\d{3})+(?!\d))/g, "."); // Định dạng giá với dấu chấm
        },
    }
}
</script>
<style>
.troongs{
    text-align: center;
    color: #ffffff91;
    margin: 100px;
    padding-left:40px ;
}
.gh{
    margin-top:30px ;
}
.empty {
  display: flex;
  flex-wrap: wrap; /* Cho phép các phần tử xuống dòng nếu không đủ chỗ */
  justify-content: space-between; /* Khoảng cách đều giữa các mục */
}

.cart-item {
  width: 20%; 
  background-color: #f9f9f9; /* Màu nền của các thẻ */
  margin: 20px; /* Khoảng cách dưới giữa các thẻ */
  padding: 15px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Thêm bóng đổ */
  border-radius: 10px; /* Bo góc cho thẻ */
  transition: transform 0.3s; /* Hiệu ứng khi hover */
  height: 400px;
}

.cart-item:hover {
  transform: scale(1.05); /* Phóng to thẻ khi hover */
}

.cart-item img {
  width: 100%; /* Hình ảnh chiếm hết chiều rộng của thẻ */
  height: 60%; /* Giữ tỉ lệ hình ảnh */
  margin-bottom: 10px;
  object-fit: cover;
}

.cart-item-details {
  text-align: center; /* Căn giữa văn bản trong thẻ */
}

.cart-item-details h4 {
  margin: 10px 0;
  font-size: 18px;
}

.cart-item-details p {
  font-size: 16px;
  color: #333;
}

.cart-item-details p span {
  font-weight: bold;
}

.btn-xoa {
  background-color: #e74c3c;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
  width: 30%;
}

.btn-xoa:hover {
  background-color: #c0392b;
}

.btn-thanhtoan{
    background-color: #03ae28; /* Màu nền nút xóa */
    color: #fff; /* Màu chữ nút xóa */
    border: none; /* Bỏ đường viền */
    border-radius: 5px; /* Bo tròn góc cho nút */
    padding: 10px 15px; /* Khoảng cách bên trong nút */
    cursor: pointer; /* Hiệu ứng con trỏ khi hover vào nút */
    transition: background-color 0.3s; /* Hiệu ứng chuyển tiếp cho màu nền */
    margin: 20px 10px 20px 10px; 
}
.btn-thanhtoan:hover {
    background-color: #1bd31b8c; /* Thay đổi màu nền khi hover vào nút xóa */
}

</style>
