<template>
  <div id="app">
    <MyEcharts :options="options" :width="width"></MyEcharts>
    <button @click="changeSize">changeSize</button>
    <button @click="changeOptions">changeOptions</button>
  </div>
</template>

<script>
import MyEcharts from './components/MyEcharts.vue';
import {options1,options2} from './options'
export default {
  name: 'App',
  components: {
    MyEcharts,
  },
  data(){
    return{
      options:options1,
      width:'600px',
      optionsabc:options2
    }
    
  },
  methods:{
    changeSize(){
      if(this.width == '600px'){
        this.width = '800px'
      }else{
        this.width = '600px'
      }
    },
    changeOptions(){
      if(this.options == options1){
        this.options = options2
      }else{
        this.options = options1
      }
    }
  }
}
</script>