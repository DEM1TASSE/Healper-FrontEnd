<!--
描述：导航栏
作者：张泰圣、王若晗
-->

<template>
    <div style="margin-left:20px;">
        <img src="../../assets/healper.png" style="zoom:30%; object-fit: contain;"/>
    </div>
    <el-menu
        default-active="main"
        class="el-menu-vertical"
        router=true
        length=1000px
        @select="handleSelect"
    >
        <el-menu-item index="main">
            <el-icon><House /></el-icon>
            <span>首页</span>
        </el-menu-item>
        <el-sub-menu index="2">
        <template #title>
            <el-icon><ChatDotRound /></el-icon>
            <span>心理咨询</span>
        </template>
            <el-menu-item index="consultation">预约咨询</el-menu-item>
            <el-menu-item index="order">我的订单</el-menu-item>
        </el-sub-menu>
            <el-menu-item index="scale">
            <el-icon><Notebook /></el-icon>
            <span>心理测评</span>
            </el-menu-item>
            <el-sub-menu> 
              <template #title>
                <el-icon><User /></el-icon>
                <span>个人信息</span>
              </template>
              <el-menu-item index="userInfo">我的信息</el-menu-item>
              <el-menu-item index="scaleRecord">测评记录</el-menu-item>
              <el-menu-item index="documentRecord">咨询档案</el-menu-item>
             </el-sub-menu>
        <el-menu-item index="login" @click="logout">
        <el-icon><Remove /></el-icon>
        <span>退出登录</span>
        </el-menu-item>
    </el-menu>

</template>

<script>
import router from "@/router";
import store from "@/store";
import axios from "axios";
import {  
    House,
    ChatDotRound,
    Notebook,
    User,
    Remove} from "@element-plus/icons-vue"
//import { ElMessage } from "element-plus";
export default {
//   components: {
//     ElMessage,
//   },
  components:{
    House,
    ChatDotRound,
    Notebook,
    User,
    Remove,
  },
  data() {
    return {
    };
  },
  methods: {
    logout() {
      store.state.userInfo = null;
      localStorage.clear();
      router.replace('/login');
      this.$emit('logout');
      axios({
        url:"api/user/logout",
        method: "post",
      })
    },
  },
};
</script>

<style scoped>
    .el-menu-vertical{
        height:100vh;
    }
</style>
