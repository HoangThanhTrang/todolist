<template>
    <div id="todo">
        
        <h2>{{title}}</h2>
        <input type="text" v-model="newItem">
        <span>

        <button v-on:click="addItem">Add</button>
        </span>
        <div class="todolist">
            <ul>
                <li v-for="(item,indx) in items" :key="indx" v-bind:class="{'done' :item.checked}">
                                       
                    <label  for="">
                        <input type="checkbox" v-model="item.checked" name="" id="">
                        {{item.text}}
                        <span><button v-on:click="deletetodo(indx)">Delete</button></span>
                    </label>
                    
                </li>
            </ul>
        </div>
        <footer>
            <span>Change your title</span>
            <input type="text" v-model="title">
        </footer>
    </div>
</template>
<script>

export default {
       name:'todolist' ,
       data() {
           return {
               title:"To do list",
               items:[
                   {text:"hadhjdhded",checked:true},
                   {text:"hihihihi",checked:false},
                   {text:"aaaa",checked:false},

               ],   
               newItem:''
           }
       },
       methods:{
           addItem(){
               var text;
               text = this.newItem.trim()
               if(text){
                   this.items.push({
                       text:text,
                       checked:false
                   });
                   this.newItem=''
               }
           },
           deletetodo(indx){
               this.items.splice(indx,1)
           }
       },
       props:{
           msg:String
       }
       
    
}
</script>
<style scoped>
ul li{
    list-style: none;

}
.done label{
    text-decoration:line-through;
    color: gray;
}
</style>