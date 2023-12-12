<template>
  <formularioAp2/>
</template>

<script>
  import formularioAp2 from './components/formularioAp2.vue'
  export default{
        name: 'MainAP',
        components: {
          formularioAp2
        }
    }
</script>

<style>
body{
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f4f4f4;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  margin: 0;
}
</style>
