<template>
  <h2>{{customTitle}}</h2>
  <p>{{squareCounter}}</p>
    <p>{{counter}}</p>
    <div>
        <button v-on:click="increaseCounter()">+1</button>
        <button v-on:click="decreaseCounter()">-1</button>

    </div>

</template>

<script>
export default {

props:{
    titulo:{
        type:String,
        required:true
    },
    start:{
        type:Number,
        default:1,
        validator(value){
            return value>100
        }
    }
},

data(){
    return {
        counter:this.start
    }
},
methods:{
    getSquareValue(){
   
        return this.counter*this.counter
    },
    increaseCounter(){
        return this.counter++
    },
        decreaseCounter(){
             return this.counter--
        },

},
computed:{
    //se guardan en el cache

    squareCounter(){
        console.log('squareCounter');
        return this.counter*this.counter;
    },
    customTitle(){
            console.log(this.titulo)
        return this.titulo?this.titulo:"counter"
        
    }
}
}
</script>

<style>
    button{
        background-color: #64BB87;
        border-radius: 5px;
        color:white;
        margin:0 5px;
        border:1px solid white;
        cursor:pointer;
        padding: 5px 15px;
        transition: 0.3s ease-in-out;

    }

    button:hover{
        background-color:#5aa67b;
        transition: 0.3s ease-in-out;
    }
</style>