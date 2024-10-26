<template>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.css" integrity="sha512-5A8nwdMOWrSz20fDsjczgUidUBR8liPYU+WymTZP1lmY9G6Oc7HlZv156XqnsgNUzTyMefFTcsFH/tnJE/+xBg==" crossorigin="anonymous" referrerpolicy="no-referrer" />
  <div id="app">
    <!--Header-->
    
            <nav class="header">
                <ul class="header1">
                    <li><a href="#" @click.prevent="changePage('TrangChu')"><i class="fa-solid fa-house"></i> HOME</a></li>
                    <li><a href="#" @click.prevent="changePage('SanPham')"><i class="fa fa-store" aria-hidden="true"></i> SHOP</a></li>
                    <li><a href="#" @click.prevent="changePage('TinTuc')"><i class="fa-regular fa-newspaper"></i> TIN TỨC</a></li>
                    <li><a href="#" @click.prevent="changePage('DanhGia')"><i class="fa-solid fa-comments"></i> ĐÁNH GIÁ</a></li>
                    <li  ><a href="#" @click.prevent="changePage('GioHang')"><i class="fa-solid fa-cart-shopping"></i> GIỎ HÀNG ({{ cart.length }})</a></li>
                </ul>
                <ul class="header2">

                    <li  ><a href="#" @click.prevent="changePage('DangNhap')"> <i class="fa-solid fa-user"></i> Đăng Nhập</a></li>
                    <li  ><a href="#" @click.prevent="changePage('DangKy')"><i class="fa-solid fa-user-plus"></i> Đăng Ký</a></li>
                </ul>
            </nav>

    <!--Body-->
    <div class="body">
      <trang-chu v-if="currentPage === 'TrangChu'" @changePage="changePage" @addToCart="addToCart" />
      <san-pham v-if="currentPage === 'SanPham'" @addToCart="addToCart" />
      <gio-hang v-if="currentPage === 'GioHang'" :cart="cart" @removeFromCart="removeFromCart" />
      <tin-tuc v-if="currentPage==='TinTuc'" @changePage="changePage"/>
      <danh-gia v-if="currentPage==='DanhGia'" @changePage="changePage"/>
      <dang-nhap v-if="currentPage==='DangNhap'" @changePage="changePage" />
      <dang-ky v-if="currentPage==='DangKy'" @changePage="changePage" />
    </div>
    <!--Footer-->
    <div class="footer">
            <div class="lh">
               <div class="col-sm-3">
                    <ul>
                        <h5>LIÊN HỆ VỚI CHÚNG TÔI</h5>
                        <li><a href="#">Địa chỉ: Tây Mỗ, Nam Từ Liêm, Hà Nội</a></li>
                        <li><a href="#">SĐT: 09876543321 </a></li>
                        <li><a href="#">Email: tanisha@gmail.com</a></li>
                    </ul>
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
import TinTuc from './components/pages/TinTuc.vue';
import DanhGia from './components/pages/DanhGia.vue';
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
    TinTuc,
    DanhGia,
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
    },

  },
}
</script>
<style>
*{
    font-family: 'Times New Roman', Times, serif;
}
.template{
    background: #000000;
}
  .header{
    background-color:#f2ccac;
    color: #000000;
    display: flex;
    justify-content:space-between;
    padding: 10px 20px 10px 20px;
  }
  .header ul li{
    list-style: none;
  }
  .header a{
    text-decoration: none;
    color: inherit;
  }
  .header1, .header2{
    display: flex;
    gap: 30px;
    
  }

  .header a:hover{
    color:#e295c2af ;
}
.footer{
    background-color: #d263a6bc;
    color: #fff;
    margin-top: 10px;
    line-height: 20px;
    bottom: 0%;
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
.footer a:hover{
    color: #c72020;
}
.bq{
    background-color: #c72020;
    justify-content: center;
    text-align: center;
    padding: 10px;
}
</style>