<template>
  <div>
    <div class="img_Box">
      <div class="singleImg">
        <img class="dream_world" :src="[propsdata.sprites.other.dream_world.front_default]">
      </div>
      <div class="singleImg">
        <img class="front_default" :src="[propsdata.sprites.front_shiny]">
      </div>
      <div class="singleImg">
        <img class="front_default" :src="[propsdata.sprites.back_shiny]">
      </div>
      
    </div> 
    <div class="infoBox">
      무게: {{ toFixed(propsdata.weight/10)}} kg <br>
      키: 0.{{ propsdata.height }} m <br>
      {{ propsdata.species.name}}
      {{ propsdata.types}}
      {{ propsdata.types[0].type.name }}
    </div>
  </div>
  
</template>


<script>
export default {
  props:['propsdata'],
  methods: {
    toFixed: function(value) {
      return `${value.toFixed(1)}`
    },
  }

}
</script>

<style scoped>
div{
  /* border: 1px solid plum; */
  width: 100%;
}
.img_Box{
  display: flex;
}

.singleImg{
  height: 15rem;
  text-align: center;
}

.singleImg>.dream_world{
  height: 11rem;
  margin-top: 2rem;
}

.singleImg>.front_default{
  height: 15rem;
}
.infoBox{
  margin: 2rem;
  width: 50rem;
}

</style>