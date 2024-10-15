<template>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.css" integrity="sha512-5A8nwdMOWrSz20fDsjczgUidUBR8liPYU+WymTZP1lmY9G6Oc7HlZv156XqnsgNUzTyMefFTcsFH/tnJE/+xBg==" crossorigin="anonymous" referrerpolicy="no-referrer" />
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
  <div id="app">
    <!--Header-->
    <div class="grid">      
            <nav class="header_nav">
                <ul class="header_nav-list">
                    <li class="header_nav-item"><a href="#" @click.prevent="changePage('TrangChu')"><img style="border-radius:100%" src="./assets/pic/logo.png" alt=""></a></li>
                    <li class="header_nav-item"><a href="#" @click.prevent="changePage('TrangChu')"><i class="fa-solid fa-house"></i> HOME</a></li>
                    <li class="header_nav-item"><a href="#" @click.prevent="changePage('SanPham')"><i class="fa fa-store" aria-hidden="true"></i> SHOP</a></li>
                    <li class="header_nav-item"><a href="#"><i class="fa-regular fa-newspaper"></i> Tin tức</a></li>
                    <li class="header_nav-item"><a href="#"><i class="fa-solid fa-money-bill-wave"></i> sale</a></li>
                </ul>
                <ul class="header_nav-list">
                    <li class="header_nav-item"><a href="#" @click.prevent="changePage('GioHang')"><i class="fa-solid fa-cart-shopping"></i> GIỎ HÀNG ({{ cart.length }})</a></li>
                    <li class="header_nav-item"><button class="btn"><a href="#" @click.prevent="changePage('DangNhap')"> <i class="fa-solid fa-user"></i> Đăng Nhập</a></button></li>
                    <li class="header_nav-item header_nav-item--separate"><button class="btn"><a href="#" @click.prevent="changePage('DangKy')"><i class="fa-solid fa-user-plus"></i> Đăng Ký</a></button></li>
                </ul>
            </nav>
    </div>
    <!--Body-->
    <div class="body">
      <trang-chu v-if="currentPage === 'TrangChu'" @changePage="changePage" @addToCart="addToCart" />
      <san-pham v-if="currentPage === 'SanPham'" @addToCart="addToCart" />
      <gio-hang v-if="currentPage === 'GioHang'" :cart="cart" @removeFromCart="removeFromCart" />
      <dang-nhap v-if="currentPage==='DangNhap'" @changePage="changePage" />
      <dang-ky v-if="currentPage==='DangKy'" @changePage="changePage" />
    </div>
    <!--Footer-->
    <div class="footer">
            <div class="lh container">
                <div class="col-sm-3">
                    <p>Địa chỉ: Tây Mỗ, Nam Từ Liêm, Hà Nội</p>
                    <p>SĐT: 09876543321 </p>
                    <p>Email: tanisha@gmail.com</p>
                </div>
                <div class="col-sm-3">
                    <ul>
                        <h5>HỖ TRỢ KHÁCH HÀNG</h5>
                        <li><a href="#">Tìm kiếm</a></li>
                        <li><a href="#">Chính sách bảo mật</a></li>
                        <li><a href="#">Điều khoản dịch vụ</a></li>
                        <li><a href="#">Hưỡng dẫn kiểm tra đơn hàng</a></li>
                    </ul>
                </div>

                <div class="col-sm-3">
                    <ul>
                        <h5>CHÍNH SÁCH</h5>
                        <li><a href="#">Trang chủ</a></li>
                        <li><a href="#">Giới thiệu</a></li>
                        <li><a href="#">Sản phẩm</a></li>
                        <li><a href="#">Liên hệ</a></li>
                        <li><a href="#">Kiểm tra</a></li>
                    </ul>
                </div>
                
                <div class="col-sm-3">
                    <ul>
                        <h5>LIÊN HỆ VỚI CHÚNG TÔI</h5>
                    </ul>
                </div>
            </div>
            <div class="bq">© Bản quyền thuộc về Tanisha</div>
    </div>    
  </div>
</template>
<script>
import TrangChu from './components/pages/TrangChu.vue';
import SanPham from './components/pages/SanPham.vue';
import GioHang from './components/pages/GioHang.vue';
import DangNhap from './components/pages/DangNhap.vue';
import DangKy from './components/pages/DangKy.vue';
export default{
  data(){
    return{
      currentPage: 'TrangChu',
      cart:[],
    }
  },
  components:{
    TrangChu,
    SanPham,
    GioHang,
    DangNhap,
    DangKy,
  },
  methods:{
    changePage(page) {
      this.currentPage = page;
    },
    addToCart(product) {
      // Thêm sản phẩm vào giỏ hàng
      this.cart.push(product);
      alert(`Đã thêm ${product.name} vào giỏ hàng!`);
    },
    removeFromCart(index) {
      this.cart.splice(index, 1); // Xóa sản phẩm khỏi giỏ hàng dựa trên chỉ mục
    }
  },
}
</script>
<style>
*{
    font-family: 'Times New Roman', Times, serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
.body{
    background-color: #ffd19dbc;
}
.grid{
    max-width: 100%;
    min-width: 200px;
    margin: 0 auto;
}
.header_nav{
    display: flex !important;
    justify-content: space-between !important;
    background-color: #f2ccac;
    width: 100%;
}
.header_nav-list{
    list-style-type: none;
    padding-left: 0px;
    margin-bottom: 0px;
}
.header_nav-item{
    display: inline-block;
    margin: 0 8px;
    position: relative;
    line-height: 60px;
}
.header_nav-item a{
    color: #000000;
    font-size: 1.2rem;
    text-decoration: none;
    font-weight: 400;
    height: auto;
}
.header_nav-item a:hover{
    color: #eb7522;
}
.grid img{
    width: 40px;
    height: auto;
}
.header_nav-item button{
    line-height: 20px;
    padding: 5px;
    border-radius: 10px;
}


.header_nav-submenu{
    display: none;
    position: absolute;
    background-color: #fff;
    border: 1px solid black;
    top: 80%;

    z-index: 1;
}
.header_nav-submenu li{
    width: 150px;
}
.header_nav-list li:hover .header_nav-submenu{
    display: block;
}
.header_nav-submenu a{
    color: black;
}
.header_nav-submenu a:hover{
    color: #1072BA;
}
.footer{
    background-color: #d263a6bc;
    color: #fff;
    padding-top: 10px;
    margin-top: 10px;
}
.lh{
    display: flex;
    justify-content: center;
    
}
.lh ul{
    list-style-type: none;
}
.lh li a{
    color: #fff;
    text-decoration: none;
}
.bq{
    background-color: #c72020;
    justify-content: center;
    text-align: center;
    padding: 10px;
}
</style>