<template>
  <div class="container">
    <div v-for="item1 in txt_array" :key="item1.txt+'A'">
      <carline v-if="item1.poz==0" :txt="item1.txt" :poz="item1.poz"></carline>
    </div>
    <div v-for="item2 in txt_array" :key="item2.txt+'B'">
      <carline v-if="item2.poz==1" :txt="item2.txt" :poz="item2.poz"></carline>
    </div>
    <div v-for="item3 in txt_array" :key="item3.txt+'C'">
      <carline v-if="item3.poz==2" :txt="item3.txt" :poz="item3.poz"></carline>
    </div>
    <div v-for="item4 in txt_array" :key="item4.txt+'D'">
      <carline v-if="item4.poz==3" :txt="item4.txt" :poz="item4.poz"></carline>
    </div>
    <div v-for="item5 in txt_array" :key="item5.txt+'E'">
      <carline v-if="item5.poz==4" :txt="item5.txt" :poz="item5.poz"></carline>
    </div>
    <br />
    <img alt="Vue logo" class="btn_img" src="../assets/push.png" @click="move_all()"/> 
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
        { txt: "2h", poz: 0 },
        { txt: "4h", poz: 0 },
        { txt: "6h", poz: 0 },
        { txt: "8h", poz: 0 },
        { txt: "12h", poz: 0 },
        { txt: "16h", poz: 0 },
        { txt: "20h", poz: 0 },
        { txt: "24h", poz: 0 },
        { txt: "28h", poz: 0 },
        { txt: "32h", poz: 0 },
        { txt: "36h", poz: 0 },
        { txt: "40h", poz: 0 },
        { txt: "1 day", poz: 0 },
        { txt: "1-2 days", poz: 0 },
        { txt: "2 days", poz: 0 },
        { txt: "2-3 days", poz: 0 },
        { txt: "End of week", poz: 0 },
        { txt: "Early next week", poz: 0 },
        { txt: "ASAP", poz: 0 }
      ]
    };
  },
  mounted() {
    function shuffle(array) {
  array.sort(() => Math.random() - 0.5);
}
    //set initial values
    shuffle(this.txt_array);
    this.txt_array.forEach((item, index) => {
      item.poz = index;
    });
    //repeat move function
    // this.move_all();
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
      var ran1 = Math.floor(Math.random() * 10) + 40;
      console.log(ran1);
      for (var i = 0; i < ran1; i++) {
        setTimeout(function() {
          vueOBJ.move_one();
        }, i * 10 * Math.abs(ran1 / 2-i*0.95));
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn_img{
    width: 50vmin;
    max-width: 75px;
}
.btn_img:hover{
      background-image: radial-gradient(teal 20%, #dbefef 60%, transparent 60% );
      
     transform: scale(1.1);
}
</style>
