<template>
  <div class="box">
    <table>
      <tr>
        <th>Tên sản phẩm</th>
        <th>Giá</th>
        <th>Số lượng</th>
      </tr>
      <tr v-for="(product, index) in products" :key="index">
        <td>{{ product.name }}</td>
        <td>{{ product.price }}</td>
        <td>{{ product.quantity }}</td>
      </tr>
    </table>

    <table>
      <tr>
        <th>Tên sản phẩm</th>
        <th>Giá</th>
        <th>Số lượng</th>
      </tr>
      <tr v-for="(product, index) in productComputed" :key="index">
        <td>{{ product.name }}</td>
        <td>{{ product.price }}</td>
        <td>{{ product.quantity }}</td>
      </tr>
    </table>

    <input type="text" v-model="text" placeholder="Nhập text">
    <p>Nội dung: {{ textComputed }}</p>

<!--    <input type="text" v-model="age" placeholder="Nhập số tuổi">-->
<!--    <p v-if="age "></p>-->
  </div>
</template>

<script>
export default {
  name: "KienThucB2",
  computed: {
    productComputed() {
      return this.products.filter(product => product.price > 17000000)
    },
    textComputed() {
      return this.text.toUpperCase()
    }
  },
  data() {
    return {
      text: "",
      age: 0,
      products: [
        {
          name: 'iPhone 12 Pro Max Chính Hãng',
          image: 'https://cdn.cellphones.com.vn/media/catalog/product/cache/1/image/9df78eab33525d08d6e5fb8d27136e95/p/h/photo_2020-10-13_22-12-24.jpg_1_2.png',
          price: 32990000,
          quantity: 566,
          isAvailable: true
        },
        {
          name: 'iPhone 12 Chính Hãng (VN/A)',
          image: '',
          price: 21790000,
          quantity: 123,
          isAvailable: true
        },
        {
          name: 'iPhone 11 Chính hãng',
          image: 'https://cdn.cellphones.com.vn/media/catalog/product/cache/1/image/9df78eab33525d08d6e5fb8d27136e95/_/0/_0004_layer_5.jpg',
          price: 16690000,
          quantity: 0,
          isAvailable: false
        },
        {
          name: 'Apple iPhone XR 64GB Chính hãng(VN/A)',
          image: 'https://cdn.cellphones.com.vn/media/catalog/product/cache/1/image/9df78eab33525d08d6e5fb8d27136e95/i/p/iphone-xr_5_.jpg',
          price: 12190000,
          quantity: 1023,
          isAvailable: true
        },
        {
          name: 'iPhone 11 Pro Max Chính hãng(VN/A)',
          image: '',
          price: 26500000,
          quantity: 45,
          isAvailable: true
        }
      ],
    }
  }
}
</script>

<style scoped>
table, th, td {
  border:1px solid black;
  border-spacing: unset;
}
th, td {
  width: 400px;
}

table {
  margin-bottom: 100px;
}
</style>