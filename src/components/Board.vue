<template>
  <div>
    <main>
      <p class="info-line mt-5 ml-5">All: 0 todos</p>
		
      <modal 
        v-show="getShow"
        @custom-modal="hideModal"
      />

      <!-- <p>data:{{ getIsShow }}</p> -->
      <p>computed:{{ getShow }}</p>

        <div class="todo-index d-flex flex-wrap ml-5">
          <todo v-for="(item, index) in todos"
            :key="item.id"
            :title="item.title"
            :deadLine = "item.deadLine"
            :status = "item.status"
            :todoIndex="index"
          />
        </div>  
    </main>
  </div> 
</template>

<script>
    import Todo from './Todo.vue'
    import Modal from './Modal.vue'
    import { mapState } from 'vuex'

    export default {
			components:{
				Todo,
        Modal
			},

      props:{
        isShow:{
          type:Boolean
        }
      },

      // data(){
      //   return{
      //     getIsShow:this.isShow
      //   }
      // },

      // created(){
      //   this.getIsShow = this.isShow
      // },

      computed:{
        ...mapState([
          'todos'
        ]),
      
        getShow:{
          get(){
            return this.isShow
          },
          set(getShow){
             this.isShow = getShow
          }
        }
      },

      methods:{
        hideModal(){
          console.log('hideModal')
          this.getShow = false;
          // this.getIsShow = false
        }
      },
    }
</script>