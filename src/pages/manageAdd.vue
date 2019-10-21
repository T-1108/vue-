<template>
  <div>
    <!-- <router-view></router-view> -->
    <div class="input">
      <el-input v-model="name" placeholder="请输入账号"></el-input>
    </div>
    <div class="input">
      <el-input placeholder="请输入密码" v-model="pass" show-password></el-input>
    </div>
    <div class="input">
      <div class="block" style="width:100%">
        <el-date-picker style="width:100%" v-model="time" type="datetime" placeholder="选择日期时间"></el-date-picker>
      </div>
    </div>
    <div class="input">
      <el-input v-model="des" placeholder="请输入描述内容"></el-input>
    </div>
  </div>
</template>

<script>
import API from "../common/js/API";
export default {
  data() {
    return {
      name:"",
      pass:"",
      time:"",
      des:""

    };
  }
};
</script>

<style lang="stylus" scoped>
@import '../common/stylus/index.styl';

.input {
  height: 40px;
  width: 50%;
  margin-bottom: 30px;
  margin: 40px auto;
}

</style>