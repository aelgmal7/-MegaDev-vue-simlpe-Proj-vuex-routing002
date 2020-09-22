<template>
  <div class="questions-box-container">
    <b-jumbotron>
      <template v-if="currentQ" v-slot:lead>{{currentQ.question}}</template>

      <hr class="my-4" />
      <b-list-group>
        <b-list-group-item
         >
         </b-list-group-item>
      </b-list-group>

      <b-button variant="primary" href="#">submit</b-button>
      <b-button variant="success" href="#" @click="next">next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQ: Object,
    next: Function,
  },
  computed: {
    
  },
  mounted() {
    console.log(this.currentQ);
  },
};
</script>