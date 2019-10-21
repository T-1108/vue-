<template>
  <div class="login mask">
    <div class="box">
      <h3 class="text-center text-primary">登录</h3>
      <!-- <select v-model="user.type">
        <option value disabled>请选择角色</option>
        <option value="0">超级管理员</option>
        <option value="1">普通管理员</option>
      </select>-->
      <el-select class="select" v-model="user.type" placeholder="请选择角色">
        <el-option 
          v-for="item in options"
          :key="item.value"
          :label="item.label"
          :value="item.value"
        ></el-option>
      </el-select>
      <div class="inp_box">
        <el-input class="zh" placeholder="请输入账号" v-model="user.name" clearable></el-input>
        <el-input placeholder="请输入密码" v-model="user.pass" show-password clearable></el-input>
      </div>

      <div class="text-center">
        <!-- <button class="btn-primary" @click="login">登录</button> -->
        <el-row>
        <el-button class="btn" type="warning" @click="login">登录</el-button>
        </el-row>
      </div>
    </div>
  </div>
</template>

<script>
import API from "../common/js/API";
export default {
  data() {
    return {
      user: {
        name: "",
        pass: "",
        type: ""
      },
      options: [
        {
          value: "0",
          label: "超级管理员"
        },
        {
          value: "1",
          label: "普通管理员"
        }
      ],
      value: ""
    };
  },
  methods: {
    login() {
      // console.log(this.user)
      this.$axios({
        url: API.login,
        method: "post",
        data: this.user
      }).then(res => {
        if (res.data.isok) {
          this.$router.push("/index");
        } else {
          alert(res.data.info);
        }
      });
    }
  }
};
</script>

<style lang="stylus" scoped>
@import '../common/stylus/index.styl';

.inp_box {
  margin: 0 40px;
}

.zh {
  display: block;
  margin-bottom: 10px;
}
.select{
  display block;
  margin 0 40px 10px;
}
.btn{
  width 70px;
  height 50px;
  margin-top 10px;
}
</style>