<template>
  <div id="app">
<!--    <FabricCanvas />-->

    <div class="Con">
      <div class="SmesBlock" :style="{ 'background-color': Smes}"> </div>
      <div class="FormBlock" :style="{ 'background-color': Form}"> </div>
      <div class="ColdBlock" :style="{ 'background-color': Cold}"> </div>
      <div class="UpBlock" :style="{ 'background-color': Up}"> </div>
      <div class="HotBlock" :style="{ 'background-color': Hot}"> </div>
      <div class="BoxBlock" :style="{ 'background-color': Box}"> </div>

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
        <button class="ButtonWarn">Формовка Авария</button>
      </div>

      <div class="ColdControl">
        <button class="ButtonOn"
        @click = 'ColdOn'
        >Охлаждение Вкл</button>
        <button class="ButtonOff"
        @click = 'ColdStop'
        >Охлаждение Стоп</button>
        <button class="ButtonWarn">Охлаждение Авария</button>
      </div>

      <div class="UpControl">
        <button class="ButtonOn"
        @click = 'UpOn'
        >Извлечение Вкл</button>
        <button class="ButtonOff"
        @click = 'UpStop'
        >Извлечение Стоп</button>
        <button class="ButtonWarn">Извлечение Авария</button>
      </div>

      <div class="HotControl">
        <button class="ButtonOn"
        @click = 'HotOn'
        >Сушка Вкл</button>
        <button class="ButtonOff"
         @click = 'HotStop'>Сушка Стоп</button>
        <button class="ButtonWarn">Сушка Авария</button>
      </div>

      <div class="BoxControl">
        <button class="ButtonOn"
        @click = 'BoxOn'
        >Упаковка Вкл</button>
        <button class="ButtonOff"
        @click = 'BoxStop'
        >Упаковка Стоп</button>
        <button class="ButtonWarn">Упаковка Авария</button>
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
  Smes.value = "red";
  // setTimeout(function() {
  //   Smes.value = 'black';
  //   setInterval(function() {
  //     Smes.value = 'red';
  //
  //   }, 500)
  // }, 3000)

 }

</script>

<style scoped>
.Con {
  background-color: grey;
  width: 900px;
  height: 90px;
  position: absolute;
  left: 23%;
  top: 18%;
  display: flex;


}


.ControlButtonPlate {
  position: absolute;
  background-color: black;
  width: 520px;
  height: 225px;
  left: 32.5%;
  top: 28%;
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
</style>

