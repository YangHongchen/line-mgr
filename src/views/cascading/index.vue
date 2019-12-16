<template>
  <div class="cascading">
    <el-select v-model="i" placeholder="请选择省份">
      <el-option
        v-for="(item,index) of provinces"
        :key="index"
        :label="item.label"
        :value="index"
      />
    </el-select>

    <el-select v-model="j" placeholder="请选择城市">
      <el-option
        v-for="(item,index) of cities[i]"
        :key="index"
        :label="item.label"
        :value="index"
      />
    </el-select>

    {{ provinceId }} === {{ cityId }}

  </div>
</template>

<script>
export default {
  data () {
    return {
      i: 0,
      j: 0,
      k: 0,
      provinces: [
        {
          value: '1',
          label: '北京'
        },
        {
          value: '2',
          label: '山东'
        },
        {
          value: '3',
          label: '河北'
        },
        {
          value: '4',
          label: '湖北'
        }
      ],
      cities: [
        [
          {
            value: '11',
            label: '北京市'
          }
        ],
        [
          {
            value: '21',
            label: '济南'
          }, {
            value: '22',
            label: '青岛'
          }, {
            value: '23',
            label: '德州'
          }
        ],
        [
          {
            value: '31',
            label: '石家庄'
          }, {
            value: '32',
            label: '保定'
          }, {
            value: '33',
            label: '廊坊'
          }, {
            value: '34',
            label: '承德'
          }
        ],
        [
          {
            value: '41',
            label: '武汉'
          }, {
            value: '42',
            label: '随州'
          }, {
            value: '43',
            label: '鄂州'
          }, {
            value: '44',
            label: '宜昌'
          }
        ]
      ]
    }
  },
  computed: {
    // 省份 ID
    provinceId: function () {
      return this.provinces[this.i].value
    },
    // 选择城市
    cityId: function () {
      return this.cities[this.i][this.j].value
    }
  },
  watch: {
    i () { this.j = 0 }
  }
}
</script>

<style scoped>
</style>
