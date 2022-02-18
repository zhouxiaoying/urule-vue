<template>
  <div class="unite-condition">
    <el-dropdown class="dropdown-wrap" split-button type="primary" @click="handleClick">
  {{rootCondition.type}}
  <el-dropdown-menu slot="dropdown">
    <el-dropdown-item>并且</el-dropdown-item>
    <el-dropdown-item>或者</el-dropdown-item>
    <el-dropdown-item divided>添加条件</el-dropdown-item>
    <el-dropdown-item>添加联合条件</el-dropdown-item>
    <el-dropdown-item divided v-if="rootCondition.id != 'ROOT'">删除</el-dropdown-item>
  </el-dropdown-menu>
</el-dropdown>
<div :class="rootCondition.subConditions.length > 1? 'sub-condition border-sub-condition':'sub-condition'" v-if="rootCondition.subConditions">
  <div v-for="item in rootCondition.subConditions" :key="item.id" class="sub-condition-wrap">
  <!-- <UniteCondition v-bind="$attrs" v-on="$listeners" v-if="item.type != 'normal'" :rootCondition="item"></UniteCondition> -->
  <UniteCondition  v-if="item.type != 'normal'" :rootCondition="item"></UniteCondition>
  <Condition v-bind="$attrs" v-on="$listeners" v-else :rootCondition="item"></Condition>
  </div>
</div>
<el-button @click="changeData">修改数据+{{rootCondition.type}}</el-button>
  </div>
</template>

<script>
import Condition from './Condition.vue'
export default {
  name: 'UniteCondition',
  props: [
   'rootCondition',
   'variables'
  ],
  components:{
    Condition
  },
  data:()=>{
    return{

    }
  },
  created(){

  },
  watch:{
    rootCondition:{
    handler(newValue,oldValue){
      console.log('unite***********8');
      console.log(newValue);
      console.log(oldValue);
    },
    deep:true
  },
  },
  methods:{
    handleClick(){

    },
    changeData(){
      this.$emit('changeData');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped type="text/css" lang="less">
  .unite-condition{
    display: flex;
    position: relative;
    .dropdown-wrap{
      margin-right: 16px;
      height: 40px;
    }
    .dropdown-wrap:after{
      content: '';
    position: absolute;
    width: 16px;
    height: 1px;
    background-color: #c9c9c9;
    top: 20px;
    right: -16px;
    }
    .sub-condition{
      padding-left: 16px;
      position: relative;
    }
    .sub-condition:before{
       content: '';
    position: absolute;
    width: 1px;
    height: 20px;
    background-color: #fff;
    top: 0;
    left: -1px;
    }
     .sub-condition:after{
        content: '';
    position: absolute;
    width: 1px;
    height: 29px;
    background-color: #fff;
    bottom: 0;
    left: -1px;
    }
    .border-sub-condition{
      border-left: 1px solid #ddd;
    }
    .sub-condition-wrap{
      position: relative;
    }
  }
  .unite-condition:before{
     content: '';
    position: absolute;
    width: 16px;
    height: 1px;
    background-color: #c9c9c9;
    top: 20px;
    left: -16px;
  }
  .sub-condition-wrap:before{
     content: '';
    position: absolute;
    width: 1px;
    height: 50px;
    background-color: #fff;
    top: 20px;
    left: -132px;
  }
</style>
