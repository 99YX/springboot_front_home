<template>
  <div class="home">
    <el-container style="height: 100vh; border: 1px solid #eee">
                <!--   overflow: hidden 宽度溢出   -->
                <!--      overflow-x: hidden 侧边栏溢出部分隐藏-->
<!-- 侧边栏宽度根据收缩后动态获取     -->
      <el-aside :width="sideWidth+'px'" style="background-color: rgb(238, 241, 246);height: 100vh;overflow: hidden"  >
        <el-menu :default-openeds="['1', '3']" style="height: 100vh;overflow-x: hidden"

                 background-color="rgb(48, 65, 86)"
                 text-color="#fff"
                 active-text-color="#ffd04b"
                 :collapse-transition="false"
                 :collapse="isCollapse"



        >
          <!--       侧边栏背景色       background-color="rgb(48,65,86)"    -->
          <el-submenu index="1">
            <template slot="title"><i class="el-icon-message"></i>导航一</template>
            <el-menu-item-group>
              <template slot="title">分组一</template>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="1-3">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="1-4">
              <template slot="title">选项4</template>
              <el-menu-item index="1-4-1">选项4-1</el-menu-item>
            </el-submenu>
          </el-submenu>
          <el-submenu index="2">
            <template slot="title"><i class="el-icon-menu"></i>导航二</template>
            <el-menu-item-group>
              <template slot="title">分组一</template>
              <el-menu-item index="2-1">选项1</el-menu-item>
              <el-menu-item index="2-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="2-3">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="2-4">
              <template slot="title">选项4</template>
              <el-menu-item index="2-4-1">选项4-1</el-menu-item>
            </el-submenu>
          </el-submenu>
          <el-submenu index="3">
            <template slot="title"><i class="el-icon-setting"></i>导航三</template>
            <el-menu-item-group>
              <template slot="title">分组一</template>
              <el-menu-item index="3-1">选项1</el-menu-item>
              <el-menu-item index="3-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="3-3">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="3-4">
              <template slot="title">选项4</template>
              <el-menu-item index="3-4-1">选项4-1</el-menu-item>
            </el-submenu>
          </el-submenu>
        </el-menu>
      </el-aside>

      <el-container>
        <el-header style=" font-size: 12px;border-bottom: 1px solid #cccccc;line-height: 60px;display: flex">
         <!--   收缩按钮      -->
          <div style="flex: 1;font-size: 18px">
            <!--   cursor: pointer 鼠标小手         -->
          <span :class="collapseBtnClass" style="font-size: 18px" @click="collapse"></span>
          </div>
          <el-dropdown  style="width: 80px">
            <span>王小虎</span><i class="el-icon-arrow-down" style="margin-left: 5px;pxcursor: pointer;"></i>
            <i class="el-icon-setting" style="margin-right: 15px"></i>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>个人信息</el-dropdown-item>

              <el-dropdown-item>退出</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>

        </el-header>

        <el-main>
          <el-table :data="tableData" :row-class-name="tableRowClassName">
            <el-table-column prop="date" label="日期" width="140">
            </el-table-column>
            <el-table-column prop="name" label="姓名" width="120">
            </el-table-column>
            <el-table-column prop="address" label="地址">
            </el-table-column>
          </el-table>
        </el-main>
      </el-container>
    </el-container>
  </div>

</template>
<style>
.el-header {
  background-color: #B3C0D1;
  color: #333;
  line-height: 60px;
}

.el-aside {
  color: #333;
}
.el-table .warning-row {
  background: oldlace;
}

.el-table .success-row {
  background: #f0f9eb;
}
</style>
<script>
// @ is an alias to /src


export default {
  name: 'HomeView',

  data() {
    const item = {
      date: '2016-05-02',
      name: '王小虎',
      address: '上海市普陀区金沙江路 1518 弄'
    };
    return {
      tableData: Array(10).fill(item),
      /*折叠属性默认是开启状态*/
      isCollapse:false,
      /*收缩按钮名称*/
      collapseBtnClass:'el-icon-s-fold',
      /*侧边栏宽度默认是200*/
      sideWidth:200
    }

  },
  /*方法*/
  methods: {
    tableRowClassName({row, rowIndex}) {
      if (rowIndex === 1) {
        return 'warning-row';
      } else if (rowIndex === 3) {
        return 'success-row';
      }
      return '';
    },
    /*折叠效果*/
    collapse(){
      /*点击后取反*/
      this.isCollapse=!this.isCollapse
      /*如果开启状态代表折叠了,则修改侧边栏宽度是64px*/
      if(this.isCollapse)
      {

        //el-menu--collapse 折叠后宽度是64px
        this.sideWidth=64


      }

    }
  }


}
</script>
