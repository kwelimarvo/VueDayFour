<script>

export default {
  data() {
    return {
      title:'To-do List',
      new_item:'',list:['apple','orange'],
      max:8
    }
  },
  computed:{
    msg(){
      if(this.list.length==0){
        return 'add a new item'
      }else if(this.list == 1){
        return 'one item'
      }else{
        return this.list.length+' items'
      }
    }
    },
    
    methods:{
      add_item(){
      if(this.new_item.length==0) return
      this.list.push(this.new_item)
      this.new_item=''
    },
    delete_item(index){
    this.list.splice(index,1)
    },
    check(){
      if(this.new_item.length>this.max){
        this.new_item = this.new_item.substring(0,this.max)
      }
    }
    }
}
</script>

<template>
<h1 class="text-green-400 text-center text-3xl bg-red-400 py-3 mb-4 font-bold">{{title}}</h1>
        <input class="bg-yellow-400 place-content-center" type="text" v-model='new_item' @input='check' :placeholder='msg'>&nbsp;
        <span>{{max-new_item.length}}/{{max}}</span>
        <button @click='add_item' :disabled='new_item.length==0'>Add Fruit</button>
        <ul class="text-center" v-if='list.length>0'>
            <li v-for='(elem,index) in list' :key='index'>
                {{elem}}
                <button @click='delete_item(index)'>delete</button><br><br><br>
            </li>
        </ul>
        <p v-else>nothing to do...</p>
</template>

<style scoped>
  button {
    background-color: lightseagreen;
    padding: 5px 5px;
    margin-left: 5px;
    border-radius: 0.4rem;
  }
</style>
