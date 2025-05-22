<template>
  <div id="app">
<!--    <FabricCanvas />-->
    <div id="Bear">
      <img id ='bear1' :src = bearStyleSrc
           :style="{ 'left':bearStylePosLeft, 'top':bearStylePosTop, 'height':bearStyleStyleHeight, 'width':bearStyleStyleWidth,
           'z-index': bearStyleStyleZ, 'transform': `rotate(${bearRotate}deg)` }"
           style="position: relative"

      >
    </div>
    <div class="Con">
      <div id="left"></div>
      <div id="right"></div>
      <div class="SmesBlock" :style="{ 'background-color': Smes}"> <p>Смеситель</p>
      <div class="SmesTech">

        <div id="TopS">
          <div id="SmesRPMtar">
            <p id="RpmTxt">RPM: {{RPMnumSmes}}</p>
          </div>
          <div class="water">
            <div class="ripple-one"></div>
            <div class="ripple-two"></div>
            <div class="ripple-three"></div>

          </div>

        </div>
        <div id="middleS">


        </div>
        <div id="bottomS" >
          <img id="picTurS" :style="{ 'transform': `rotate(${bottomSRotate}deg)`}" src="https://cdn2.iconfinder.com/data/icons/drone-applications/512/turbine-1024.png">

        </div>
      </div>
      </div>
      <div class="FormBlock" :style="{ 'background-color': Form}"> <p>Формовка</p>
        <div class="FormTech">
          <div id="TopF"></div>
          <div   id="middleF">
            <div ref="udm" id="middleF1" ></div>
            <div id="bottomF"></div>
          </div>
      </div>
      </div>
      <div class="ColdBlock" :style="{ 'background-color': Cold}"> <p>Охлаждение</p>
        <div class="ColdTech">
          <div id="TopC"></div>
          <div id="middleC"></div>
          <div  id="bottomC">
            <img id="picTurC" :style="{ 'transform': `rotate(${bottomCRotate}deg)`}" src="https://avatars.mds.yandex.net/i?id=06d4eb0640f97077a81e81bce482bda907cdbbf0-5194765-images-thumbs&n=13">
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
          <div  id="bottomH" :style="{ 'background-color': Hot1}"></div>
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
        :style="{'cursor': SmesButtOn}"
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
                :style="{'cursor': FormButtOn}"
        >Формовка Вкл</button>
        <button class="ButtonOff"
                @click = 'FormStop'
        >Формовка Стоп</button>
        <button class="ButtonWarn"
        @click = 'FormWarn'
        >Формовка Авария</button>
      </div>

      <div class="ColdControl">
        <button class="ButtonOn"
        @click = 'ColdOn'
                :style="{'cursor': ColdButtOn}"
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
                :style="{'cursor': UDButtOn}"
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
                :style="{'cursor': HotButtOn}"
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
                :style="{'cursor': BoxButtOn}"
        >Упаковка Вкл</button>
        <button class="ButtonOff"
        @click = 'BoxStop'
        >Упаковка Стоп</button>
        <button class="ButtonWarn"
                @click = 'BoxWarn'
        >Упаковка Авария</button>
      </div>
      <a
        href = "http://www.evraz.com/ru"
        class="Txt">Control Panel</a>
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
let SmesButtOn = ref('')
let Smes = ref('')
let Form = ref('')
let Cold = ref('')
let Up = ref('')
let Hot = ref('')
let Hot1 = ref("")
let Box = ref('')
let bottomSRotate = ref(0)
let bottomCRotate = ref(0)
let interval = ref()
let interval2 = ref()
let interval3 = ref()
let interval4 = ref()
let interval5 = ref()
let interval6 = ref()
let intervalhot = ref()


let udm = ref()
Smes.value = "#21BA45"
Form.value = "#21BA45"
Cold.value = "#21BA45"
Up.value = "#21BA45"
Hot.value = "#21BA45"
Box.value = "#21BA45"
Hot1.value = "rgb(250, 50, 50, 45%)"

let bearStyleSrc = ref("")
let bearStyleStyleHeight = ref("")
let bearStyleStyleWidth = ref("")
let bearStylePosLeft = ref("")
let bearStylePosTop = ref("")
let bearStyleStyleZ = ref("")
let bearRotate = ref("")
let TimeStop1 = ref()
let TimeStop2 = ref()
let TimeStop3 = ref()
let TimeStop4 = ref()
let TimeStop5 = ref()
let TimeStop = ref()
let RPMnumSmes = 0
let TimeStopInt = ref()


