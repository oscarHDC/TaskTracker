<template>
  <button @click="onClick()" :style="{ 'background-color': color}" class="btn">{{ text }}</button>
</template>

<script>

export default{
  name: "Button",

  props: {
    text: String,
    color: String
  },

  methods: {
    onClick(){
      console.log("Button clicked");
    }
  }
}

</script>

<style>

</style>