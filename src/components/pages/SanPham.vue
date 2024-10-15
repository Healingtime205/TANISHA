<template>
    <div>
        <div class="khung">
            <div>
                <label for="category">Phân loại:</label>
                <select class="pick" v-model="selectedCategory">
                    <option value="all">Tất cả</option>
                    <option value="banhkem">Bánh kem</option>
                    <option value="banhlava">Bánh lava</option>
                    <option value="banhtiramisu">Bánh Tiramisu</option>
                </select>
            </div>
            <div class="product-items">
                <div class="product-item" v-for="sp in filteredsps" :key="sp.id">
                    <img :src="require(`@/assets/pic/${sp.thum}`)" alt="">
                    <div class="product-item-text">
                        <h4>{{ sp.name }}</h4>
                        <p>{{ sp.description }}</p>
                        <p><span>Giá: {{ sp.price }}</span><sup>đ</sup></p>
                    </div>
                    <button @click="addToCart(sp)"><i class="fa-solid fa-cart-plus"></i> Thêm vào giỏ hàng</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default{
        name:'SanPham',
        props:['products'],
        data(){
            return{
                selectedCategory: 'all',
                sps:[    
                    { id: 1,category:"banhkem", name: 'Bánh Kem Dâu', description: 'Bánh kem với vị dâu ngọt ngào.', thum:  'kd.jpg', price: "200.000" },
                    { id: 2,category:"banhkem", name: 'Bánh Kem Socola', description: 'Bánh kem hương socola béo ngậy.', thum:  'ks.webp', price: "250.000" },
                    { id: 3,category:"banhkem", name: 'Bánh Kem Trái Cây', description: 'Bánh kem với nhiều loại trái cây tươi.', thum:  'ktc.jpg', price: "300.000" },
                    { id: 4,category:"banhkem", name: 'Bánh Kem Matcha', description: 'Bánh kem với vị matcha thơm ngon.', thum:  'kmc.jpg', price: "220.000" },
                    { id: 5,category:"banhkem", name: 'Bánh Kem Sầu Riêng', description: 'Bánh kem với hương vị sầu riêng đặc trưng.', thum:  'ksr.jpg', price: "280.000" },
                    { id: 6,category:"banhkem", name: 'Bánh Kem Chanh Dây', description: 'Bánh kem với hương vị chanh dây tươi mát.', thum:  'kcd.jpg', price: "260.000" },
                    { id: 7,category:"banhkem", name: 'Bánh Kem Dừa', description: 'Bánh kem với vị dừa béo ngậy và thơm ngon.', thum:  'kdua.jpg', price: "230.000" },
                    { id: 8, category:"banhlava", name: 'Bánh Lava Socola', description: 'Bánh lava với nhân socola chảy.', thum: 'scllv.png'  , price: "350.000" },
                    { id: 9, category:"banhlava", name: 'Bánh Lava Matcha', description: 'Bánh lava với nhân thơm hương matcha.', thum: 'mclv.jpg'  , price: "400.000" },
                    { id: 11, category:"banhlava", name: 'Bánh Lava Chanh dây', description: 'Bánh lava với hương vị chanh dây đặc trưng.', thum:  'lvcd.jpg', price: "420.000" },
                    { id: 12, category:"banhlava", name: 'Bánh Lava Bơ', description: 'Bánh lava với nhân bơ béo ngậy', thum:  'lvb.jpg', price: "380.000" },
                    { id: 13, category:"banhlava", name: 'Bánh Lava Dâu tằm', description: 'Bánh lava với nhân chua ngọt .', thum:  'lvdt.jpg', price:" 390.000" },
                    { id: 14, category:"banhtiramisu", name: 'Tiramisu Matcha', description: 'Bánh tiramisu với hương vị Matcha đậm đà.', thum: 'matcha.jpg'  , price: "450.000" },
                    { id: 15, category:"banhtiramisu", name: 'Tiramisu Chocolate', description: 'Bánh tiramisu với hương vị socola.', thum: 'scl.png'  , price: "500.000" },
                    { id: 16, category:"banhtiramisu", name: 'Tiramisu Trái Cây', description: 'Bánh tiramisu với nhiều loại trái cây tươi.', thum:  'traicay.jpg', price: "480.000" },
                    { id: 17, category:"banhtiramisu", name: 'Tiramisu Cafe', description: 'Bánh tiramisu với hương vị cà phê thơm ngon.', thum:  'caphe.jpg', price: "470.000" },
                    { id: 18, category:"banhtiramisu", name: 'Tiramisu Vanila', description: 'Bánh tiramisu với hương vị vanila nhẹ nhàng.', thum:  'vani.jpg', price: "460.000" },                 
                ]
            }
        },
        methods:{
            addToCart(sp) {
                this.$emit('addToCart', sp);
            }
        },
        computed:{
            filteredsps() {
                if (this.selectedCategory === 'all') {
                    return this.sps;
                }
                    return this.sps.filter(sp => sp.category === this.selectedCategory);
            }
        },
    }
</script>
<style>
.khung{
    padding: 20px 10px;
}
h1{
    text-align: center;
    color: #FF5622;
}
.pick{
    margin: 5px;
    border-radius: 5px;
}
.product-items {
    display: flex;
    flex-wrap: wrap;
    gap: 45px;
}
.product-item {
    width: 20%;
    height: 400px;
    border:10px #FF5622;
    background-color: #fff;
    padding: 12px;
    margin-bottom: 12px;
    text-align: center;
    white-space: pre-wrap;
    overflow: hidden;
}

.product-item img {
    width: 100%;
    height: 60%;
    margin-bottom: 20px;
    object-fit: cover;
} 
.product-item-text h4 {
    font-size: 1rem;
}
.product-item button {
    margin-bottom: 12px;
    height: 30px;
    padding: 0 12px;
    cursor: pointer;
    border: none;
    border-radius: 5px;
}
.product-item button:hover {
    background-color: rgb(203, 236, 119);
    transform: translateY(-5px);
    box-shadow: 0px 5px 10px rgba(90, 151, 0, 0.908);
}
.btn-added {
    background-color: gray;
    color: white;
    border: none;
    cursor: not-allowed;
}

</style>