let NumberPos = 0
function pos1() {
  bearStyleSrc.value = 'https://media.teradom.ru/images/39/198.jpg'
  bearStylePosLeft.value = 0 + "px"
  bearStylePosTop.value = 0 + "px"
  bearStyleStyleHeight.value = 20 + "px"
  bearStyleStyleWidth.value = 120 + "px"
}
function pos2() {
  bearStylePosLeft.value = 140 + "px"
  bearStylePosTop.value = 14 + "px"
  bearStyleStyleHeight.value = 20 + "px"
  bearStyleStyleWidth.value = 120 + "px"
}
function pos3() {
  bearStylePosLeft.value = 280 + "px"
  bearStylePosTop.value = 18 + "px"
  bearStyleStyleHeight.value = 20 + "px"
  bearStyleStyleWidth.value = 120 + "px"
}
function pos4() {
  bearStyleStyleHeight.value = 25 + "px"
  bearStyleStyleWidth.value = 40 + "px"
  bearStylePosLeft.value = 459 + "px"
  bearStylePosTop.value = -10 + "px"
  bearStyleSrc.value = "https://media.istockphoto.com/id/1302390177/ru/%D0%B2%D0%B5%D0%BA%D1%82%D0%BE%D1%80%D0%BD%D0%B0%D1%8F/%D0%BE%D1%80%D0%B0%D0%BD%D0%B6%D0%B5%D0%B2%D1%8B%D0%B9-%D0%BA%D0%BB%D0%B5%D0%B9%D0%BA%D0%B8%D0%B9-%D0%BC%D0%B5%D0%B4%D0%B2%D0%B5%D0%B4%D1%8C-%D0%B6%D0%B5%D0%BB%D0%B5-%D1%81%D0%BB%D0%B0%D0%B4%D0%BA%D0%B8%D0%B5-%D0%BA%D0%BE%D0%BD%D1%84%D0%B5%D1%82%D1%8B-%D1%81-%D1%83%D0%B4%D0%B8%D0%B2%D0%B8%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%BC-%D0%B2%D0%BA%D1%83%D1%81%D0%BE%D0%BC-%D0%BF%D0%BB%D0%BE%D1%81%D0%BA%D0%B8%D0%B9-%D1%81%D1%82%D0%B8%D0%BB%D1%8C-%D0%B4%D0%B8%D0%B7%D0%B0%D0%B9%D0%BD.jpg?s=612x612&w=0&k=20&c=Kd9x56zTT8NoEQPS4txp4XFVdIca29zq8MhdvuKUw38="

}
function pos5() {
  bearStyleStyleHeight.value = 25 + "px"
  bearStyleStyleWidth.value = 40 + "px"
  bearStylePosLeft.value = 603 + "px"
  bearStylePosTop.value = 0 + "px"
  bearRotate.value = "90"
}
function pos6() {
  bearStyleStyleHeight.value = 45 + "px"
  bearStyleStyleWidth.value = 45 + "px"
  bearStylePosLeft.value = 747 + "px"
  bearStylePosTop.value = -39 + "px"
  bearRotate.value = "0"
  bearStyleSrc.value = "https://avatars.mds.yandex.net/get-mpic/4304254/2a0000018a5e9a3a25e166314e5f55102e92/optimize"
}


