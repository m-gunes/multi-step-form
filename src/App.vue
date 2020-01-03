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

               <form action="" class="multi-step-form" v-if="activeStep === 0">
                  <section>
                     <div class="multi-step-form__heading">
                        <h3>Data Product Name</h3>
                        <span>With the Internet spreading like wildfire and reaching every part.</span>
                     </div>
                     <Input />
                     <a-button type="primary" @click="previous()">Back</a-button>
                     <a-button type="primary" @click="next()">Next</a-button>
                  </section>
               </form>

               <form action="" class="multi-step-form" v-if="activeStep === 1">
                  <section>
                     <h3>step 2</h3>
                     <Input />
                     <a-button type="primary" @click="previous()">Back</a-button>
                     <a-button type="primary" @click="next()">Next</a-button>

                  </section>
               </form>

               <form action="" class="multi-step-form" v-if="activeStep === 2">
                  <section>
                     <h3>step 3</h3>
                     <Input />
                     <a-button type="primary" @click="previous()">Back</a-button>
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
import { Input, Col, Row, Button } from 'ant-design-vue';

export default {
  name: 'app',
  data(){
     return{
        activeStep: 0
     }
  },
  components: {
    Input,
    "a-row": Row,
    "a-col": Col,
    "a-button": Button
  },
  methods: {
     next(){
        this.activeStep++;
     },
     previous(){
        this.activeStep--;
     }
  }
}
</script>

<style lang='scss'>
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
   &__heading{
      text-align: left;
   }
}
</style>
