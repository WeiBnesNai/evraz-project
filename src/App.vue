<template>
  <div id="app">
<!--    <FabricCanvas />-->

    <div class="Con">
      <div class="SmesBlock" :style="{ 'background-color': Smes}"> <p>Смеситель</p>
      <div class="SmesTech">
        <div id="TopS">
          <div class="water">
            <div class="ripple-one"></div>
            <div class="ripple-two"></div>
            <div class="ripple-three"></div>
          </div>

        </div>
        <div id="middleS"></div>
        <div id="bottomS" >
          <img id="picTurS" :style="{ 'transform': `rotate(${bottomSRotate}deg)`}" src="https://cdn2.iconfinder.com/data/icons/drone-applications/512/turbine-1024.png">

        </div>
      </div>
      </div>
      <div class="FormBlock" :style="{ 'background-color': Form}"> <p>Формовка</p>
        <div class="FormTech">
          <div id="TopF"></div>
          <div id="middleF"></div>
          <div id="bottomF"></div>
      </div>
      </div>
      <div class="ColdBlock" :style="{ 'background-color': Cold}"> <p>Охлождение</p>
        <div class="ColdTech">
          <div id="TopC"></div>
          <div id="middleC"></div>
          <div  id="bottomC">
            <img id="picTurC" :style="{ 'transform': `rotate(${bottomCRotate}deg)`}" src="https://avatars.mds.yandex.net/i?id=06d4eb0640f97077a81e81bce482bda907cdbbf0-5194765-images-thumbs&n=13"
          </div>
        </div>
      </div>
      <div class="UpBlock" :style="{ 'background-color': Up}"> <p>Извлечение</p>
        <div class="UpTech">
          <div id="TopU"></div>
          <div id="middleU"></div>
          <div  id="bottomU"></div>
        </div>
      </div>
      <div class="HotBlock" :style="{ 'background-color': Hot}"> <p>Сушка</p>
        <div class="HotTech">
          <div id="TopH"></div>
          <div id="middleH"></div>
          <div  id="bottomH"></div>
        </div>
      </div>
      <div class="BoxBlock" :style="{ 'background-color': Box}"> <p>Упаковка</p>
        <div class="BoxTech">
          <div id="TopB"></div>
          <div id="middleB"></div>
          <div  id="bottomB"></div>
        </div>
      </div>

    </div>



    <div class="ControlButtonPlate">


        <div class="ControlSmesitel">
<button class="ButtonOn"
@click = 'SmesOn'
>Смеситель Вкл</button>
      <button class="ButtonOff"
      @click ='SmesStop'
      >Смеситель Стоп</button>
      <button class="ButtonWarn"
      @click = 'SmesWarn'
      >Смеситель Авария</button>
    </div>

      <div class="FormControl">
        <button class="ButtonOn"
        @click = 'FormOn'
        >Формовка Вкл</button>
        <button class="ButtonOff"
                @click = 'FormStopp'
        >Формовка Стоп</button>
        <button class="ButtonWarn"
        @click = 'FormWarn'
        >Формовка Авария</button>
      </div>

      <div class="ColdControl">
        <button class="ButtonOn"
        @click = 'ColdOn'
        >Охлаждение Вкл</button>
        <button class="ButtonOff"
        @click = 'ColdStop'
        >Охлаждение Стоп</button>
        <button class="ButtonWarn"
                @click = 'ColdWarn'
        >Охлаждение Авария</button>
      </div>

      <div class="UpControl">
        <button class="ButtonOn"
        @click = 'UpOn'
        >Извлечение Вкл</button>
        <button class="ButtonOff"
        @click = 'UpStop'
        >Извлечение Стоп</button>
        <button class="ButtonWarn"
                @click = 'UpWarn'
        >Извлечение Авария</button>
      </div>

      <div class="HotControl">
        <button class="ButtonOn"
        @click = 'HotOn'
        >Сушка Вкл</button>
        <button class="ButtonOff"
         @click = 'HotStop'>Сушка Стоп</button>
        <button class="ButtonWarn"
                @click = 'HotWarn'
        >Сушка Авария</button>
      </div>

      <div class="BoxControl">
        <button class="ButtonOn"
        @click = 'BoxOn'
        >Упаковка Вкл</button>
        <button class="ButtonOff"
        @click = 'BoxStop'
        >Упаковка Стоп</button>
        <button class="ButtonWarn"
                @click = 'BoxWarn'
        >Упаковка Авария</button>
      </div>
      <button class="Txt">Control Panel</button>
    </div>



  </div>
</template>
<script setup>
import { ref } from 'vue'
// import FabricCanvas from './components/FabricCanvas.vue';
// export default {
//   name: 'App',
//   components: {
//     FabricCanvas,
//   },
// };

let Smes = ref('')
let Form = ref('')
let Cold = ref('')
let Up = ref('')
let Hot = ref('')
let Box = ref('')
let bottomSRotate = ref(0)
let bottomCRotate = ref(0)
let interval = ref()

