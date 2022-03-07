<template>
  <div>
    <el-button type="primary" @click="handleSave">保存</el-button>
    <UniteCondition class="ftms-condition" 
    :rootCondition="rootCondition"
    :variables="variables"
    :constants="constants"
    :funcs="funcs"
    @changeData="changeData"
    >
    </UniteCondition>
  </div>
</template>

<script>
import UniteCondition from './UniteCondition.vue'
// import Condition from './Condition.vue'/
export default {
  name: 'ConditionView',
  props: [],
  data:()=>{
    return{
      rootCondition: {
        id: 'ROOT',
        type: 'and',
        subConditions: [
          {
            id: '95fe42f0b1f395f9e20529b825e5599d',
            type: 'normal',
            expression: {
              left: {
                id: 'fb842a8d3730e7cd5a919fc8a0014214',
                type: 'variable',
                value: {
                  groupCode: ['kehu'],
                  groupLabel: '客户',
                  propCode: 'hunfou',
                  propLabel: '婚否'
                }
              },
              operator: {
                label: '等于',
                charator: '=='
              },
              right: {
                id: '769dfa8a8013d8987735d542df188021',
                type: 'input',
                value: '未婚'
              }
            }
          },
          {
            id: '638b12ff1d67d0e61a3aace0f1e6a11c',
            type: 'normal',
            expression: {
              left: {
                id: 'f0c01555924010e52f9cc918c5a55d7d',
                type: 'variable',
                value: {
                  groupCode: ['kehu'],
                  groupLabel: '客户',
                  propCode: 'nianling',
                  propLabel: '年龄'
                }
              },
              operator: {
                label: '等于',
                charator: '=='
              },
              right: {
                id: '5a30eaec8e0ed46f49dcb25ebd51bc7c',
                type: 'func',
                value: {
                  actionName: 'date.action',
                  methodName: 'format',
                  methodLabel: '格式化日期',
                  parameters: [
                    {
                      name: '目标日期',
                      type: 'Date',
                      value: {
                        id: 'dfc3cd60659f125bcd5766905260b20c',
                        type: 'func',
                        value: {
                          actionName: 'date.action',
                          methodName: 'getDate',
                          methodLabel: '当前日期',
                          parameters: []
                        }
                      }
                    },
                    {
                      name: '格式',
                      type: 'String',
                      value: {
                        id: '150fea2a440d4a251c8e62982d7ef054',
                        type: 'input',
                        value: 'YYYYMMDD'
                      }
                    }
                  ]
                }
              }
            }
          },
          {
            id: '9ee37340f10e30a944f23860f7b06afd',
            type: 'normal',
            expression: {
              left: {
                id: 'b83129403fcaaf3c70b330d4d53ae60b',
                type: 'variable',
                value: {
                  dicts: {
                    label: '性别',
                    value: 'sex',
                    children: [
                      {
                        label: '男',
                        value: '1'
                      },
                      {
                        label: '女',
                        value: '0'
                      }
                    ]
                  },
                  groupCode: ['kehu'],
                  groupLabel: '客户',
                  propCode: 'xingbie',
                  propLabel: '性别'
                }
              },
              operator: {
                label: '等于',
                charator: '=='
              },
              right: {
                id: 'e12a208596c5525130399c43d507a3aa',
                type: 'constant',
                value: {
                  dicts: {
                    label: '性别',
                    value: 'sex',
                    children: [
                      {
                        label: '男',
                        value: '1'
                      },
                      {
                        label: '女',
                        value: '0'
                      }
                    ]
                  },
                  dictType: 'sex',
                  dictTypeLabel: '性别',
                  code: '1',
                  label: '男'
                }
              }
            }
          },
          {
            id: '57d2401cb7b49f4643bd4ba775886fc5',
            type: 'normal',
            expression: {
              left: {
                id: 'a201a2e363defe1868233f469705437d',
                type: 'variable',
                value: {
                  dicts: {
                    label: '性别',
                    value: 'sex',
                    children: [
                      {
                        label: '男',
                        value: '1'
                      },
                      {
                        label: '女',
                        value: '0'
                      }
                    ]
                  },
                  groupCode: ['kehu'],
                  groupLabel: '客户',
                  propCode: 'xingbie',
                  propLabel: '性别'
                }
              },
              operator: {
                label: '在集合中',
                charator: 'in'
              },
              right: {
                id: '911fb641ab283eccc1a17fd78601c551',
                type: 'constant',
                value: {
                  dicts: {
                    label: '性别',
                    value: 'sex',
                    children: [
                      {
                        label: '男',
                        value: '1'
                      },
                      {
                        label: '女',
                        value: '0'
                      }
                    ]
                  },
                  dictType: 'sex',
                  dictTypeLabel: '性别',
                  code: '',
                  label: ''
                }
              }
            }
          },
          {
            id: '50757e83994e09379b35c4132e4415bb',
            type: 'or',
            subConditions: [
              {
                id: '0a2d8a7d952e124159226a69ed21fb15',
                type: 'normal',
                expression: {
                  left: {
                    id: '2956e9cc421afbb073f3fc537d2a7d49',
                    type: 'variable',
                    value: {
                      groupCode: ['kehu'],
                      groupLabel: '客户',
                      propCode: 'nianling',
                      propLabel: '年龄'
                    }
                  },
                  operator: {
                    label: '大于等于',
                    charator: '>='
                  },
                  right: {
                    id: 'aaee47dcbcd8b775ad98baf0be3171f8',
                    type: 'input',
                    value: '99'
                  }
                }
              },
              {
                id: '0a2d8a7d952e124159226a69ed21fb17',
                type: 'normal',
                expression: {
                  left: {
                    id: '2956e9cc421afbb073f3fc537d2a7d49',
                    type: 'variable',
                    value: {
                      groupCode: ['kehu'],
                      groupLabel: '客户',
                      propCode: 'nianling',
                      propLabel: '年龄'
                    }
                  },
                  operator: {
                    label: '大于等于',
                    charator: '>='
                  },
                  right: {
                    id: 'aaee47dcbcd8b775ad98baf0be3171f8',
                    type: 'input',
                    value: '99'
                  }
                }
              }
            ]
          },
          {
            id: 'bbc7b9132e24deff907386b6c511fec2',
            type: 'or',
            subConditions: [
              {
                id: '1d1c6a532ac8222b8f45e05e59983688',
                type: 'normal',
                expression: {
                  left: {
                    id: '3a0dd38fea59adc86ba3bc3a86cee3c2',
                    type: 'variable',
                    value: {
                      groupCode: ['dingdan'],
                      groupLabel: '订单',
                      propCode: 'shuliang',
                      propLabel: '数量'
                    }
                  },
                  operator: {
                    label: '大于等于',
                    charator: '>='
                  },
                  right: {
                    id: 'f3e8f1bd1baf90153cabf5a7c3d119a0',
                    type: 'input',
                    value: '1000000'
                  }
                }
              },
               {
                id: '1d1c6a532ac8222b8f45e05e59983678',
                type: 'normal',
                expression: {
                  left: {
                    id: '3a0dd38fea59adc86ba3bc3a86cee3c2',
                    type: 'variable',
                    value: {
                      groupCode: ['dingdan'],
                      groupLabel: '订单',
                      propCode: 'shuliang',
                      propLabel: '数量'
                    }
                  },
                  operator: {
                    label: '大于等于',
                    charator: '>='
                  },
                  right: {
                    id: 'f3e8f1bd1baf90153cabf5a7c3d119a0',
                    type: 'input',
                    value: '1000000'
                  }
                }
              },
               {
                id: '1d1c6a532ac8222b8f45e05e59983668',
                type: 'normal',
                expression: {
                  left: {
                    id: '3a0dd38fea59adc86ba3bc3a86cee3c2',
                    type: 'variable',
                    value: {
                      groupCode: ['dingdan'],
                      groupLabel: '订单',
                      propCode: 'shuliang',
                      propLabel: '数量'
                    }
                  },
                  operator: {
                    label: '大于等于',
                    charator: '>='
                  },
                  right: {
                    id: 'f3e8f1bd1baf90153cabf5a7c3d119a0',
                    type: 'input',
                    value: '1000000'
                  }
                }
              },
              {
            id: 'bbc7b9132e24deff907286b6c511fec2',
            type: 'or',
            subConditions: [
              {
                id: '1d1c6a532ac8222b8f45e05e49983688',
                type: 'normal',
                expression: {
                  left: {
                    id: '3a0dd38fea59adc86ba3bc3a86cee3c2',
                    type: 'variable',
                    value: {
                      groupCode: ['dingdan'],
                      groupLabel: '订单',
                      propCode: 'shuliang',
                      propLabel: '数量'
                    }
                  },
                  operator: {
                    label: '大于等于',
                    charator: '>='
                  },
                  right: {
                    id: 'f3e8f1bd1baf90153cabf5a7c3d119a0',
                    type: 'input',
                    value: '1000000'
                  }
                }
              },

               
            ]
          }
            ]
          },
           {
                id: '1d1c6a532ac8222b8f35e05e59983468',
                type: 'normal',
                expression: {
                  left: {
                    id: '3a0dd38fea59adc86ba3bc3a86cee3c2',
                    type: 'variable',
                    value: {
                      groupCode: ['dingdan'],
                      groupLabel: '订单',
                      propCode: 'shuliang',
                      propLabel: '数量'
                    }
                  },
                  operator: {
                    label: '大于等于',
                    charator: '>='
                  },
                  right: {
                    id: 'f3e8f1bd1baf90153cabf5a7c3d119a0',
                    type: 'input',
                    value: '1000000'
                  }
                }
              }
        ]
      },
      variables:[
  {
    label: '客户',
    value: 'kehu',
    desc: '描述客户的一些信息',
    children: [
      { label: '年龄', value: 'nianling', dictType: '' },
      { label: '性别', value: 'xingbie', dictType: 'sex' },
      { label: '婚否', value: 'hunfou', dictType: '' },
      {
        label: '订单',
        value: '_dingdan',
        children: [
          { label: '数量', value: '_shuliang' },
          { label: '名称', value: '_mingcheng' },
          { label: '价格', value: '_jiage' }
        ]
      }
    ]
  },
  {
    label: '订单',
    value: 'dingdan',
    desc: '描述订单的一些信息',
    children: [
      { label: '数量', value: 'shuliang' },
      { label: '名称', value: 'mingcheng' },
      { label: '价格', value: 'jiage' }
    ]
  }
],
constants:[
  {
    label: '性别',
    value: 'sex',
    children: [
      { label: '男', value: '1' },
      { label: '女', value: '0' }
    ]
  }
],
funcs:[
  {
    label: '日期',
    value: 'date.action',
    id: 'date.action',
    children: [
      {
        value: 'format',
        label: '格式化日期',
        parameters: [
          { name: '目标日期', type: 'Date' },
          { name: '格式', type: 'String' }
        ]
      },
      {
        value: 'getDate',
        label: '当前日期',
        parameters: []
      },
      {
        value: 'addDateForDay',
        label: '日期加天',
        parameters: [
          { name: '目标日期', type: 'Date' },
          { name: '加几天', type: 'Number' }
        ]
      }
    ]
  }
]
    }
  },
  components:{
    UniteCondition,
    // Condition
  },
  methods:{
    handleSave(){
      console.log(this.rootCondition);
    },
    changeData(){
      alert(1);
      console.log(this.rootCondition);
      // this.rootCondition.subConditions[5].type = 'And';
      this.getTreeName(this.rootCondition.subConditions,'1d1c6a532ac8222b8f45e05e59983688');
    },
    getTreeName(list,id){
       let _this=this
      for (let i = 0; i < list.length; i++) {
        let a=list[i];
         if(a.id === 'bbc7b9132e24deff907386b6c511fec2'){
              let temp =  {
                id: '1d1c6a532ac8222b8f45e05e59983689',
                type: 'normal',
                expression: {
                  left: {
                    id: '3a0dd38fea59adc86ba3bc3a86cee3c2',
                    type: 'variable',
                    value: {
                      groupCode: ['dingdan'],
                      groupLabel: '订单',
                      propCode: 'shuliang',
                      propLabel: '数量'
                    }
                  },
                  operator: {
                    label: '大于等于',
                    charator: '>='
                  },
                  right: {
                    id: 'f3e8f1bd1baf90153cabf5a7c3d119a0',
                    type: 'input',
                    value: '1000000'
                  }
                }
              };
              // a.subConditions.push(temp);
              this.$set(a.subConditions,a.subConditions.length,temp)
            }
        if(a.id===id){
          console.log(a);
            // a.type = 'Andnd'
            // a.expression.operator.label = 'Andnd'
            this.$set(a.expression.operator,'label','Andnd');
          // return a.type
          alert(123);
        }else{
          if(a.subConditions && a.subConditions.length>0){
            let res=_this.getTreeName(a.subConditions,id)
            if(res){
              // return res
            }
          }
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
  .ftms-condition:after{
    content: '';
    position: absolute;
    width: 16px;
    height: 1px;
    background-color: #fff;
    top: 20px;
    left: -16px;
  }
</style>
