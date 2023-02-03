<template>
  <div>
    <h1>{{currentEmployee}}</h1>
  <div>
   <button @click="clicked($event.target.value)" value="Ann">Ann</button>
   <button @click="clicked($event.target.value)" value="Joe">Joe</button>
   <button @click="clicked($event.target.value)" value="John">John</button>
   <button @click="clicked($event.target.value)" value="Delete">Delete</button>
  </div>
  <br/>

  <br/>
  <br/>
  <el-breadcrumb separator="/">
    <el-breadcrumb-item :to="{ path: '/' }">homepage</el-breadcrumb-item>
      <el-breadcrumb-item v-for="s in stack" :key="s" :to="{ path: `/${s}` }">{{s}}</el-breadcrumb-item>


  </el-breadcrumb>


  </div>
</template>

<script>
export default {
data(){
  return{
    currentEmployee:'',
    stack:[]
  }
},

created(){
  this.currentEmployee= this.stack[this.stack.length-1]

},
methods:{
  clicked(val){
    if(val.includes('Delete')){
      this.stack.pop()
        this.currentEmployee= this.stack[this.stack.length-1]

    }
    else{
    console.log(val+" has been clicked")
    this.currentEmployee=''+val
    if(this.stack.includes(val)){
      
     

    }else{

    
    this.stack.push(val)
    }
    }
  }

}
}
</script>

<style>
body{
  background-color: white;
  color:black;
}
button{
  margin:10px;
}
</style>