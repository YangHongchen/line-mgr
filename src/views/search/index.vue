<template>
  <div class="app-container">
    <div class="local-search">
      <div class="search">
        <div style="margin: 15px 0px;">
          <el-input v-model="searchVal" placeholder="请输入内容" class="input-with-select">
            <el-button slot="append" icon="el-icon-search" />
          </el-input>
        </div>
      </div>

      <el-table :data="list" style="width: 100%">
        <el-table-column
          prop="name"
          label="商品名"
          width="280"
          sortable
        />
        <el-table-column
          prop="price"
          label="单价"
          width="180"
          sortable
        />
        <el-table-column
          prop="sales"
          label="销量"
          sortable
        />
      </el-table>
    </div>
  </div>

</template>

<script>
export default {
  data() {
    return {
      goodsList: [
        // 假数据
        { name: '三星Galaxy Note8', price: 5200, sales: 2.6 },
        { name: 'iphone5s', price: 2500, sales: 2.2 },
        { name: 'iphone6', price: 2800, sales: 1.6 },
        { name: 'iphone6s', price: 3200, sales: 2.9 },
        { name: 'iphone7', price: 3800, sales: 12.6 },
        { name: 'iphone7plus', price: 4200, sales: 2.1 },
        { name: 'iphone8', price: 5500, sales: 10.6 },
        { name: '华为', price: 4600, sales: 7.6 },
        { name: '小米', price: 1200, sales: 32.6 },
        { name: 'OPPOR11', price: 3000, sales: 1.2 },
        { name: 'vivoX20', price: 3250, sales: 2.9 }
      ],
      searchVal: '', // 默认输入为空
      letter: '', // 默认不排序
      original: false // 默认从小到大排列
    }
  },
  computed: {
    list: function() {
      // eslint-disable-next-line no-unused-vars
      var _this = this
      var arrByZM = []
      for (var i = 0; i < this.goodsList.length; i++) {
        if (this.goodsList[i].name.search(this.searchVal) !== -1) {
          arrByZM.push(this.goodsList[i])
        }
      }
      // 自己实现的排序，elment-ui 表格自带排序功能，暂时不用
      // if (this.letter !== '') {
      //   arrByZM.sort(function(a, b) {
      //     if (_this.original) {
      //       return b[_this.letter] - a[_this.letter]
      //     } else {
      //       return a[_this.letter] - b[_this.letter]
      //     }
      //   })
      // }
      // 一定要记得返回筛选后的数据
      return arrByZM
    }
  },
  methods: {
    // orderFn: function(letter, original) {
    //   this.letter = letter // 排序字段 price or sales
    //   this.original = original // 排序方式  up or down
    // }
  }
}
</script>

<style scoped>
</style>
