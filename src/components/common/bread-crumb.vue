<template>
    <el-breadcrumb class="breadcrumb-container" separator=">">
        <el-breadcrumb-item v-for="item in levelList" :key="item.path">
        {{item.name}}
        </el-breadcrumb-item>
    </el-breadcrumb>
</template>
<script>
export default {
  name: 'Navbar',
  data () {
    return {
      levelList: []
    }
  },
  watch: {
    $route () {
      this.getBreadcrumb()
    }
  },
  created () {
    this.getBreadcrumb()
  },
  methods: {
    getBreadcrumb () {
      const Const = this.$route.const.filter(item => item.name)
      this.levelList = Const
    }
  }
}
</script>
