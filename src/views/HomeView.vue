<template>
  <div>
    <!-- 整个页面 -->
    <el-container>
      <!-- 顶部 -->
      <el-header class="layout-header">
        <h1>酷鲨商城运营管理平台</h1>
      </el-header>
      <!-- 下半部分 -->
      <el-container class="layout-body">
        <!-- 下半部分的左侧边栏 -->
        <el-aside class="layout-aside">
          <el-menu
              router
              default-active="2"
              class="el-menu-vertical-demo"
              background-color="#9ed3d7"
              text-color="#fff"
              active-text-color="#fff">
            <el-menu-item index="/sys-admin/index">
              <i class="el-icon-s-home"></i>
              <span slot="title">首页</span>
            </el-menu-item>
            <el-submenu index="9">
              <template slot="title">
                <i class="el-icon-s-tools"></i>
                <span>临时页面</span>
              </template>
              <el-menu-item index="/sys-admin/temp/album/add-new">
                <i class="el-icon-circle-plus"></i>
                <span slot="title">添加相册</span>
              </el-menu-item>
              <el-menu-item index="/sys-admin/temp/brand/add-new">
                <i class="el-icon-circle-plus"></i>
                <span slot="title">添加品牌</span>
              </el-menu-item>
              <el-menu-item index="/sys-admin/temp/brand/list">
                <i class="el-icon-s-operation"></i>
                <span slot="title">品牌列表</span>
              </el-menu-item>
            </el-submenu>
            <el-submenu index="2">
              <template slot="title">
                <i class="el-icon-s-goods"></i>
                <span>商品管理</span>
              </template>
              <el-menu-item index="/sys-admin/product/spu-management">
                <i class="el-icon-s-grid"></i>
                <span slot="title">SPU台账</span>
              </el-menu-item>
              <el-menu-item index="/sys-admin/product/spu-add-new">
                <i class="el-icon-circle-plus"></i>
                <span slot="title">新增SPU</span>
              </el-menu-item>
              <el-menu-item index="/sys-admin/product/album-management">
                <i class="el-icon-picture"></i>
                <span slot="title">相册管理</span>
              </el-menu-item>
              <el-menu-item index="/sys-admin/product/category-management">
                <i class="el-icon-s-unfold"></i>
                <span slot="title">商品类别</span>
              </el-menu-item>
              <el-menu-item index="/sys-admin/product/attribute-template-management">
                <i class="el-icon-s-flag"></i>
                <span slot="title">属性模版</span>
              </el-menu-item>
              <el-menu-item index="/sys-admin/product/brand-management">
                <i class="el-icon-s-data"></i>
                <span slot="title">品牌管理</span>
              </el-menu-item>
            </el-submenu>
            <el-submenu index="3">
              <template slot="title">
                <i class="el-icon-s-order"></i>
                <span>订单管理</span>
              </template>
            </el-submenu>
            <el-submenu index="4">
              <template slot="title">
                <i class="el-icon-s-ticket"></i>
                <span>营销管理</span>
              </template>
            </el-submenu>
            <el-submenu index="5">
              <template slot="title">
                <i class="el-icon-s-shop"></i>
                <span>商家管理</span>
              </template>
            </el-submenu>
            <el-submenu index="6">
              <template slot="title">
                <i class="el-icon-s-check"></i>
                <span>权限管理</span>
              </template>
            </el-submenu>
          </el-menu>
        </el-aside>
        <!-- 下半部分的右侧主体 -->
        <el-main>
          <!-- 将由其它视图组件显示右侧的主体部分 -->
          <router-view/>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<style>
body {
  background-color: #fff !important;
}

.layout-header {
  background: #72bfc5;
  line-height: 60px;
  font-size: 16px;
}

.layout-body {
  position: absolute;
  top: 60px;
  bottom: 0;
  left: 0;
  right: 0;
}

.layout-aside {
  background: #9ed3d7;
}

.layout-aside i {
  color: #fff;
}

.el-menu-item.is-active {
  background-color: #79a1a4 !important;
}
</style>