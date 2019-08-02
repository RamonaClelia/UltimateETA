<template>
  <div class="container">
    <div v-for="item in txt_array">
      <carline v-if="item.poz==0" :txt="item.txt" :poz="item.poz"></carline>
    </div>
    <div v-for="item in txt_array">
      <carline v-if="item.poz==1" :txt="item.txt" :poz="item.poz"></carline>
    </div>
    <div v-for="item in txt_array">
      <carline v-if="item.poz==2" :txt="item.txt" :poz="item.poz"></carline>
    </div>
    <div v-for="item in txt_array">
      <carline v-if="item.poz==3" :txt="item.txt" :poz="item.poz"></carline>
    </div>
    <div v-for="item in txt_array">
      <carline v-if="item.poz==4" :txt="item.txt" :poz="item.poz"></carline>
    </div>
    <br />
    <div @click="move_all()">Click</div>
  </div>
</template>

<script>
import carline from "./carline.vue";
export default {
  name: "carousel",
  components: {
    carline
  },
  props: {},
  data() {
    return {
      txt_array: [
        { txt: "text1", poz: 0 },
        { txt: "text2", poz: 0 },
        { txt: "text3", poz: 0 },
        { txt: "text4", poz: 0 },
        { txt: "text5", poz: 0 },
        { txt: "text6", poz: 0 },
        { txt: "text7", poz: 0 },
        { txt: "text8", poz: 0 },
        { txt: "text9", poz: 0 }
      ]
    };
  },
  mounted() {
    //set initial values
    this.txt_array.forEach((item, index) => {
      item.poz = index;
    });
    //repeat move function
    this.move_all();
  },
  methods: {
    move_one() {
      let len = this.txt_array.length;
      this.txt_array.forEach((item, index) => {
        if (item.poz == 0) item.poz = len;
        item.poz--;
      });
    },
    move_all() {
      let vueOBJ = this;
      var ran1 = Math.floor(Math.random() * 20) + 20;
      for (var i = 0; i < ran1; i++) {
        setTimeout(function() {
          vueOBJ.move_one();
        }, i * 10 * Math.abs(ran1 / 2 - i));
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
