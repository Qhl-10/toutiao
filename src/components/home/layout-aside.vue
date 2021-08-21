<template>
    <div class="layout-aside">
        <div class="title">
            <img src="../../assets/img/logo_admin.png">
        </div>
        <el-menu background-color="#19549c" text-color="white"
            :default-active="this.$router.path"
            router>
          <el-menu-item index="/home">
            <i class="el-icon-s-home"></i>
            <span>首页</span>
          </el-menu-item>
          <el-submenu index="2">
            <template slot="title">
                <i class="el-icon-s-grid"></i>
                <span>内容管理</span>
            </template>
            <el-menu-item index="/home/publish">发布文章</el-menu-item>
            <el-menu-item index="/home/articles">内容列表</el-menu-item>
            <el-menu-item index="/home/comment">评论列表</el-menu-item>
            <el-menu-item index="/home/material">素材管理</el-menu-item>
          </el-submenu>
          <el-submenu index="3">
            <template slot="title">
                <i class="el-icon-chat-round"></i>
                <span>粉丝管理</span>
            </template>
            <el-menu-item index="/home/pricture">图文数据</el-menu-item>
            <el-menu-item index="/home/fansinfo">粉丝概况</el-menu-item>
            <el-menu-item index="/home/fanimg">粉丝画像</el-menu-item>
            <el-menu-item index="/home/fanlist">粉丝列表</el-menu-item>
          </el-submenu>
          <el-menu-item index="4">
            <i class="el-icon-user-solid"></i>
            <span>账户信息</span>
          </el-menu-item>
        </el-menu>
    </div>
</template>

<style lang="less" scoped>
    .layout-aside {
      background-color: #174f94;
      height: 100vh;
      width: 230px;
    }
    .layout-aside>.title{
        text-align: center;
        padding: 10px;
    }
    .layout-aside>.title>img{
        height: 35px;
    }
    .el-menu{
        border-right: #174f94;
    }
</style>
