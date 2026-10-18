<template>
  <div id="app">
    <el-container>
      <el-header style="font-size: 40px;background-color: rgb(238, 241, 246);text-align: left;padding-left: 20px;">Quiz后台管理</el-header>
      <el-container>
        <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
          <el-menu
            :default-openeds="['1']"
            :default-active="$route.path"
            background-color="rgb(238, 241, 246)"
            text-color="#303133"
            @select="handleMenuSelect"
          >
            <el-submenu index="1">
              <template slot="title">管理选项</template>
              <el-menu-item index="/user" :class="{clickedItem: clickedList.includes('/user')}">
                <router-link to="/user">用户管理</router-link>
              </el-menu-item>
              <el-menu-item index="/question" :class="{clickedItem: clickedList.includes('/question')}">
                <router-link to="/question">题目管理</router-link>
              </el-menu-item>
            </el-submenu>
          </el-menu>
        </el-aside>
        <el-main>
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "hello vue",
      clickedList: [] // 用来存放已经点击过的路由，一旦存入永久保留
    };
  },
  methods: {
    handleMenuSelect(index) {
      // 判断：如果不在数组里面，才加入，加入后永远保留
      if (!this.clickedList.includes(index)) {
        this.clickedList.push(index);
      }
    }
  }
};
</script>

<style>
.el-header,
.el-footer {
  background-color: #b3c0d1;
  color: #333;
  line-height: 60px;
}

.el-aside {
  background-color: #d3dce6;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
}

/* ========== 【未点击状态】全部强制统一深灰色，覆盖所有默认状态 ========== */
.el-menu-item a,
.el-menu-item a:link,
.el-menu-item a:visited,
.el-menu-item.is-active a,
.el-menu-item.is-active a:link,
.el-menu-item.is-active a:visited{
  text-decoration: underline;
  color: #346ad4 !important;
}

/* ========== 【点击过后】永久紫色，只有添加clickedItem类才生效 ========== */
.el-menu-item.clickedItem a,
.el-menu-item.clickedItem a:link,
.el-menu-item.clickedItem a:visited {
  color: #9C88FF !important;
}
</style>