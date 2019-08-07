<template>
  <div class="container">
    <div class="cont_car">
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
    </div>

    <img alt="Vue logo" class="btn_img" src="../assets/push.png" @click="move_all()" />
    <div id="resultCont">
      <div class="resultTop" v-for="(res,indx) in topResults" :key="indx">{{res}}</div>
    </div>
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
      options: [
        "4h",
        "6h",
        "8h",
        "End of day",
        "1 day",
        "1-2 days",
        "2 days",
        "2-3 days",
        "End of week",
        "Early next week"
      ],
      txt_array: [],
      topResults: []
    };
  },
  mounted() {
    function shuffle(array) {
      array.sort(() => Math.random() - 0.5);
    }
    let vueObj = this;
    this.options.forEach(itm => {
      vueObj.txt_array.push({ txt: itm, poz: 0 });
    });
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
      var ran1 = Math.floor(Math.random() * 10) + 30;
      var count = 0;
      for (var i = 0; i < ran1; i++) {
        setTimeout(function() {
          vueOBJ.move_one();
          count++;
          if (count == ran1) {
            if (vueOBJ.topResults.length == 3) {
              vueOBJ.topResults.shift();
            }

            vueOBJ.topResults.push(
              vueOBJ.txt_array.find(elm => {
                return elm.poz == 2;
              }).txt
            );
          }
        }, i * 10 * Math.abs(ran1 / 2 - i * 0.55));
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn_img {
  width: 50vmin;
  max-width: 75px;
  margin: 20px 0px;
}
.btn_img:hover {
  background-image: radial-gradient(teal 20%, #dbefef 60%, transparent 60%);
  transform: scale(1.1);
  cursor: pointer;
}
.container {
  background: white;
  border: 10px solid gray;
  border-style: outset;
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14),
    0 3px 1px -2px rgba(0, 0, 0, 0.12), 0 1px 5px 0 rgba(0, 0, 0, 0.2);
}
.cont_car {
  border: 2px solid #359898;
  border-style: double;
  background-color: darkcyan;
}
#resultCont {
  display: flex;
  align-items: center;
  justify-content: space-around;
}
.resultTop {
  background-color: #aedcdc;
  padding: 5px;
  border-radius: 5px;
  margin: 5px 0px;
  font-weight: bold;
}
</style>