function SmesStop() {
  Smes.value = 'orangered'
}
function FormStopp() {
  Form.value = 'orangered'
}
function ColdStop() {
  Cold.value = 'orangered'
}
function UpStop() {
  Up.value = 'orangered'
}
function HotStop() {
  Hot.value = 'orangered'
}
function BoxStop() {
  Box.value = 'orangered'
}

function SmesOn() {
  Smes.value = "#21BA45"
  clearInterval(interval.value)

}
function FormOn() {
  Form.value = "#21BA45"

}
function ColdOn() {
  Cold.value = "#21BA45"
}
function UpOn() {
  Up.value = "#21BA45"
}
function HotOn() {
  Hot.value = "#21BA45"
}
function BoxOn() {
  Box.value = "#21BA45"
}
function SmesWarn() {
  interval.value = setInterval(() => {
    if (Smes.value === 'black') {
      Smes.value = 'red'
    }
    else {
      Smes.value = 'black'

    }
  }, 500)
}


  // setTimeout(function() {
  //   Smes.value = 'black';
  //   setInterval(function() {
  //     Smes.value = 'red';
  //
  //   }, 500)
  // }, 3000)


function FormWarn() {
  Form.value = "red";
}
function ColdWarn() {
  Cold.value = "red";
}
function UpWarn() {
  Up.value = "red";
}
function HotWarn() {
  Hot.value = "red";
}
function BoxWarn() {
  Box.value = "red";
}


function rotateBottomS() {
  setInterval(() => {
    bottomSRotate.value += 5
  }, 25)
}

rotateBottomS()
function rotateBottomC() {
  setInterval(() => {
    bottomCRotate.value += 15
  }, 25)
  // setInterval(() => {
  //   bottomCRotate.value += 12
  // }, 125)
}

rotateBottomC()

</script>

<style scoped>
.Con {
  background-color: grey;
  width: 900px;
  height: 90px;
  position: absolute;
  left: 230px;
  top: 330px;
  display: flex;
  font-size: 18px;
  text-align: center;
  color: wheat;


}


.ControlButtonPlate {
  position: absolute;
  background-color: black;
  width: 520px;
  height: 225px;
  left: 375px;
  top: 425px;
  text-align: center;

}
.ControlSmesitel {
  font-size: 18px;
  position: relative;
  top: 3px;
}
.ButtonOn{
  background-color: white;
  color: #21BA45;
  border: #21BA45 solid 1px;
  cursor: pointer;

}
.ButtonOff{
  background-color: white;
  border: orangered solid 1px;
  color: orangered;
  cursor: pointer;

}
.ButtonWarn{
  background-color: white;
  border: red solid 1px;
  color: red;
  cursor: pointer;
}


.FormControl{
font-size: 18px;
  position: relative;
  top: 6px;
  z-index: 2;
}


.ColdControl{
  font-size: 18px;
  position: relative;
  top: 9px;
  z-index: 2;
}

.UpControl {
  font-size: 18px;
  position: relative;
  top: 12px;
  z-index: 2;
}

.HotControl {
  font-size: 18px;
  position: relative;
  top: 15px;
  z-index: 2;
}

.BoxControl {
  font-size: 18px;
  position: relative;
  top: 18px;
  z-index: 2;
}
.Txt {
  font-size: 18px;
  color: rgb(70, 70, 70, 50%);
  top: 14px;
  position: relative;
  text-align: center;
  background-color: black;
  border: 0;
  z-index: 1;
  height: 10px;
}


.SmesBlock {
  height: 82px;
  width: 120px;
  background-color: #21BA45;
  position: relative;
  left: 20px;
  top: 4px;
}

.FormBlock {
  height: 82px;
  width: 120px;
  background-color: #21BA45;
  position: relative;
  left: 40px;
  top: 4px;
}

.ColdBlock {
  height: 82px;
  width: 120px;
  background-color: #21BA45;
  position: relative;
  left: 60px;
  top: 4px;
}

.UpBlock {
  height: 82px;
  width: 120px;
  background-color: #21BA45;
  position: relative;
  left: 80px;
  top: 4px;
}

.HotBlock {
  height: 82px;
  width: 120px;
  background-color: #21BA45;
  position: relative;
  left: 100px;
  top: 4px;
}

.BoxBlock {
  height: 82px;
  width: 120px;
  background-color: #21BA45;
  position: relative;
  left: 120px;
  top: 4px;
}

.SmesTech{
  position: relative;
  bottom: 305px;
  left: 23px;
}
#TopS{
  background-color: grey;
  height: 120px;
  width: 70px;
}
#middleS {
  background-color: #1D1D1D;
  width: 30px;
  height: 90px;
 left: 18%;
  position: relative;
}
#bottomS{
  position: relative;
  width: 60px;
  height: 60px;
  left: 7px;
  //background-image: url("https://cdn2.iconfinder.com/data/icons/drone-applications/512/turbine-1024.png");
  //background-size: auto 100%;
  border: #1D1D1D 1px solid;
  z-index: -1;
}
#bottomCRotate {
  width: 60px;
  height: 60px;
}
#picTurS {
  width: 60px;
  height: 60px;
}

