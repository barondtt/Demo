<template>
  <div class="container">
    <div class="productList">
      <table>
        <tr>
          <th>STT</th>
          <th>Sản phẩm</th>
          <th>Giá</th>
          <th>Số lượng</th>
          <th>Trạng thái</th>
          <th>Hành động</th>
        </tr>
        <tr v-for="(product, index) in products" :key="index">
          <td class="textCenter">
            {{ index + 1 }}
          </td>
          <td>
            <img :src="product.image" alt="" class="imgProduct" v-if="product.image">
            <img src="../../assets/logo.png" alt="" class="imgProduct" v-else>
            {{ product.name }}
          </td>
          <td>
            {{ formatPrice(product.price) }}
          </td>
          <td class="textCenter">
            {{ product.quantity }}
          </td>
          <td class="textCenter">
            <span v-if="product.quantity > 0">Còn hàng</span>
            <span v-else>Hết hàng</span>
          </td>
          <td>
            <button @click="addToCard(product)">Thêm giỏ hàng</button>
          </td>
        </tr>
      </table>
    </div>
    <div class="cartWrap">
      <div class="title">Giỏ hàng</div>
      <div v-if="cartProducts.length <= 0">
        Không có sản phẩm nào được thêm vào giỏ
      </div>
      <div v-else>
        <div v-for="(product, index) in cartProducts" :key="index">
          <img :src="product.image" alt="" class="imgProduct" v-if="product.image">
          <img src="../../assets/logo.png" alt="" class="imgProduct" v-else>
          {{ product.name }}
          <input type="text" v-model="product.quantity">
          <buton @click="removeItem(index)">Xóa</buton>
        </div>
      </div>

      <div>Tổng tiền: {{totalComputed}}</div>
    </div>

  </div>
</template>

<script>
export default {
  name: "BT2Buoi2",
  data() {
    return {
      products: [
        {
          id: 1,
          name: 'iPhone 12 Pro Max Chính Hãng',
          image: 'https://product.hstatic.net/1000340016/product/iphone-12-mini-red-select-2020_684ae3ca65004da18be7d151f3c9b222.png',
          price: 32990000,
          quantity: 566,
        },
        {
          id: 2,
          name: 'iPhone 12 Chính Hãng (VN/A)',
          image: '',
          price: 21790000,
          quantity: 123,
        },
        {
          id: 3,
          name: 'iPhone 11 Chính hãng',
          image: 'https://product.hstatic.net/1000340016/product/iphone-12-mini-red-select-2020_684ae3ca65004da18be7d151f3c9b222.png',
          price: 16690000,
          quantity: 0,
        },
        {
          id: 4,
          name: 'Apple iPhone XR 64GB Chính hãng(VN/A)',
          image: 'https://product.hstatic.net/1000340016/product/iphone-12-mini-red-select-2020_684ae3ca65004da18be7d151f3c9b222.png',
          price: 12190000,
          quantity: 1023,
        },
        {
          id: 5,
          name: 'iPhone 11 Pro Max Chính hãng(VN/A)',
          image: '',
          price: 26500000,
          quantity: 6,
        }
      ],
      cartProducts: [],
      total: 0
    }
  },
  computed: {
    totalComputed() {
      let result = 0
      this.cartProducts.map(product => {
        result += product.quantity * product.price
      })

      return this.formatPrice(result)
    }
  },
  methods: {
    formatPrice(price) {
      return price.toString().replace(/(\d)(?=(\d\d\d)+(?!\d))/g, "$1.") + ' đ'
    },
    formatProductName(name = '') {
      console.log(name)
    },
    addToCard(product) {
      if (product.quantity <= 0) {
        alert("Sản phẩm hết hàng")
        return false
      }

      let cart = this.cartProducts.filter(function (item) {
        return item.id === product.id
      })
      if (cart.length > 0) {
        let indexCart = this.cartProducts.findIndex(function (item) {
          return item.id === product.id
        })

        if (indexCart !== -1) {
          this.cartProducts[indexCart].quantity = Number(this.cartProducts[indexCart].quantity + 1)
        }
      } else {
        let data = product
        data.quantity = 1
        data.name = data.name.slice(0, 25) + "..."
        this.cartProducts.push(data)
      }
    },
    removeItem(index) {
      this.cartProducts.splice(index, 1)
    }
  }
}
</script>

<style scoped lang="scss">
$colorStroke: #d8e0ea;
$colorMain: #0080dd;
$colorDefault: #253036;
$colorGreen: #39cd74;
$colorRed: #f54b5e;
$colorTableHeader: #f2f6fe;
$colorWhite: #fff;

.container {
  height: 100vh;
  padding: 24px;
  color: $colorDefault;
  display: flex;
  align-items: flex-start;

  .productList {
    .textCenter {
      text-align: center;
    }

    .textGreen {
      color: $colorGreen;
    }

    .textRed {
      color: $colorRed;
    }

    .textMain {
      color: $colorMain;
    }

    table {
      border: 1px solid $colorStroke;
      border-spacing: 0;
      width: 900px;

      th {
        background: $colorTableHeader;
        padding: 14px;
        border-right: 1px solid $colorStroke;
        border-bottom: 1px solid $colorStroke;
      }

      td {
        text-align: left;
        padding: 12px;
        font-size: 14px;
        border-right: 1px solid $colorStroke;
      }

      .productNameWrap {
        display: flex;
        align-items: center;

        img {
          margin-right: 8px;
          width: 40px;
          height: 40px;
        }
      }

      .addToCartButton {
        background: $colorMain;
        border: unset;
        font-size: 14px;
        font-weight: bold;
        color: $colorWhite;
        width: 120px;
        height: 40px;
        border-radius: 5px;
        cursor: pointer;
      }
    }
  }

  .cartWrap {
    border: 1px solid $colorStroke;
    width: 500px;
    height: 500px;
    margin-left: 20px;
    padding: 24px;
    position: relative;

    .title {
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 20px;
    }

    .cartEmpty {
      text-align: center;
      margin-top: 100px;
    }

    .cartProductWrap {
      height: 60px;
      border-bottom: 1px solid $colorStroke;
      display: flex;
      align-items: center;
      justify-content: space-between;

      .cartProductNameWrap {
        display: flex;
        align-items: center;

        img {
          margin-right: 8px;
          width: 40px;
          height: 40px;
        }
      }

      .actions {
        display: flex;
        align-items: center;

        .quantityChangeInput {
          width: 80px;
          height: 30px;
          margin-right: 12px;
          border: 1px solid $colorStroke;
        }

        .removeFromCartButton {
          width: 60px;
          height: 30px;
          background: $colorRed;
          border: unset;
          border-radius: 5px;
          color: $colorWhite;
          cursor: pointer;
        }
      }
    }

    .cartTotal {
      position: absolute;
      bottom: 0;
      right: 0;
      padding: 24px;
      color: $colorRed;
      font-size: 20px;
      font-weight: bold;
    }
  }
}

.imgProduct {
  width: 50px;
  height: 50px;
}
</style>