<template>
  <div class="content">
    <div>
      <span>系统操作</span>
      <br />
      <Edit class="icon"/>
      <span class="space">用气计划</span>
      <el-tag class="tag">已完成</el-tag>
      <br />
        <Share class="icon"/>
      <span class="space">设备参数</span>
      <el-tag class="tag" type="warning">在修订</el-tag>
      <br />
        <Help class="icon"/>
      <span class="space">水管阀门</span>
      <el-tag class="tag">已完成</el-tag>
      <br />
      <List class="icon"/>
      <span class="space">数据抄写</span>
      <el-tag class="tag" type="danger">待修订</el-tag>
    </div>
  </div>
</template>

<script>
import {Edit, Help, List, Share} from "@element-plus/icons-vue";

export default {
    components: {List, Help, Share, Edit}
};
</script>

<style scoped>
.content {
  border-radius: 10px;
  background-color: #ffffff;
  box-shadow: 20px 20px 60px #bebebe, -20px -20px 60px #ffffff;
}
.space {
  margin-left: 10px;
}
.tag{
    margin-left:30px
}
svg.icon{
    height: 1.125em;
    vertical-align: sub;
}
</style>
