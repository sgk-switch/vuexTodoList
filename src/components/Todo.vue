<template>
<div>
  <v-card
    class="mx-auto mr-5 mb-5"
    width="320"
    outlined  
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">
          期日:{{ deadLine }}
        </div>
        <v-list-item-title class="headline mb-1">
          {{ title }}
          <p class="text-body-1 mt-1">
            {{ status }}
          </p>  
        </v-list-item-title>
      </v-list-item-content>
    </v-list-item>

    <v-card-actions>
      <v-btn
				color="primary"
        rounded
				@click="deleteTodo"
      >
        削除する
      </v-btn>
    </v-card-actions>
  </v-card>
</div>

</template>

<script>
    export default {
        props:{
            title: {
                type: String,
                required: true
            },
            todoIndex:{
                type: Number,
                required: true
            },
            deadLine:{
              type:String,
              required: false
            },
            status:{
              type:String,
              required: false
            }
        },

        methods:{
            deleteTodo(){
                if(confirm('本当にこのTodoを削除しますか？')){
                    this.$store.dispatch('deleteTodo', {todoIndex: this.todoIndex})
                }
            }
        }
    }

</script>

