<template>
    <div id="products" v-if="currentPage === 'products'">
        <div class="banner">
            <img :src="image" alt="">
            <div>
                <p>Tanisha</p>
            </div>
            <div>
                <a>Ngon khó cưỡng!!</a>
            </div>
        </div>

            <div class="container ">
                <div class="tieude">
                    <h1>Sale</h1>   
                </div>
                <div class="product-items">
                 <div class="product-item" v-for="product in products" :key="product.id"> 
                           <img :src="require(`@/assets/pic/${product.thum}`)" alt="" style="width: 95%;" >    
                        <h3>{{ product.name }}</h3>
                        <p style="text-align:left; color:red;margin:3px;"><del>Giá cũ: {{ product.oldprice }}<sup>đ</sup>  </del></p>
                        <p style="text-align:left"><span >Giá mới: {{ product.price }}</span><sup>đ</sup></p>
                        <button @click="$emit('addToCart', product)" >Thêm vào giỏ hàng</button>
                    </div>
                </div>
            </div>
    </div>
</template>
<script>
export default{
    name:'TrangChu',
    props:['product'],
    data(){
        return{
            image: require(`@/assets/pic/banner.jpg`),
            currentPage: 'products',
            products:[
                { id: 1,category:"banhkem", name: 'Bánh Kem Dâu',  thum:  'kd.jpg', oldprice:"300.000", price: "200.000" },
                { id: 2,category:"banhkem", name: 'Bánh Kem Socola', thum:  'ks.webp', oldprice:"350.000", price: "250.000" },
                { id: 4,category:"banhkem", name: 'Bánh Kem Matcha', description: 'Bánh kem với vị matcha thơm ngon.', thum:  'kmc.jpg',oldprice:"350.000", price: "220.000" },
                { id: 8, category:"banhlava", name: 'Bánh Lava Socola',  thum: 'scllv.png'  , oldprice:"400.000", price: "350.000" },
                { id: 6,category:"banhkem", name: 'Bánh Kem Chanh Dây', description: 'Bánh kem với hương vị chanh dây tươi mát.', thum:  'kcd.jpg',oldprice:"350.000", price: "260.000" },
                { id: 9, category:"banhlava", name: 'Bánh Lava Matcha', thum: 'mclv.jpg'  , oldprice:"500.000" ,price: "400.000" },
                { id: 16, category:"banhtỉamisu", name: 'Tiramisu Trái Cây',  thum:  'traicay.jpg', oldprice:"700.000", price: "480.000" },
                { id: 17, category:"banhtỉamisu", name: 'Tiramisu Cafe',   thum:  'caphe.jpg', oldprice:"600.000", price: "470.000" },
        ]
        }
    },
    methods:{
        addToCart(shop) {
            this.$emit('addToCart', shop);
            alert(`${shop.name} đã được thêm vào giỏ hàng!`);
        }
    },

}
</script>
<style>

.banner img{
    width: 100%;
}
.banner p{
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: #4f2d2b;
    font-size: 100px;
}
.banner a{
    position: absolute;
    bottom: 30%;
    left: 10%;
    transform: translate(-50%, -50%);
}
</style>