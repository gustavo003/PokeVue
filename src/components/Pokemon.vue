<template>
<div id="pokemon">
  <div class="card">
  <div class="card-image">
    <figure >
      <img :src="currentimage" alt="Placeholder image">
    </figure>
  </div>
  <div class="card-content">
    <div class="media">
  
      <div class="media-content">
        <p class="title is-4">{{num}} - {{name}}</p>
        <p class="subtitle is-6">{{pokemon.type}}</p>
      </div>
    </div>

    <div class="content">
   <button @click="mudar" class="button">Mudar Sprite</button>
    </div>
  </div>
</div>
</div>

   
</template>
<script>
import axios from 'axios';
export default {
    created:function(){
axios.get(this.url).then((result)=>{
this.pokemon.type = result.data.types[0].type.name;
this.pokemon.front = result.data.sprites.front_default;
this.pokemon.back = result.data.sprites.back_default; 
this.currentimage = this.pokemon.front;
})
    },
    props:{
        num:Number,
        name:String,
        url:String
    },
    methods:{
mudar:function(){
    if(this.isfront){
        this.isfront=false;
        this.currentimage = this.pokemon.back
    }
    else{        this.isfront=true;

                this.currentimage = this.pokemon.front;

    }
}
    },
    data(){
return{
    isfront:true,
    currentimage:'',
    pokemon:{
        type:'',
        front:'',
        back:''
    }
}
    },
filters:{
    upper: function(value){
var newval = value[0].toUpperCase() +value.slice(1);
return newval;
    }
}

}
</script>

<style scoped>
#pokemon{
    margin-top:2%
}
</style>