<template>
  <div id = "container">


     <table class="dataTabble">
  <thead>
    <tr>
      <th width="110">栏目名称</th>
      <th width="200">发布时间</th>
      <th width="160">公告数量</th>
      <th width="160">操作</th>
    </tr>
  </thead>
  <draggable v-model="tablelist" element="tbody" :move="getdata" @update="datadragEnd">
    <tr v-for="(item,id) in tablelist" :key="id" class="custom-title cusstom-top-title custom-bottom">
      <td class="custom-title">{{item.name}}</td>
      <td class="custom-title">{{item.time}}</td>
      <td class="custom-title">{{item.num}}</td>
      <td class="custom-title">
        <div class="tabopa">
          <a @click="add"> <i class="el-icon-plus"></i></a>
          <a @click="open2"> <i class="el-icon-close"></i></a>
          <a @click="open2"> <i class="el-icon-rank"></i></a>
        </div>
      </td>
    </tr>
  </draggable>
</table>
<div class="zhu mt40">提示：拖动可对栏目进行排序</div>
  </div>
</template>
<script>

import draggable from"vuedraggable";
export default {
  components: {
    draggable,
  },
data(){
  return {
    initData:'123',
        tablelist: [
      { id: 1, name:"活动消息1", time:"2018-08-25 14：54", num:"1000" },
      { id: 2, name:"公司消息2", time:"2018-08-25 14：54", num:"200" },
      { id: 3, name:"个人消息3", time:"2018-08-25 14：54", num:"30000" },
      { id: 4, name:"客户消息4", time:"2018-08-25 14：54", num:"40" }
    ],
          tableItem:{
            id: 4,
            name: '王小虎1',
            time:"2018-08-25 14：54", num:"1000"
          },
  }
},
mounted() {


  },
    methods: {
  //拖动中与拖动结束
    getdata(evt) {
      console.log(evt.draggedContext.element.id);
    },
    datadragEnd(evt) {
      console.log("拖动前的索引 :" + evt.oldIndex);
      console.log("拖动后的索引 :" + evt.newIndex);
      console.log(this.tags);
    },
    open2(){},
    add(){}
    },
}
</script>
<style scoped>
#container{

  display: flex;
}
.custom-item {
  margin-bottom: 5px;
  border-bottom: 1px solid #f8f8f8;
}
.custom-title {
  padding: 5px 0px;
 text-align: center;
}
.custom-title > b {
  display: inline-block;
  width: 33%;
}
.custom-title > b:first-child {
  width: 45%;
}
.custom-title > b:last-child {
  width: 8%;
}
.custom-title > b:nth-child(2) {
  width: 35%;
}
.custom-title > b:nth-child(3) {
  width: 10%;
}
.cusstom-top-title > b:last-child {
  width: 15%;
}
.custom-bottom{
   border-bottom: 1px solid #000;
}
</style>
