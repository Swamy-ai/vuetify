<template>
  <v-container>
    <v-row class="text-center">
      <v-col col="12">
        <v-card class="d-flex flex-column align-center">
        <v-card width="100%" class="purple lighten-4">
            <h1 class="mt-5 pink--text">TODOS</h1>
            <div class="d-flex flex-column align-start">
            <h1 class="pl-3 mt-5 display-1 pink--text"><span class="display-2">Create</span> Task</h1>
            <input type="text" depressed class="pink lighten-5 rounded-pill pl-5 pr-5 pt-3 pb-3 align-self-center mx-4" placeholder="Whats needs to be done?" v-model="title" name="title"/>
            <v-btn
      class="ma-2 align-self-center"
      fab
      dark
      small
      color="pink darken-1"
      v-on:click="addTodo"
    >
      <v-icon dark>
        mdi-plus
      </v-icon>
    </v-btn>
    <h1 class="px-4 py-4 pink--text display-1 align-self-center"><span class="">MY</span> Tasks</h1>
            </div>
        </v-card>
        </v-card>

      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name:'Header',
    data(){
        return{
            title:''
        }
    },
    methods:{
        addTodo(){
            const newTodo={
                title:this.title,
                completed:false
            }
            this.$emit('add-todo',newTodo);
            this.title='';
        }
    }
  }
</script>
