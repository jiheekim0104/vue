<template>
  <div id="app">
    <app-header/>
    <div class="content">
      <div class="sidebar">
        <app-searchbox v-on:search="getInputValue"/>
        <app-basic v-bind:propsdata="boardList"/>
      </div>
      <app-detail v-bind:propsdata="boardList"/>
    </div>
    
    <app-footer/>
  
    <router-view></router-view>
  </div>
</template>

<script>
import _ from 'lodash'
import appHeader from './views/AppHeader.vue'
import appFooter from './views/AppFooter.vue'
import appSearchBox from './views/AppSearchBox.vue'
import appBasic from './views/AppBasic.vue'
import appDetail from './views/AppDetail.vue'


export default {
  components:{
    'app-header' : appHeader,
    'app-searchbox' : appSearchBox,
    'app-basic' : appBasic,
    'app-detail' : appDetail,
    'app-footer' : appFooter,
  },
  name: 'BoardList',
  data: function () {
    return {
      boardList: [],
      result: [],
      inputValue:'',
      all:[],
      types:[],
    }
  },
  //가져온 API 뿌려버리기!
  // created: function () {
  //   this.getList()
  // },
  created() {
    for(var i=0;i<=10;i++){
      this.getList(i);
    }
    console.log(this);
  },
  //포켓몬API axios로 가져옴
  methods: {
    getInputValue: function(searchNum){
      // console.log('숫자:',searchNum);
      this.inputValue=searchNum
      this.getList(searchNum);
    },
    getList: function (inputValue) {
      // console.log(inputValue);
      // if(inputValue=='NOT EXISTS'){
      //   console.log('come in');
      //   return this.boardList.push('NOT EXISTS')
      // }
      var url = 'https://pokeapi.co/api/v2/pokemon/'+inputValue
      this.$axios.get(url).then(response => {
        // console.log('### response: ' + JSON.stringify(response))
        this.all.push(response.data) 
        this.types = _.uniqBy(this.all,'types[0].type.name')
      }).catch(error => {
        console.log(error)
      })
    },


  }
}
</script>

<style>
html,body{
  margin: 0;
  height: 100%;
}
#app{
  height: 100%;
}
.content{
  display: flex;
  height: 92%;
}
.sidebar{
  width: 30rem;
  border-right:1rem black double;
  display: flex;
  flex-direction: column;
}

</style>
