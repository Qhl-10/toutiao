<template>
    <el-row align="middle" type="flex" class="layout-header">
      <el-col class="left" :span="12">
          <i class="el-icon-s-order"></i>
          <span>云联科技有限公司</span>
      </el-col>
      <el-col class="right" :span="12">
          <el-row type="flex" justify="end" align="middle">
            <img src="../../assets/img/avatar.jpg" style="margin-right:10px;">
            <el-dropdown>
                <span>相善若水</span>
                <el-dropdown-menu slot="dropdown">
                    <el-dropdown-item>个人信息</el-dropdown-item>
                    <el-dropdown-item>git地址</el-dropdown-item>
                    <el-dropdown-item>退出</el-dropdown-item>
                </el-dropdown-menu>
            </el-dropdown>
          </el-row>
      </el-col>
    </el-row>
</template>
<style lang='less' scoped>
    .layout-header{
        height: 60px;
    }
    .layout-header>.left>i{
        font-size: 20px;
    }
</style>
