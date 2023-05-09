<template>
      <header>
            <h1 class="title">{{title}}</h1>
            <ButTon @btn-click="$emit('toggle-add-task')" 
                    :text="showAddTask ? 'Close' : 'Add Task'" 
                    :color="showAddTask ? 'red' : 'green'"/>
      
      <!--
      For Add More Button from component 'Button':

      <ButTon text="Upd Task" color="black"/>
      <ButTon text="Del Task" color="red"/> 
      -->
      </header>

</template>

<script>
      import ButTon from './button.vue'
      export default{
            // eslint-disable-next-line vue/multi-word-component-names
            name: 'Header',
            props:{
                  title: String,
                  showAddTask: Boolean
            },
      components : {
            ButTon
      }
      }
</script> 

<style scoped>
      header{
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
      }

</style>
