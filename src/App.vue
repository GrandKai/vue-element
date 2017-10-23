<template>
    <div id="app">
        <!--<img src="./assets/logo.png">-->
        <!--<h1>{{ msg }}</h1>-->
        <!--<el-button @click.native="startHacking">Yes!</el-button>-->

        <el-menu :default-active="activeIndex2" class="el-menu-demo" mode="horizontal" @select="handleSelect">
            <el-menu-item index="1">处理中心</el-menu-item>
            <el-submenu index="2">
                <template slot="title">我的工作台</template>
                <el-menu-item index="2-1">选项1</el-menu-item>
                <el-menu-item index="2-2">选项2</el-menu-item>
                <el-menu-item index="2-3">选项3</el-menu-item>
            </el-submenu>
            <el-menu-item index="3"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
        </el-menu>

        <el-row class="tac">
            <el-col :span="3">
                <h5>带 icon</h5>
                <el-menu default-active="2" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose"
                         :collapse="isCollapse">
                    <el-submenu index="1">
                        <template slot="title"><i class="el-icon-message"></i><span slot="title">导航一</span></template>
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
                            <el-menu-item index="1-4-1">选项1</el-menu-item>
                        </el-submenu>
                    </el-submenu>
                    <el-menu-item index="2"><i class="el-icon-menu"></i><span slot="title">导航二</span></el-menu-item>
                    <el-menu-item index="3"><i class="el-icon-setting"></i><span slot="title">导航三</span></el-menu-item>
                </el-menu>
            </el-col>
        </el-row>


        <el-radio-group v-model="isCollapse" style="margin-bottom: 20px;">
            <el-radio-button :label="false">展开</el-radio-button>
            <el-radio-button :label="true">收起</el-radio-button>
        </el-radio-group>
        <el-button plain @click="startHacking">可自动关闭</el-button>
        <el-button plain @click="open3">成功</el-button>
        <el-button plain @click="open4">警告</el-button>
        <el-button plain @click="open5">消息</el-button>
        <el-button plain @click="open6">错误</el-button>
    </div>
</template>

<script>
  export default {
    data() {
      return {
        isCollapse: true,
        msg: 'Want something new?',
        activeIndex: '1',
        activeIndex2: '1'
      }
    },

    methods: {
      startHacking() {
        const h = this.$createElement;
        this.$notify({
          title: '标题名称',
          message: h('i', {style: 'color: teal'}, '这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案'),
          duration: 2000
        })
      },
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      },
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      },
      open3(key, keyPath) {
        this.$notify({
          title: '成功',
            message: '这是一条成功的提示消息',
            type: 'success'
        });
      },
      open4(key, keyPath) {
        this.$notify({
          title: '警告',
          message: '这是一条警告的提示消息',
          type: 'warning'
        });
      },
      open5() {
        this.$notify.info({
          title: '消息',
          message: '这是一条消息的提示消息'
        });
      },

      open6() {
        this.$notify.error({
          title: '错误',
          message: '这是一条错误的提示消息'
        });
      }
    }
  }
</script>


<style>
    #app {
        font-family: Helvetica, sans-serif;
        text-align: center;
    }
</style>