bearStyleSrc.value = 'https://media.teradom.ru/images/39/198.jpg'
function BearTravel() {
pos1()
  NumberPos = 1
  console.log(NumberPos)
  TimeStop1.value = setTimeout(() => {
    pos2()
    NumberPos = 2
    console.log(NumberPos)
    }, 3000)
  TimeStop2.value = setTimeout(() => {
    pos3()
    NumberPos = 3
    console.log(NumberPos)
    }, 6000)
  TimeStop3.value = setTimeout(() => {
    pos4()
    NumberPos = 4
    console.log(NumberPos)
 }, 9000)
  TimeStop4.value =  setTimeout(() => {
    pos5()
    NumberPos = 5
    console.log(NumberPos)
    }, 12000)
  TimeStop5.value = setTimeout(() => {
    pos6()
    NumberPos = 6
    console.log(NumberPos)
 }, 15000)
}
BearTravel()
function BearTravelInterval() {
  TimeStopInt.value = setInterval(() => {
    BearTravel()
  }, 18000)
}
BearTravelInterval()
function RunBearTravel() {
  if (NumberPos === 1) {
     setTimeout(() => {
      pos2()
       BearTravelInterval()
      console.log(NumberPos)
    }, 3000)
     setTimeout(() => {
      pos3()

      console.log(NumberPos)
    }, 6000)
     setTimeout(() => {
      pos4()

      console.log(NumberPos)
    }, 9000)
      setTimeout(() => {
      pos5()

      console.log(NumberPos)
    }, 12000)
     setTimeout(() => {
      pos6()

      console.log(NumberPos)
    }, 15000)
  }
//   if (NumberPos === 2) {
//     pos3()
//     pos4()
//     pos5()
//     pos6()
//   }
//   if (NumberPos === 3) {
//     pos4()
//     pos5()
//     pos6()
//   }
//   if (NumberPos === 4) {
//     pos5()
//     pos6()
//   }
//   if (NumberPos === 5) {
//     pos6()
//   }
//   if (NumberPos === 6) {
// pos1()
//   }
}

let numberTime = ref()
let FormButtOn = ref()
let ColdButtOn = ref()
let UDButtOn = ref()
let HotButtOn = ref()
let BoxButtOn = ref()


function ActionIfButt() {
  setInterval(() => {
    if (Smes.value === "#21BA45") {
      SmesButtOn.value = "not-allowed"
    } else {
      SmesButtOn.value = "pointer"
    }
    if (Form.value === "#21BA45") {
      FormButtOn.value = "not-allowed"
    } else {
      FormButtOn.value = "pointer"
    }
    if (Cold.value === "#21BA45") {
      ColdButtOn.value = "not-allowed"
    } else {
      ColdButtOn.value = "pointer"
    }
    if (Up.value === "#21BA45") {
      UDButtOn.value = "not-allowed"
    } else {
      UDButtOn.value = "pointer"
    }
    if (Hot.value === "#21BA45") {
      HotButtOn.value = "not-allowed"
    } else {
      HotButtOn.value = "pointer"
    }
    if (Box.value === "#21BA45") {
      BoxButtOn.value = "not-allowed"
    } else {
      BoxButtOn.value = "pointer"
    }
}, 99)
}
ActionIfButt()
function UDForm() {
  setInterval(() => {
    if (numberTime.value === 0) {
      let rect = udm.value.getBoundingClientRect()
      let newTop = rect.height = 90
      udm.value.style.height = newTop + 'px'
    }
    if (numberTime.value === 1) {
      let rect = udm.value.getBoundingClientRect()
      let newTop = rect.height = 100
      udm.value.style.height = newTop + 'px'
    }
  }, 1)
  // console.log(1)
  setInterval(() => {
    // console.log(1.5)
      if (Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      let rect = udm.value.getBoundingClientRect()
      let newTop = rect.height + 10
      udm.value.style.height = newTop + 'px'
        numberTime.value = 1
    }
  }, 900)
  // console.log(2)
  setInterval(() => {
    if (Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      // console.log(2.5)
      let rect = udm.value.getBoundingClientRect()
      let newTop = rect.height - 20
      udm.value.style.height = newTop + 'px'
      numberTime.value = 0
    }

  }, 1800)
  // console.log(3)
}
UDForm()

