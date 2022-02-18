<template>
  <div class="condition-wrap condition-wrap-before">
     <el-cascader
     style="margin-right:20px;"
    :options="options"
    v-model="selectedOptions">
  </el-cascader>
   <el-select style="margin-right:20px;width:80px;" v-model="Svalue" placeholder="请选择">
    <el-option
      v-for="item in Selectoptions"
      :key="item.value"
      :label="item.label"
      :value="item.value">
    </el-option>
  </el-select>
  <el-input style="margin-right:20px;width: 120px;" v-model="input" placeholder="请输入内容"></el-input>

  </div>
</template>

<script>
export default {
  name: 'Condition',
  props: [
    'rootCondition'
  ],
  data:()=>{
    return {
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
      options:[{
          value: 'zhinan',
          label: '指南',
          children: [{
            value: 'shejiyuanze',
            label: '设计原则',
            children: [{
              value: 'yizhi',
              label: '一致'
            }]
          }, {
            value: 'daohang',
            label: '导航',
            children: [{
              value: 'cexiangdaohang',
              label: '侧向导航'
            }, {
              value: 'dingbudaohang',
              label: '顶部导航'
            }]
          }]
        }, {
          value: 'zujian',
          label: '组件',
          children: [{
            value: 'basic',
            label: 'Basic',
            children: [{
              value: 'layout',
              label: 'Layout 布局'
            }]
          }, {
            value: 'form',
            label: 'Form',
            children: [{
              value: 'radio',
              label: 'Radio 单选框'
            }, {
              value: 'checkbox',
              label: 'Checkbox 多选框'
            }]
          }, {
            value: 'data',
            label: 'Data',
            children: [{
              value: 'table',
              label: 'Table 表格'
            }]
          }, {
            value: 'notice',
            label: 'Notice',
            children: [{
              value: 'alert',
              label: 'Alert 警告'
            }]
          }, {
            value: 'navigation',
            label: 'Navigation',
            children: [{
              value: 'menu',
              label: 'NavMenu 导航菜单'
            }]
          }, {
            value: 'others',
            label: 'Others',
            children: [{
              value: 'dialog',
              label: 'Dialog 对话框'
            }]
          }]
        }, {
          value: 'ziyuan',
          label: '资源',
          children: [{
            value: 'axure',
            label: 'Axure Components'
          }]
        }]
    }
  },
  created(){
    // this.Svalue =  this.rootCondition.expression.operator.label
  },
  watch:{
     'rootCondition.expression':{
    handler(newValue,oldValue){
      console.log(newValue);
      console.log(oldValue);
      this.Svalue =  newValue.operator.label
    },
    immediate:true,
    deep:true
  },
  }
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
