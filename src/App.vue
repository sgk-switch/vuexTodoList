<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
       <v-toolbar-title>My TodoList</v-toolbar-title>
      <v-spacer></v-spacer>

      <v-btn 
        text
        @click="openModal()"
      >
        新規作成
      </v-btn>

    </v-app-bar>

    <v-main>
      <Board :isShow='isShow'/>
    </v-main>
  </v-app>
</template>

<script>
import Board from './components/Board.vue';

export default {
  name: 'App',

  components: {
    Board,
  },

  data(){
    return{
      isShow: false,
    }
  },

  methods:{
    openModal(){
      this.isShow = !this.isShow
    }
  }

};
</script>
