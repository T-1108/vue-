<template>
  <div>
    <button class="add btn-third" @click="$router.push('/index/manage/add?id='+0)">添加</button>
    <table>
      <tr>
        <th>序号</th>
        <th>账号</th>
        <th>属性</th>
        <th>时间</th>
        <th>操作</th>
      </tr>
      <tr v-for="(item,index) in d" :key="item.id">
        <td>{{index+1}}</td>
        <td>{{item.name}}</td>
        <td>{{item.des}}</td>
        <td>{{item.time}}</td>
        <td>
          <button @click="toAdd(item.id)">修改</button>
          <v-del :idx="item.id" @del="myDel"></v-del>
        </td>
      </tr>
      <tr v-if="d.length==0">
        <td colspan="5">暂无数据</td>
      </tr>
    </table>
    
    
  </div>
</template>
<script>
import API from "../common/js/API";
export default {
  data() {
    return {
      d: [],
    };
  },
  methods: {
    init() {
      this.$axios({
        url: API.findManage,
        mehtod: "post"
      }).then(res => {
        this.d = res.data.data;
        // console.log(res);
      });
    }
  }
};
</script>
<style lang="stylus" scoped>
@import '../common/stylus/index.styl';

.add {
  width: 100px;
  margin-left: 100px;
}


</style>