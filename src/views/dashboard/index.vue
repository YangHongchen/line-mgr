<template>
  <div class="dashboard-container">
    <UploadExcel :on-success="handleSuccess" :before-upload="beforeUpload" />
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import UploadExcel from '@/components/UploadExcel/index'

export default {
  name: 'Dashboard',
  components: {
    // eslint-disable-next-line vue/no-unused-components
    UploadExcel
  },
  computed: {
    ...mapGetters(['name'])
  },
  methods: {
    beforeUpload(file) {
      console.log(file)
    },
    handleSuccess(res) {
      console.log(res)
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