function SmesStop() {
  Smes.value = 'orangered'
  clearInterval(interval.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStopInt.value)
  clearInterval(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0

}
function FormStop() {
  Form.value = 'orangered'
  clearInterval(interval2.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}
function ColdStop() {
  Cold.value = 'orangered'
  clearInterval(interval3.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}
function UpStop() {
  Up.value = 'orangered'
  clearInterval(interval4.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}
function HotStop() {
  Hot.value = 'orangered'
  clearInterval(interval5.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}
function BoxStop() {
  Box.value = 'orangered'
  clearInterval(interval6.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}

function SmesOn() {
  Smes.value = "#21BA45"
  // setInterval(TimeStopInt.value)
  // setTimeout(TimeStop1.value)
  // setTimeout(TimeStop2.value)
  // setTimeout(TimeStop3.value)
  // setTimeout(TimeStop4.value)
  // setTimeout(TimeStop5.value)
  clearInterval(interval.value)
  // BearTravelInterval()
  RunBearTravel()
}
function FormOn() {
  Form.value = "#21BA45"
  clearInterval(interval2.value)
}
function ColdOn() {
  Cold.value = "#21BA45"
  clearInterval(interval3.value)
}
function UpOn() {
  Up.value = "#21BA45"
  clearInterval(interval4.value)
}
function HotOn() {
  Hot.value = "#21BA45"
  clearInterval(interval5.value)
}
function BoxOn() {
  Box.value = "#21BA45"
  clearInterval(interval6.value)
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
  Hot1.value = "rgb(250, 50, 50, 45%)"
  RPMnumSmes = 0
}

function FormWarn() {
  interval2.value = setInterval(() => {
    if (Form.value === 'black') {
      Form.value = 'red'
    }
    else {
      Form.value = 'black'

    }
  }, 500)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}

function ColdWarn() {
  interval3.value = setInterval(() => {
    if (Cold.value === 'black') {
      Cold.value = 'red'
    }
    else {
      Cold.value = 'black'

    }
  }, 500)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}
function UpWarn() {
  interval4.value = setInterval(() => {
    if (Up.value === 'black') {
      Up.value = 'red'
    }
    else {
      Up.value = 'black'

    }
  }, 500)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}
function HotWarn() {
  interval5.value = setInterval(() => {
    if (Hot.value === 'black') {
      Hot.value = 'red'
    }
    else {
      Hot.value = 'black'

    }
  }, 500)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}
function BoxWarn() {
  interval6.value = setInterval(() => {
    if (Box.value === 'black') {
      Box.value = 'red'
    }
    else {
      Box.value = 'black'

    }
  }, 500)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearTimeout(TimeStop1.value)
  clearTimeout(TimeStop2.value)
  clearTimeout(TimeStop3.value)
  clearTimeout(TimeStop4.value)
  clearTimeout(TimeStop5.value)
  RPMnumSmes = 0
}

function rotateBottomS() {
  setInterval(() => {
    if( Smes.value === "#21BA45" & Form.value ==="#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45")
    bottomSRotate.value += 5
  }, 25)
}

rotateBottomS()
function rotateBottomC() {
  setInterval(() => {
    if( Smes.value === "#21BA45" & Form.value ==="#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45")
    bottomCRotate.value += 15
  }, 25)
}
function hot() {
  intervalhot.value = setInterval(() => {
    if( Smes.value === "#21BA45" & Form.value ==="#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45"){
    if (Hot1.value === "rgb(250, 50, 50, 45%)") {
      Hot1.value = "rgb(250, 50, 50, 69%)"
    }
    else {
      Hot1.value = "rgb(250, 50, 50, 45%)"

    }  }
  }, 900)

}
hot()
rotateBottomC()

function SmesRPM() {
  setInterval(() => {
    if( Smes.value === "#21BA45" & Form.value ==="#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      RPMnumSmes = 100
      RPMnumSmes = RPMnumSmes + 5
      setTimeout(() => {
        RPMnumSmes = RPMnumSmes - 5
      }, 400)
      setTimeout(() => {
        RPMnumSmes = RPMnumSmes - 5
      }, 800)
      setTimeout(() => {
        RPMnumSmes = RPMnumSmes + 5
      }, 1200)
      setTimeout(() => {
        RPMnumSmes = RPMnumSmes + 5
      }, 1600)
      setTimeout(() => {
        RPMnumSmes = RPMnumSmes - 5
      }, 200)
    }
},2500)
}
SmesRPM()
</script>

<style scoped>
.Txt {
  text-decoration: Canvas;
  cursor: context-menu;
}
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

#left{
  position: relative;
  width: 3px;
  height: 25px;
  background-color: #1D1D1D;
  left: 27px;
  bottom: 25px;

}
#right{
  left: 137px;
  bottom: 25px;
  position: relative;
  width: 3px;
  height: 25px;
  background-color: rgb(40, 40, 40, 75%);
  backdrop-filter: blur(3px);
}

#Bear {
  position: relative;
  height: 50px;
  width: 120px;
  left: 255px;
  top: 310px;
  z-index: -2;

}
#bear1 {
  height: 20px;
  width: 120px;
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
#SmesRPMtar{
  height: 20px;
  width: 70px;
  background-color: black;
  position: relative;
  bottom: 20px;
  font-size: 15px;

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
#middleF1 {
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
  background-color: rgb(30, 30, 30, 5%);
  backdrop-filter: blur(10px);
  z-index: -3;
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

