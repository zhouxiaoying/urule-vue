<template>
  <div class="condition-wrap condition-wrap-before">
     <el-cascader
     ref="cascader"
     style="margin-right:20px;"
    :options="options"
    v-show="selectedOptions[0] !== 'INPUT'"
    v-model="selectedOptions">
  </el-cascader>

<div v-show="selectedOptions[0] == 'INPUT'" style="display:inline-block">
   <el-input  style="margin-right:20px;width: 120px;" v-model="input" placeholder="请输入内容"></el-input>
  <el-cascader
  placeholder="修改值类型"
     style="margin-right:20px;"
    :options="options"
    @change="getCascaderValue">
  </el-cascader>
</div>
   <el-select style="margin-right:20px;width:80px;" v-model="Svalue" placeholder="请选择操作符">
    <el-option
      v-for="item in Selectoptions"
      :key="item.value"
      :label="item.label"
      :value="item.value">
    </el-option>
  </el-select>
  <el-cascader
     ref="cascader"
     style="margin-right:20px;"
    :options="options"
    v-show="selectedOptions[0] !== 'INPUT'"
    v-model="selectedOptions">
  </el-cascader>

<div v-show="selectedOptions[0] == 'INPUT'" style="display:inline-block">
   <el-input  style="margin-right:20px;width: 120px;" v-model="input" placeholder="请输入内容"></el-input>
  <el-cascader
  placeholder="修改值类型"
     style="margin-right:20px;"
    :options="options"
    @change="getCascaderValue">
  </el-cascader>
</div>
<el-button type="text">删除</el-button>
 
  </div>
</template>

<script>
export default {
  name: 'Condition',
  props: [
    'rootCondition',
    'variables',
    'constants',
    'funcs'
  ],
  data:()=>{
    return {
      curValue:{},
      input:'',
      Svalue:'',
      Selectoptions:[
        {
          value: '选项1',
          label: '+'
        }, {
          value: '选项2',
          label: '-'
        }, {
          value: '选项3',
          label: '*'
        }, {
          value: '选项4',
          label: '/'
        }, {
          value: '选项5',
          label: '%'
        }
      ],
      selectedOptions:[],
      options:[
        {
          value: 'INPUT',
          label: '输入值',
        }]
    }
  },
  created(){
    console.log(this.rootCondition);
    let tempVARIABLE = {
          value: 'VARIABLE',
          label: '选择变量',
          children: this.variables
        }
    let tempCONSTANT = {
          value: 'CONSTANT',
          label: '选择常量',
          children: this.constants
        }
    let tempFUNC = {
          value: 'FUNC',
          label: '选择函数',
          children: this.funcs
        }
    this.options.push(tempVARIABLE)
    this.options.push(tempCONSTANT)
    this.options.push(tempFUNC)
    // this.Svalue =  this.rootCondition.expression.operator.label
  },
  watch:{
     'rootCondition.expression':{
    handler(){
      // console.log(newValue);
      // console.log(oldValue);
      // this.Svalue =  newValue.operator.label
    },
    immediate:true,
    deep:true
  },
  },
  methods: {
    getCascaderValue(val){
      this.selectedOptions = val
      // console.log(val);
      // this.$set(this.curValue,'type',val[0])
      // console.log(this.curValue);
      // this.$refs.cascader.blur()
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
  .condition-wrap{
    text-align: left;
    margin-bottom: 10px;
    position: relative;
  }
  .condition-wrap:before{
     content: '';
    position: absolute;
    width: 16px;
    height: 1px;
    background-color: #c9c9c9;
    top: 20px;
    left: -16px;
  }
  
  
</style>
<style type="text/css" lang="less">
.el-cascader{
    .el-input__inner{
      border: none;
    }
  }
</style>
