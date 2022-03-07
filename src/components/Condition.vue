<template>
  <div class="condition-wrap condition-wrap-before">
    <!--左侧变量-->
     <el-cascader
     :key="rootCondition.expression.left.id"
     ref="cascader"
     style="margin-right:20px;"
    :options="options"
    v-show="rootCondition.expression.left.id && selectedOptions[0] !== 'INPUT'"
    v-model="selectedOptions">
  </el-cascader>

<div v-show="rootCondition.expression.left.id && selectedOptions[0] == 'INPUT'" style="display:inline-block">
   <el-input :key="rootCondition.expression.left.id"  style="margin-right:20px;width: 120px;" v-model="inputLeft" placeholder="请输入内容"></el-input>
  <el-cascader
  placeholder="修改值类型"
     style="margin-right:20px;width:100px"
    :options="options"
    @change="getCascaderValue">
  </el-cascader>
</div>

<!--中间操作符-->
   <el-select v-show="rootCondition.expression.operator" style="margin-right:20px;width:80px;" v-model="Svalue" placeholder="请选择操作符">
    <el-option
      v-for="item in Selectoptions"
      :key="item.value"
      :label="item.label"
      :value="item.value">
    </el-option>
  </el-select>



<!--右侧变量-->
  <el-cascader
  :key="rootCondition.expression.right.id"
     ref="cascader"
     style="margin-right:20px;"
    :options="options"
    v-show="rootCondition.expression.right.id && selectedOptionsRight[0] !== 'INPUT'"
    v-model="selectedOptionsRight">
  </el-cascader>

<div v-show="rootCondition.expression.right.id && selectedOptionsRight[0] == 'INPUT'" style="display:inline-block">
   <el-input :key="rootCondition.expression.right.id"  style="margin-right:20px;width: 120px;" v-model="inputRight" placeholder="请输入内容"></el-input>
  <el-cascader
  placeholder="修改值类型"
     style="margin-right:20px;"
    :options="options"
    @change="getCascaderValueRight">
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
      inputLeft:'',
      inputRight:'',
      Svalue:'',
      Selectoptions:[
        {
          value: '==',
          label: '=='
        }, {
          value: '!=',
          label: '!='
        }, {
          value: '<',
          label: '<'
        }, {
          value: '<=',
          label: '<='
        }, {
          value: '>',
          label: '>'
        },
        {
          value: '>=',
          label: '>='
        },
        {
          value: 'in',
          label: 'in'
        },
        {
          value: 'NotIn',
          label: 'NotIn'
        },
        {
          value: 'StartWith',
          label: 'StartWith'
        },
        {
          value: 'NotStartWith',
          label: 'NotStartWith'
        },
        {
          value: 'EndWith',
          label: 'EndWith'
        },
        {
          value: 'NotEndWith',
          label: 'NotEndWith'
        },
      ],
      selectedOptions:[],
      selectedOptionsRight:[],
      options:[
        {
          value: 'INPUT',
          label: '输入值',
        }]
    }
  },
  created(){
    console.log(this.rootCondition);
    //左侧变量初始化
    this.selectedOptions.push((this.rootCondition.expression.left.type).toUpperCase())
    if((this.rootCondition.expression.left.type).toUpperCase() == 'VARIABLE'){
      this.selectedOptions.push(this.rootCondition.expression.left.value.groupCode[0])
      this.selectedOptions.push(this.rootCondition.expression.left.value.propCode)
    }else if((this.rootCondition.expression.left.type).toUpperCase() == 'INPUT'){
      this.inputLeft = this.rootCondition.expression.left.value
    }else if((this.rootCondition.expression.left.type).toUpperCase() == 'CONSTANT'){
      this.selectedOptions.push(this.rootCondition.expression.left.value.dictType)
      this.selectedOptions.push(this.rootCondition.expression.left.value.code)
    }else if((this.rootCondition.expression.left.type).toUpperCase() == 'FUNC'){
      this.selectedOptions.push(this.rootCondition.expression.left.value.actionName)
      this.selectedOptions.push(this.rootCondition.expression.left.value.methodName)
    }
    //操作符初始化
    this.Svalue = this.rootCondition.expression.operator.charator
    //右侧变量初始化
    this.selectedOptionsRight.push((this.rootCondition.expression.right.type).toUpperCase())
    if((this.rootCondition.expression.right.type).toUpperCase() == 'VARIABLE'){
      this.selectedOptionsRight.push(this.rootCondition.expression.right.value.groupCode[0])
      this.selectedOptionsRight.push(this.rootCondition.expression.right.value.propCode)
    }else if((this.rootCondition.expression.right.type).toUpperCase() == 'INPUT'){
      this.inputRight = this.rootCondition.expression.right.value
    }else if((this.rootCondition.expression.right.type).toUpperCase() == 'CONSTANT'){
      this.selectedOptionsRight.push(this.rootCondition.expression.right.value.dictType)
      this.selectedOptionsRight.push(this.rootCondition.expression.right.value.code)
    }else if((this.rootCondition.expression.right.type).toUpperCase() == 'FUNC'){
      this.selectedOptionsRight.push(this.rootCondition.expression.right.value.actionName)
      this.selectedOptionsRight.push(this.rootCondition.expression.right.value.methodName)
    }
    console.log(this.selectedOptions);
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
      console.log(val);
      // this.$set(this.curValue,'type',val[0])
      // console.log(this.curValue);
      // this.$refs.cascader.blur()
    },
    getCascaderValueRight(val){
      this.selectedOptionsRight = val
      console.log(val);
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
  .el-input__inner{
    border: none !important;
  }
</style>
