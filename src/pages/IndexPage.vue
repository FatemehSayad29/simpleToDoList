<template>
  <q-page class="flex flex-center">
    <q-card class="my-card" style="width: 500px">
      <q-card-section>
        <div class="text-h1">
          <h4>ToDoList</h4>
        </div>
      </q-card-section>
      <q-card-section>
        <div class="row justify-center">
          <div class="col-12">
            <q-input v-model="todoTask" label="insert sth">
              <template v-slot:after>
                <q-btn round dense flat icon="send" @click="addItem"/>
              </template>
            </q-input>
          </div>
        </div>
      </q-card-section>
      <q-separator/>
      <q-card-section v-if="todoList.length>0">
        <div class="row justify-center" v-for="(item,index) in todoList" :key="index">
          <div class="col-8 q-py-md">
            {{item.value}}
          </div>
          <div class="col-auto q-py-md">
            <q-btn round dense flat icon="done" style="color:green" @click="removeItem(index)"/>
          </div>
        </div>
      </q-card-section>
      <q-card-section v-else>
        <div class="row justify-center">
          <div class="col-12">
              <h5>No Items</h5>
          </div>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { createApp, defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  data(){
    return{
      todoTask:'',
      todoList:[
        {value:'create an app'},
        {value:'build an app'}
      ]
    }
  },
  methods:{
    addItem(){
      this.todoList.push({value:this.todoTask})
    },
    removeItem(index){
      this.todoList.splice(index,1)
    }
  }
});
</script>
