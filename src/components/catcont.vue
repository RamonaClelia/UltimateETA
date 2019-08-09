<template>
  <div class="ContBig">
    <canvas id="mycanv"  v-on:mousemove="getelem($event) " :width="canvx" :height="canvy"></canvas>
    <!-- v-on:mousemove="draw($event) " -->
  </div>
</template>

<script>
import vueCanvasNest from "vue-canvas-nest";
import { debuglog } from "util";
export default {
  name: "catcont",
  props: {},
  data() {
    return {
      canvx: 500,
      canvy: 500,
      ballx: 50,
      bally: 50,
      ballr: 30,
      billyr: 20,
      movetype: 0,
      mousex: 0,
      mousey: 0,
      exampleContent: "Start",
      evt: {}
    };
  },
  methods: {
    updateCanvas() {
      var canvas = document.getElementById("mycanv"),
        ctx = canvas.getContext("2d");
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = "black";
      ctx.font = "20px Georgia";
      ctx.fillText(this.exampleContent, 10, 50);
    },
    getMousePos(canvas, evt) {
      var canvas = document.getElementById("mycanv");
      var rect = canvas.getBoundingClientRect();
      return {
        x:
          ((evt.clientX - rect.left) / (rect.right - rect.left)) * canvas.width,
        y: ((evt.clientY - rect.top) / (rect.bottom - rect.top)) * canvas.height
      };
    },
    getelem(e){
      this.evt=e;
    },
    draw(e) {
      var canvas = document.getElementById("mycanv"),
        ctx = canvas.getContext("2d");

      //clear canvas
      ctx.clearRect(0, 0, this.canvx, this.canvy);

      //get dots
      var pos = this.getMousePos(canvas, e);

      this.mousex = pos.x;
      this.mousey = pos.y;
      ctx.fillStyle = "#000000";

      // draw small ball
      //console.log(this.mousex, this.mousey);
      //ctx.fillRect(this.mousex, this.mousey, 4, 4);
      ctx.beginPath();
      ctx.arc(this.mousex, this.mousey, this.billyr, 0, 2 * Math.PI);
      ctx.stroke();

      //draw the big ball/cat

      this.draw_cat(canvas,ctx);
      // ctx.beginPath();
      // ctx.arc(this.ballx, this.bally, this.ballr, 0, 2 * Math.PI);
      // ctx.stroke();
    },
    draw_cat(canvas, ctx){
      console.log('cat');
      ////if circle
      // ctx.beginPath();
      // ctx.arc(this.ballx, this.bally, this.ballr, 0, 2 * Math.PI);
      // ctx.stroke();
      
      ////if cat
      //head
      ctx.strokeStyle="black"
      ctx.beginPath();
      ctx.arc(this.ballx, this.bally, this.ballr, 0, 2 * Math.PI);
      ctx.stroke();
      ctx.fill();
      //ear left
      ctx.beginPath();
      ctx.moveTo(this.ballx, this.bally);
      ctx.lineTo(this.ballx-30, this.bally-40);
      ctx.lineTo(this.ballx-30, this.bally);
      ctx.lineTo(this.ballx, this.bally);
      ctx.stroke();
      ctx.fill();
      //ear right
      ctx.beginPath();
      ctx.moveTo(this.ballx, this.bally);
      ctx.lineTo(this.ballx+30, this.bally-40);
      ctx.lineTo(this.ballx+30, this.bally);
      ctx.lineTo(this.ballx, this.bally);
      ctx.stroke();
      ctx.fill();
      //eye1 white
      ctx.fillStyle="white"
      ctx.beginPath();
      ctx.arc(this.ballx-12, this.bally,8,2*Math.PI,0*Math.PI);
      ctx.stroke();
      ctx.fill();
      //eye2 white
      ctx.fillStyle="white"
      ctx.beginPath();
      ctx.arc(this.ballx+12, this.bally,8,2*Math.PI,0*Math.PI);
      ctx.stroke();
      ctx.fill();
      //eye1 black
      ctx.fillStyle="black"
      ctx.beginPath();
      ctx.arc(this.ballx-10, this.bally,4,2*Math.PI,0*Math.PI);
      ctx.stroke();
      ctx.fill();
      //eye2 black
      ctx.fillStyle="black"
      ctx.beginPath();
      ctx.arc(this.ballx+10, this.bally,4,2*Math.PI,0*Math.PI);
      ctx.stroke();
      ctx.fill();
      //eye1 white small
      ctx.fillStyle="white"
      ctx.beginPath();
      ctx.arc(this.ballx-9, this.bally+2,2,2*Math.PI,0*Math.PI);
      ctx.stroke();
      ctx.fill();
      //eye2 white small
      ctx.fillStyle="white"
      ctx.beginPath();
      ctx.arc(this.ballx+9, this.bally+2,2,2*Math.PI,0*Math.PI);
      ctx.stroke();
      ctx.fill();
      //nose
      ctx.fillStyle="brown"
      ctx.beginPath();
      ctx.moveTo(this.ballx-5, this.bally+10);
      ctx.lineTo(this.ballx+5, this.bally+10);
      ctx.lineTo(this.ballx, this.bally+2.5+10);
      ctx.lineTo(this.ballx-5, this.bally+10);
      ctx.stroke();
      ctx.fill(); 
      //thonga
      if (Math.abs(this.mousex-this.ballx)<5 && Math.abs(this.mousey-this.bally)<5 ){
      ctx.strokeStyle="red"
      ctx.fillStyle="red"
      ctx.beginPath();
      ctx.ellipse(this.ballx-1.5, this.bally+5+10, 5, 7, Math.PI*0.1, Math.PI*2, Math.PI);
      // ctx.lineTo(this.ballx, this.bally+2.5+10);
      ctx.stroke();
      ctx.fill(); 
      }

      //wiskas left
      ctx.strokeStyle="white"
      ctx.fillStyle="black"
      ctx.beginPath();
      ctx.ellipse(this.ballx-5, this.bally+2.5+10, 5, 3, 0, Math.PI*2, Math.PI);
      // ctx.lineTo(this.ballx, this.bally+2.5+10);
      ctx.stroke();
      ctx.fill(); 
      //wiskas right
      ctx.strokeStyle="white"
      ctx.fillStyle="black"
      ctx.beginPath();
      ctx.ellipse(this.ballx+5, this.bally+2.5+10, 5, 3, 0, Math.PI*2, Math.PI);
      // ctx.lineTo(this.ballx, this.bally+2.5+10);
      ctx.stroke();
      ctx.fill(); 

      // var x=this.ballx;
      // var y=this.bally;
      //   ctx.beginPath();
      //   ctx.moveTo(40+x, 73+y);
      //   ctx.ellipse(38+x, 50+y, 30, 20,  Math.PI*0.3,0, Math.PI);
      //   ctx.lineTo(20+x, 25+y);
      //   ctx.lineTo(20+x, 10+y);
      //   ctx.lineTo(30+x, 20+y);
      //   // ctx.arc(50,20,10,Math.PI,0*Math.PI);
      //   //void ctx.ellipse(x, y, radiusX, radiusY, rotation, startAngle, endAngle [, anticlockwise]);
      //   ctx.ellipse(50+x, 20+y, 20, 10, 0, Math.PI, 0);
      //   ctx.lineTo(70+x, 20+y);
      //   ctx.lineTo(80+x, 10+y);
      //   ctx.lineTo(80+x, 25+y);
      //   ctx.ellipse(62+x, 50+y, 30, 20,  Math.PI/1.4, Math.PI, 0);
      //   // ctx.fillStyle="blue";
      //   ctx.fill();
    }
  },
  watch: {
    exampleContent: function(val, oldVal) {
      this.updateCanvas();
    }
  },
  mounted: function() {
    // window.addEventListener('mousemove', this.draw(event), false);
    this.updateCanvas();
    //set interval
    const interval = setInterval(() => {
      // console.log('x');
      if (this.ballx>this.mousex){
        this.ballx--;
      }
      if (this.ballx<this.mousex){
        this.ballx++;
      }
      if (this.bally>this.mousey){
        this.bally--;
      }
      if (this.bally<this.mousey){
        this.bally++;
      }
      this.draw(this.evt);
      // if (secondsToCountDown === 0) {
      //   clearInterval(interval); // time is up
      // }

    }, 10);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.ContBig {
  /* background-color: floralwhite; */
  /* border: 1px solid darkblue; */
}
#mycanv {

  width: 500px;
  height: 500px;
  max-width: 80vmin;
  max-height: 80vmin;

  background: white;
  border: 10px solid gray;
  border-style: outset;
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14),
    0 3px 1px -2px rgba(0, 0, 0, 0.12), 0 1px 5px 0 rgba(0, 0, 0, 0.2);
}
</style>
