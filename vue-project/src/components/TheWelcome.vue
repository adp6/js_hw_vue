<script>
export default{
  name:"ToDoList",
  data(){
    return{
      list:["buy laptop","saddsadsa","buy food","a test"],
      add:'',
      remove:'',
      showErr:false,
      inputErr:false,
      sortMethod:''
    }
  },
  methods:{
    addToList(){
      if(this.add.length>0){
        this.add.toLocaleLowerCase()
        this.add.trimStart()
        this.add.trimEnd()
        this.inputErr=false
        this.list.push(this.add)
      }
      else{
        this.inputErr=true
      }
    },
    removeFromList(){
      for (let i=0;i<this.list.length;i++) {
        if(this.remove === this.list[i]){
          this.remove.toLocaleLowerCase()
          this.remove.trimStart()
          this.remove.trimEnd()
          this.list.splice(i,1)
          this.showErr = false
        }
        else{
          this.showErr = true
        }
      }
    },
    sort(){
      if(this.sortMethod === 'alp'){
        this.list.sort()
      }
      else if(this.sortMethod === 'len'){
        this.list.sort((a,b)=>a.length-b.length)
      }
    }
  }
}
</script>

<template>
    <main>
      <div>
        <ul>
          To Do List
          <li v-for="li in list">{{ li }}</li>
        </ul>
      </div>
      <div>
        <input type="text" v-model="add"><button @click="addToList">add</button>
      </div>
      <div v-if="inputErr">
        Empty input
      </div>
      <div>
        <input type="text" v-model="remove"><button @click="removeFromList">remove</button>
      </div>
      <div v-if="showErr">
        no such item
      </div>
      <div>
        <div><input type="radio" name="sort" id="" value="alp" v-model="sortMethod" @change="sort"><label for=""> sort by alphabet</label></div>
        <div><input type="radio" name="sort" id="" value="len" v-model="sortMethod" @change="sort"><label for=""> sort by length</label></div>
      </div>
    </main>
</template>

<style>
  ul{
    color: white;
  }
  main div{
    margin-bottom: 10px;
  }
</style>