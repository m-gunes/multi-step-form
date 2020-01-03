<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <a-row type="flex" justify="space-around" align="middle" >
      <a-col :span="9" class="img-field" >
        <img alt="Vue logo" src="./assets/logo.png" />
        <h1>Multi Step Form</h1>
      </a-col>
      <a-col :span="15">
        <a-row type="flex" justify="center">
          <a-col :span="10">
            <a-steps progressDot size="small" :current="activeStep">
              <a-step v-for="item in steps" :key="item" />

              <!-- <a-step v-for="item in steps" :key="item" > -->
              <!-- <a-icon :component="StepIcon" slot="icon"/> -->
              <!-- <img :src="StepIcon" slot="icon"/> -->
              <!-- </a-step> -->
            </a-steps>
            <div class="indicator">{{activeStep}}/3</div>

            <a-form action class="multi-step-form">
              <section v-if="activeStep === 0">
                <div class="multi-step-form__heading">
                  <h3>Data Product Name</h3>
                  <span>With the Internet spreading like wildfire and reaching every part.</span>
                </div>

                <a-form-item label="Data">
                  <a-input placeholder="Customer Services Data" />
                  <small class="small-exp">At least 14, max. 72 character.</small>
                </a-form-item>

                <a-button type="primary" class="next-btn" @click="next()">Next</a-button>
              </section>

              <section v-if="activeStep === 1">
                <div class="multi-step-form__heading">
                  <h3>What industry is this  data related?</h3>
                  <span>With the Internet spreading like wildfire and reaching every part.</span>
                </div>

                <div class="industry-body">
                  <a-button type="link" @click="selectAll()" class="select-all-btn">Select all that apply</a-button>
                  <div>
                     <a-card-grid
                     v-for="item in industryItem"
                     :key="item.name"
                     @click="selectItem(item)"
                     class="industry-body__item"
                     :class="{selectedItem: item.isActive}"
                     >{{item.name}}</a-card-grid>
                  </div>
                </div>

                <a-button type="primary" class="previous-btn" @click="previous()">Back</a-button>
                <a-button type="primary" class="next-btn" @click="next()">Next</a-button>
              </section>

              <section v-if="activeStep === 2">
                 <div class="multi-step-form__heading">
                  <h3>Data Collect</h3>
                  <span>With the Internet spreading like wildfire and reaching every part.</span>
                </div>

                <div class="dataCollect-body">
                   <div class="dataCollect-body__title">How ws this data collected?</div>
                  <div>
                     <a-card-grid
                        v-for="item in dataCollect"
                        :key="item.name"
                        @click="selectItem(item)"
                        class="dataCollect-body__item"
                        :class="{selectedItem: item.isActive}"
                     >{{item.name}}</a-card-grid>
                  </div>
                </div>

                <a-button type="primary" class="previous-btn" @click="previous()">Back</a-button>
              </section>
            </a-form>
          </a-col>
        </a-row>
      </a-col>
    </a-row>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import {
  Form,
  Input,
  Col,
  Row,
  Button,
  Steps,
  Icon,
  Card
} from "ant-design-vue";
import StepIcon from "./assets/oval.svg";

export default {
  name: "app",
  data() {
    return {
      //current: 0,
      activeStep: 0,
      totalTabs: 0,
      steps: [0, 1, 2],
      industryItem: [
        { name: "Advertising", isActive: false },
        { name: "Automotive", isActive: false },
        { name: "Financial Services", isActive: false },
        { name: "Energy", isActive: false },
        { name: "Internet", isActive: false },
        { name: "Telecommunications", isActive: false },
        { name: "Healthcare", isActive: false },
        { name: "Insurance", isActive: false },
        { name: "Agriculture", isActive: false },
        { name: "Tobacco", isActive: false },
        { name: "Music Production", isActive: false },
        { name: "Gas & Oil", isActive: false },
        { name: "Food & Beverage", isActive: false },
        { name: "Drug Manufacturers", isActive: false },
        { name: "Defense", isActive: false },
        { name: "Computer Software", isActive: false },
        { name: "Construction", isActive: false }
      ],
      dataCollect: [
         {name: "With the Internet spreading like wildfire and reaching every part.", isActive: false},
         {name: "With the Internet spreading like wildfire and reaching every part.", isActive: false},
         {name: "With the Internet spreading like wildfire and reaching every part.", isActive: false},
         {name: "With the Internet spreading like wildfire and reaching every part.", isActive: false},
      ]
    };
  },
  components: {
    "a-row": Row,
    "a-col": Col,
    "a-form": Form,
    "a-button": Button,
    "a-steps": Steps,
    "a-step": Steps.Step,
    "a-input": Input,
    "a-form-item": Form.Item,
    //"a-card": Card,
    "a-card-grid": Card.Grid
    //"a-icon": Icon,
    //StepIcon
  },

  methods: {
    next() {
      // isValid ?
      this.activeStep++;
    },
    previous() {
      this.activeStep--;
    },
    selectItem(item) {
      item.isActive = !item.isActive;
      //  this.selectedIndustryItem.push(item);
      console.log("industryItem ", this.industryItem);
    },
    selectAll() {
      this.industryItem.map(item => (item.isActive = true));
      console.log("industryItem all ", this.industryItem);
    }
  }
};
</script>

<style lang='scss'>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  //text-align: center;
  color: #2c3e50;
  //margin-top: 60px;
}

.img-field {
  background-color: #f9f9f9;
  height: 100vh;
  text-align: center;
}

.progress-bar {
  margin-bottom: 40px !important;
}

.indicator {
  text-align: left;
  font-weight: 600;
  color: #57bf94;
}

.multi-step-form {
  &__heading {
    text-align: left;
    margin-bottom: 20px;
    //font-family: Inter;
    h3 {
      font-size: 24px;
      font-weight: bold;
      color: #363948;
    }
    span {
      font-size: 14px;
      font-weight: 500;
      line-height: 1.57;
      color: #626b89;
    }
  }

  .ant-form-item-label {
    text-align: left;
    float: left;
  }
  .small-exp {
    opacity: 0.4;
    //font-family: GalanoGrotesque;
    font-size: 12px;
    font-weight: 500;
    line-height: 3;
    color: #2c3241;
    float: left;
  }
  .previous-btn {
    float: left;
  }
  .next-btn {
    float: right;
  }
  .industry-body {
      border-top: 1px solid #ccc;
      border-bottom: 1px solid #ccc;
      overflow: scroll;
      height: 315px;
      margin-bottom: 10px;
      padding-top: 10px;
      &__item {
         width: calc(50% - 24px);
         text-align: center;
         cursor: pointer;
         padding: 14px;
         margin: 8px;
      }
  }

  .selectedItem {
    background-color: #5e9fda;
  }
  .select-all-btn {
      //font-family: GalanoGrotesque;
      font-size: 14px;
      font-weight: 500;
      line-height: 1.57;
      color: #2c3241;
      padding: 7px;
  }

   .dataCollect-body {
      &__title {
         //font-family: GalanoGrotesque;
         font-size: 14px;
         font-weight: 500;
         line-height: 1.57;
         color: #2c3241;
      }
      &__item {
            width: 100%;
            padding: 14px;
            margin-bottom: 10px;
            cursor: pointer;
      }
   }
}
</style>
