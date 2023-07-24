<template>
  <div class="basic" >
    <img class="front_default" :src="[propsdata.sprites.other.home.front_default]"><br>
    <div class="infoBox">  
      <div class="name">번호</div>
      <span>{{ propsdata.id }}</span>
    </div> 
    <div class="infoBox">
      <div class="name">이름</div>
      <span>{{ propsdata.name }}</span>
    </div>
     
  </div>
</template>

<script>
export default {
  props:['propsdata'],
  
}
</script>

<style scoped>
.basic{
  /* border: 1px solid darkorange; */
  height: 100%;
  padding: 1rem;
}
.front_default{
  height: 18rem;
  margin: 1rem;
}
.infoBox{
  font-size: 1.3rem;
  display: flex;
  margin-bottom: 1rem;
}
.name{
  background-color: rgb(51,104,176);
  height: 1.4rem;
  width: 3.5rem;
  margin: 0.17rem 0 0.17rem 0.45rem;
  border-radius: 2rem;
  font-size: 0.9rem;
  font-weight: bolder;
  text-align: center;
  color: white;
  padding-top: 0.1rem;
}
.infoBox>span{
  margin-left: 1rem;
}
</style>