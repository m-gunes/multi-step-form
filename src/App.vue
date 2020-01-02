<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <a-row type="flex" justify="space-around" align="middle" class="">
      <a-col :span="9" class="img-field">
         <img alt="Vue logo" src="./assets/logo.png">
         <h1>Multi Step Form</h1>
      </a-col>
      <a-col :span="15">
         <a-row type="flex" justify="center">
            <a-col :span="10">
               <form action="" class="multi-step-form">
                  <section>
                     <h3>step 1</h3>
                     <Input />
                  </section>
               </form>
            </a-col>
         </a-row>
      </a-col>
    </a-row>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import { Input, Col, Row } from 'ant-design-vue';

export default {
  name: 'app',
  components: {
    Input,
    "a-row": Row,
    "a-col": Col,
    
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.img-field {
   background-color: #f9f9f9;
   height: 100vh;

}

.multi-step-form {
}
</style>
