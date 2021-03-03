<template>
    <div>
        <input @input="onInput" class="mx-auto"/>
    </div>
</template>

<script>
    export default {
      name: 'SearchBar', 
      methods: {
          onInput: function(event) {
            this.$emit('termChange', event.target.value);
          }
      }
    };
</script>

<style scoped>
  input {
    max-width: 400px;
    width: 100%;
    border: 1px solid #ddd;
    border-radius: 5px;
    padding: 10px; 
  }

  div {
    text-align: center;
    margin: 20px auto;
  }
</style>