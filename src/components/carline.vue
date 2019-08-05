<template>
  <div
    class="cont1"
    v-bind:class="{ 'center2': poz==0||poz==4, 'center1': poz==1||poz==3, 'center0': poz==2 }"
  >{{txt}}</div>
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
  width: 400px;
  max-width: 90vw;
}
.center2 {
  font-size: 15px;
  opacity: 0.75;
  filter: blur(2px);
}
.center1 {
  font-size: 22px;
  opacity: 0.85;
  filter: blur(1.5px);
}
.center0 {
  font-size: 30px;
}
.center0 {
    animation: example 1s cubic-bezier(0.150, 0.750, 0.950, 0.950) both;
}
@keyframes example {
  0% {
     transform: rotate(0deg) translate(0px,0px);
  }
  90% {
     transform: rotate(0deg) translate(0px,-5px);
  }
  100% {
     transform: rotate(0deg) translate(0px,0px);
  }
}
.center1 {
    animation: example1 1s cubic-bezier(0.150, 0.750, 0.950, 0.950) both;
}
@keyframes example1 {
  0% {
     transform: rotate(0deg) translate(0px,0px);
  }
  90% {
     transform: rotate(0deg) translate(0px,-2.5px);
  }
  100% {
     transform: rotate(0deg) translate(0px,0px);
  }
}
</style>
