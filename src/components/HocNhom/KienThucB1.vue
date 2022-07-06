<template>
  <div class="box">
    <h1>Các hàm xử lý mảng và chuỗi</h1>
<!--    <button @click="handleConcat()">Click</button>-->
  </div>
</template>

<script>
export default {
  name: "KienThucB1",
  data() {
    return {
      array_1: [1, 2, 3, 4],
      array_2: [5, 6, 7, 8],
      array_3: [9, 10, 11, 12],

      words: [
        'spray',
        'limit',
        'elite',
        'exuberant',
        'destruction',
        'present'
      ]
    }
  },
  methods: {
    // Xử lý mảng
    handleConcat() {
      /*
      * concat() dùng để nối 2 hay nhiều mảng với nhau
      * concat() KHÔNG làm thay đổi mảng ban đầu mà trả về một mảng mới sau khi nối
      */
      //
      // console.log(this.array_1)
      // console.log(this.array_2)
      // Nối 2 mảng
      // let result = this.array_1.concat(this.array_2)

      // Nối nhiều mảng
      let resultMultiple = this.array_1.concat(this.array_2, this.array_3)
      //
      // console.log(result)
      console.log(resultMultiple)
    },
    handleFilter() {
      /*
      * filter() dùng để lọc ra các phần tử trong mảng thoả mãn một điều kiện nào đó
      * filter() KHÔNG làm thay đổi mảng ban đầu mà trả về một mảng mới sau sau khi lọc
      * filter() trả về một mảng RỖNG nếu không có phần tử nào thỏa mãn điều kiện
      */

      // cú pháp 1
      // let result = this.words.filter(word => word.length > 6)
      //
      // // cú pháp 2
      // let result_1 = this.words.filter(function (word) {
      //   return word.length > 6
      // })

      // Trả về mảng rỗng nếu không thỏa mãn điều kiện
      let resultEmpty = this.words.filter(word => word.length > 15)

      // console.log(result)
      // console.log(result_1)
      console.log(resultEmpty)
    },
    handleFind() {
      /*
      * find() dùng để lọc ra các phần tử trong mảng thoả mãn một điều kiện nào đó
      * find() trả về phần tử đầu tiên thỏa mãn điều kiện trong mảng
      * find() trả về undefined nếu không tìm thấy
      * find() KHÔNG làm thay đổi mảng ban đầu
      */
      let result = this.array_1.find(el => el > 2)

      let result_1 = this.array_1.find(function (el) {
        return el > 2
      })

      console.log(result)
      console.log(result_1)
    },
    handleIncludes() {
      /*
      * includes() kiểm tra xem phần tử đã cho có tồn tại trong mảng hay không
      * includes() KHÔNG làm thay đổi mảng ban đầu
      * includes() trả về kiểu Boolean: true nếu tìm thấy hoặc false nếu không tìm thấy
      */

      // let result = this.array_1.includes(3)
      // let result_1 = this.array_1.includes(6)
      //
      // console.log(result)
      // console.log(result_1)

      let arr = ["a", "b", "c", "d", "e"]

      console.log(arr.includes("k"))
    },
    handleJoin() {
      /*
      * join() dùng để tạo ra một chuỗi mới bằng cách nối tất cả các phần tử của mảng
      */

      // Mặc định các các từ được nối với nhau bằng dấu phẩy
      // let result = this.words.join()
      //
      // let result_1 = this.words.join(" - ")
      //
      //
      // console.log(result)
      // console.log(result_1)

      let arr = ["a", "b", "c", "d", "e"]

      console.log(arr.join("-"))
    },

    // Xóa phần tử cuối cùng của mảng
    handlePop() {
      /*
      * pop() dùng để xoá phần tử cuối cùng ra khỏi mảng
      * pop() làm thay đổi giá trị của mảng ban đầu
      */

      console.log(`Trước khi thay đổi: ${this.words}`)
      this.words.pop()

      console.log(`Sau khi thay đổi: ${this.words}`)
    },

    // Xóa phần tử đầu tiên trong mảng
    handleShift() {
      /*
      * shift() dùng để xoá phần tử đầu tiên ra khỏi mảng
      * shift() làm thay đổi giá trị của mảng ban đầu
      */

      console.log(`Trước khi thay đổi: ${this.words}`)
      this.words.shift()

      console.log(`Sau khi thay đổi: ${this.words}`)
    },

    // Thêm phần tử vào cuối mảng
    handlePush() {
      /*
      * push() giúp ta thêm một hoặc nhiều phần tử vào cuối mảng
      */

      // console.log(this.words)
      // this.words.push("Phần tử 1")
      // console.log(this.words)
      this.words.push("Phần tử 1", "Phần tử 2", "Phần tử 3")
      console.log(this.words)
    },

    // Thêm phần tử vào đầu mảng
    handleUnshift() {
      /*
      * unshift() giúp ta thêm một hoặc nhiều phần tử vào đầu mảng
      */

      console.log(this.words)
      this.words.unshift("Phần tử 1")
      console.log(this.words)
      this.words.unshift("Phần tử 1", "Phần tử 2", "Phần tử 3")
      console.log(this.words)
    },

    // Đảo ngược mảng
    handleReverse() {
      /*
      * reverse() dùng để đảo ngược mảng, phần tử đầu thành phần tử cuối và ngược lại
      */

      console.log(this.array_1)
      this.array_1.reverse()
      console.log(this.array_1)
    },

    // Xử lý chuỗi
    handleChartAt() {
      /*
      * Trả về ký tự ở vị trí đã chỉ định theo index
      */

      let word = "hello world"

      let result = word.charAt(6)

      console.log(result)
    },
    handleIndexOf() {
      /*
      * Dùng để tìm kiếm vị trí của chuỗi trong một chuỗi khác
      * Trả về vị trí đầu tiên được tìm thấy (bắt đầu từ vị trí được chỉ định tìm kiếm) hoặc trả về -1 nếu không tìm thấy
      */
      let word = "The quick brown abc fox jumps over the lazy dog. If the dog abc barked, was it really lazy?"

      // let result = word.indexOf("abc")

      /*
      * str.indexOf(searchValue, fromIndex)
      * searchValue: từ khóa để tìm kiếm
      * fromIndex: vị trí bắt đầu tìm kiếm
      */
      let result_1 = word.indexOf("abc", 17)

      // console.log(result)
      console.log(result_1)
    },
    handleLastIndexOf() {
      /*
      * Dùng để tìm kiếm vị trí của chuỗi trong một chuỗi khác
      * Trả về vị trí cuối cùng được tìm thấy (bắt đầu từ vị trí được chỉ định tìm kiếm) hoặc trả về -1 nếu không tìm thấy
      */
      let word = "The quick brown abc fox jumps over abc the lazy dog. If the dog abc barked, was it really lazy?"

      // let result = word.lastIndexOf("abc")

      /*
      * str.lastIndexOf(searchValue, fromIndex)
      * searchValue: từ khóa để tìm kiếm
      * fromIndex: vị trí bắt đầu tìm kiếm
      */
      let result_1 = word.lastIndexOf("abc", 16)

      // console.log(result)
      console.log(result_1)
    },
    handleReplace() {
      /*
      * Thay thế từ đầu tiên (phù hợp) trong chuỗi
      */
      let str = "The quick brown fox jumps over the fox lazy dog. If the DOG reacted, fox was it really lazy?"

      console.log(str.replace("fox", "AAA"))
    },
    handleReplaceAll() {
      /*
      * Thay thế tất cả các từ phù hợp trong chuỗi
      */
      let str = "The quick brown fox jumps over the fox lazy dog. If the DOG reacted, fox was it really lazy?"

      console.log(str.replaceAll("fox", "BBB"))
    },
    handleSlice() {
      let str = "The quick brown fox jumps over the lazy dog."

      console.log(str.slice(4));     // lấy từ index = 4 tới str.length
      console.log(str.slice(4, 19));  // lấy từ index = 4 tới index = 19
      console.log(str.slice(-4));     // lấy từ index = -4 tới str.length
      console.log(str.slice(-9, -5)); // lấy từ index = -9 tới index = -5
    },
    handleSplit() {
      /*
      * Cắt chuỗi thành mảng dựa theo điều kiện
      */

      let str = "hello world"

      let result = str.split()
      let result_1 = str.split("")
      let result_2 = str.split("", 3)

      console.log(result)
      console.log(result_1)
      console.log(result_2)
    },
    handleToLowerCase() {
      /*
      * Chuyển toàn bộ chuỗi thành chữ thường
      */
      let str = "The quiCk BrowN FoX jUMps oVEr thE lAzy DOg."

      let result = str.toLowerCase()

      console.log(result)
    },
    handleToUpperCase() {
      /*
      * Chuyển toàn bộ chuỗi thành chữ in hoa
      */
      let str = "The quiCk BrowN FoX jUMps oVEr thE lAzy DOg."

      let result = str.toUpperCase()

      console.log(result)
    },
    handleTrim() {
      /*
      * Loại bỏ khoảng trắng ở 2 đầu của chuỗi
      */

      let str = "   hello     world     "

      let result = str.trim()

      console.log(result)
    },
    handleTrimStart() {
      /*
      * Loại bỏ khoảng trắng ở đầu chuỗi
      */

      let str = "   hello     world     "

      let result = str.trimStart()

      console.log(result)
    },
    handleTrimEnd() {
      /*
      * Loại bỏ khoảng trắng ở cuối chuỗi
      */

      let str = "      hello     world     "

      let result = str.trimEnd()

      console.log(result)
    },
  },
  mounted() {
    // this.handleConcat()
    // this.handleFilter()
    // this.handleFind()
    // this.handleIncludes()
    // this.handleJoin()
    // this.handlePop()
    // this.handleShift()
    // this.handlePush()
    // this.handleUnshift()
    // this.handleReverse()


    // this.handleChartAt()
    // this.handleIndexOf()
    // this.handleLastIndexOf()
    // this.handleReplace()
    // this.handleReplaceAll()
    // this.handleSlice()
    // this.handleSplit()
    // this.handleToLowerCase()
    // this.handleToUpperCase()
    // this.handleTrim()
    // this.handleTrimStart()
    // this.handleTrimEnd()
  }
}
</script>

<style scoped>

</style>