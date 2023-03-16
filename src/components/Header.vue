<template>
  <header>
    <h1 >{{ title }}</h1>
    <AppButton text="Add task" class="btn" color="green"></AppButton>
  </header>
</template>

<script>
  export default{
    name:"Header",
    components: {
    AppButton,
  },
    props: {
      title: {
        type: String,
        default: "Hello World"
      }
    },

    methods: {
      handleModal(){
        $emit('showModal', true)
      },  
    },

    emits: ['showModal'],


  }

import AppButton from './AppButton.vue';
</script>

<style scoped>

header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

</style>