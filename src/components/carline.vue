<template>
  <div
    class="cont1"
    v-bind:class="{ 'center2': poz==0||poz==4, 'center1': poz==1||poz==3, 'center0': poz==2 }"
  >{{poz}} {{txt}}</div>
</template>

<script>
export default {
  name: "carline",
  props: {
    txt: String,
    poz: Number
  },
  data() {
    return {};
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cont1 {
  border: 1px solid darkcyan;
  background-color: #aedcdc;
  border-radius: 5px;
}
.center2 {
  font-size: 15px;
  opacity: 0.75;
  filter: blur(1px);
}
.center1 {
  font-size: 22px;
  opacity: 0.85;
  filter: blur(1px);
}
.center0 {
  font-size: 30px;
}
</style>