.FormTech{
  position: relative;
  bottom: 280px;
  left: 23px;
}

#TopF{
  background-color: grey;
  height: 120px;
  width: 70px;
}
#middleF {
  background-color: #1D1D1D;
  width: 30px;
  height: 90px;
  left: 18%;
  position: relative;
}
#bottomF{
  position: relative;
  width: 60px;
  height: 15px;
  background-color: #1D1D1D;
  left: 7px;
}

.ColdTech {
  position: relative;
  bottom: 280px;
  left: 23px;
}
#TopC{
  background-color: grey;
  height: 120px;
  width: 70px;
}
#middleC{
  background-color: #1D1D1D;
  width: 30px;
  height: 80px;
  left: 18%;
  position: relative;
}
#bottomC{
  position: relative;
  width: 45px;
  height: 45px;
  left: 14px;
  //background-image: url("https://avatars.mds.yandex.net/i?id=06d4eb0640f97077a81e81bce482bda907cdbbf0-5194765-images-thumbs&n=13");
  border: #1D1D1D 1px solid;
  //background-size: auto 100%;
  z-index: -1;
}
#picTurC{
  width: 31px;
  height: 31px;
  top: 6px;
  position: relative;
  z-index: -1;
}

.UpTech {
  position: relative;
  bottom: 290px;
  left: 23px;
}

#TopU{
  background-color: grey;
  height: 120px;
  width: 70px;
}
#middleU{
  background-color: #1D1D1D;
  width: 30px;
  height: 90px;
  left: 18%;
  position: relative;
}
#bottomU{
border: #1D1D1D solid 1px;
  width: 90px;
  height: 30px;
  position: relative;
  right: 7px;
  background-color: rgb(50, 50, 50, 25%);
  backdrop-filter: blur(10px);
}

.HotTech{
  position: relative;
  bottom: 290px;
  left: 23px;
}
#TopH{
  background-color: grey;
  height: 120px;
  width: 70px;
}
#middleH{
  background-color: #1D1D1D;
  width: 30px;
  height: 90px;
  left: 18%;
  position: relative;
}
#bottomH{
  border: orangered solid 1px;
  width: 90px;
  height: 15px;
  position: relative;
  right: 7px;
  background-color: rgb(250, 50, 50, 45%);
}

.BoxTech {
  position: relative;
  bottom: 210px;
  left: 23px;
}
#TopB{
  background-color: grey;
  height: 50px;
  width: 90px;
}
#middleB{
  background-color: #1D1D1D;
  width: 30px;
  height: 45px;
  left: 25%;
  position: relative;
}
#bottomB{
  border: rgb(150,100, 20, 85%) 1px solid;
  width: 90px;
  height: 60px;
  position: relative;
  background-color: rgb(350,100, 20, 45%);
}

.water {
  position: relative;
  width: 45px;
  height: 72px;
  overflow: hidden;
  display: flex;
  justify-content: center;
  border-radius: 50px;
  box-shadow: 18px 18px 30px rgba(209, 217, 230, 1), -18px -18px 30px rgba(255, 255, 255, 1);
  transform: translate3d(0, 0, 0);
  left: 12px;
  top: 20px;
}

.water:after {
  content: "";
  display: block;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0%;
  border-radius: 50px;
  background: linear-gradient(
    transparent 0%,
    transparent 40%,
    hsla(0, 81%, 46%, 0.91) 100%
  );
  mix-blend-mode: color;
  z-index: 4;
  transform: translate3d(0, 0, 0);
}

.ripple-one {
  position: absolute;
  top: 20%;
  width: 52px;
  height: 52px;
  border-radius: 45%;
  transform-origin: 50% 48%;
  animation: water 5s infinite linear;
  background: hsla(16, 100%, 50%, 0.7);
  z-index: 3;
  transform: translate3d(0, 0, 0);
}

.ripple-two {
  position: absolute;
  width: 50px;
  height: 50px;
  border-radius: 42%;
  top: 20%;
  transform-origin: 50% 48%;
  animation: water 4s infinite linear;
  background: hsla(14, 100%, 50%, 0.4);
  z-index: 2;
}

.ripple-three {
  position: absolute;
  top: 20%;
  width: 65px;
  height: 65px;
  border-radius: 45%;
  transform-origin: 50% 48%;
  animation: water 6s infinite linear;
  background: hsla(342, 100%, 50%, 0.4);
  z-index: 1;
}

@keyframes water {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}


@keyframes spacing {
  0% {	letter-spacing: 0.7em; margin-left: 0.7em; }
  100% { letter-spacing: 1em; margin-left: 1em;}
}


</style>

