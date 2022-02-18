<template>
  <div id="app">
    <ConditionView
                        disabled={disabled}
                        ruleId={id}
                        rootCondition={rootCondition}
                        dispatch={dispatch}
                        constants={constants}
                        variables={variables}
                        funcs={funcs}
                      />
  </div>
</template>

<script>
import ConditionView from './components/ConditionView.vue'

export default {
  name: 'App',
  mounted(){
    async function async1(){
      console.log('async1 start');
      await async2();
      console.log('async1 end');
    }
    async function async2(){
      console.log('async2');
    }
    console.log('start');
    setTimeout(function(){
      console.log('settimeout');
    },0)
    async1();
    new Promise(function(resolve){
      console.log('promise1');
      resolve();
    }).then(function(){
      console.log('promise2');
    })
    console.log('script end');
  },
  components: {
    ConditionView
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
