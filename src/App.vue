<template>
  <div id="app">
    <Header />
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <questionsBox v-if="questions" 
          :currentQ="questions[index]" 
          :next="next"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>

import Header from "./components/Header.vue";
import questionsBox from "./components/questionsBox.vue";

export default {
  name: "App",

  components: {
    Header,
    questionsBox,
  },
  data() {
    return {
      questions: [],
      index: 0,
    };
  },
  methods:{
    
    next() {
       this.index++

    }

  },
  created: function () {
    fetch(
      "https://opentdb.com/api.php?amount=10&category=27&difficulty=easy&type=multiple",
      {
        method: "get",
      }
    )
      .then((response) => {
        console.log(response)
        return response.json();

      })
      .then((jsonData) => {
        this.questions = jsonData.result;
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
