<template id="cont">



  <div id="app">
<!--    <FabricCanvas />-->
    <div id="container">
      <div id="BackGround"></div>
    <div id="Bear">
      <img id ='bear1' :src = bearStyleSrc
           :style="{ 'left':bearStylePosLeft, 'top':bearStylePosTop, 'height':bearStyleStyleHeight, 'width':bearStyleStyleWidth,
           'z-index': bearStyleStyleZ, 'transform': `rotate(${bearRotate}deg)` }"
           style="position: relative"

      >
    </div>
    <div class="Con">
      <div id="OwPanel"></div>

      <div id="left"></div>
      <div id="right"></div>
      <div class="SmesBlock" :style="{ 'background-color': Smes}">
        <p>Смеситель</p>
        <div id="SmesRPMtar">
          <p id="RpmTxt">RPM: {{RPMnumSmes}}</p>
        </div>
      <div class="SmesTech">

        <div id="TopS">

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
          <div id="TopC">

          </div>
          <div id="middleC"></div>
          <div  id="bottomC">
            <img id="picTurC" :style="{ 'transform': `rotate(${bottomCRotate}deg)`}" src="https://avatars.mds.yandex.net/i?id=06d4eb0640f97077a81e81bce482bda907cdbbf0-5194765-images-thumbs&n=13">
          </div>
          <div id="ColdTemp"
               :style="{ 'color': ColorTextTemp}">
            {{ColdTempNum}}°
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
          <div id="TopH">
            <div id="HotTime">
              {{HotTime}}:00
            </div>
          </div>
          <div id="middleH"></div>
          <div  id="bottomH" :style="{ 'background-color': Hot1}"></div>
          <div id="HotTempBlock">
            {{HotTemp}}°
          </div>
        </div>
      </div>
      <div class="BoxBlock" :style="{ 'background-color': Box}"> <p>Упаковка</p>
        <div class="BoxTech">
          <div id="TopB">
          </div>
          <div id="middleB"></div>
          <div  id="bottomB"></div>
        </div>
      </div>
    </div>
      <div id="ControlPanelBackGround"></div>
    <div class="ControlButtonPlate">
        <div class="ControlSmesitel">

<!--          Кнопки отвечающие за контроль блока "Смеситель"-->
<button class="ButtonOn"
        :style="{'cursor': SmesButtOn}"
@click = 'SmesOn'
>Смеситель Вкл</button>
      <button class="ButtonOff"
      @click ='SmesStop'
      >Смеситель Стоп</button>
      <button :style="{'cursor': SmesWarnCur}"  class="ButtonWarn"
      @click = 'SmesWarn'
      >Смеситель Авария</button>
    </div>

      <!--          Кнопки отвечающие за контроль блока "Формовка"-->
      <div class="FormControl">
        <button class="ButtonOn"
        @click = 'FormOn'
                :style="{'cursor': FormButtOn}"
        >Формовка Вкл</button>
        <button class="ButtonOff"
                @click = 'FormStop'
        >Формовка Стоп</button>
        <button :style="{'cursor': FormWarnCur}"  class="ButtonWarn"
        @click = 'FormWarn'
        >Формовка Авария</button>
      </div>

      <!--          Кнопки отвечающие за контроль блока "Охлаждение"-->
      <div class="ColdControl">
        <button class="ButtonOn"
        @click = 'ColdOn'
                :style="{'cursor': ColdButtOn}"
        >Охлаждение Вкл</button>
        <button class="ButtonOff"
        @click = 'ColdStop'
        >Охлаждение Стоп</button>
        <button :style="{'cursor': ColdWarnCur}"  class="ButtonWarn"
                @click = 'ColdWarn'
        >Охлаждение Авария</button>
      </div>

      <!--          Кнопки отвечающие за контроль блока "Извлечение"-->
      <div class="UpControl">
        <button class="ButtonOn"
        @click = 'UpOn'
                :style="{'cursor': UDButtOn}"
        >Извлечение Вкл</button>
        <button class="ButtonOff"
        @click = 'UpStop'
        >Извлечение Стоп</button>
        <button :style="{'cursor': UPWarnCur}"  class="ButtonWarn"
                @click = 'UpWarn'
        >Извлечение Авария</button>
      </div>

      <!--          Кнопки отвечающие за контроль блока "Сушка"-->
      <div class="HotControl">
        <button class="ButtonOn"
        @click = 'HotOn'
                :style="{'cursor': HotButtOn}"
        >Сушка Вкл</button>
        <button class="ButtonOff"
         @click = 'HotStop'>Сушка Стоп</button>
        <button :style="{'cursor': HotWarnCur}"  class="ButtonWarn"
                @click = 'HotWarn'
        >Сушка Авария</button>
      </div>

      <!--          Кнопки отвечающие за контроль блока "Упаковка"-->
      <div class="BoxControl">
        <button class="ButtonOn"
        @click = 'BoxOn'
                :style="{'cursor': BoxButtOn}"
        >Упаковка Вкл</button>
        <button class="ButtonOff"
        @click = 'BoxStop'
        >Упаковка Стоп</button>
        <button
          :style="{'cursor': BoxWarnCur}"
          class="ButtonWarn"
                @click = 'BoxWarn'
        >Упаковка Авария</button>
      </div>
      <a
        href = "http://www.evraz.com/ru"
        class="Txt">Control Panel</a>
    </div>

  </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
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
let ColdTempNum = 0
let HotTemp = 21
let HotTime = 0
let ColorTextTemp = ref("")

let SmesWarnCur = ref('')
let FormWarnCur = ref('')
let ColdWarnCur = ref('')
let UPWarnCur = ref('')
let HotWarnCur = ref('')
let BoxWarnCur = ref('')
let udm = ref()
Smes.value = "#21BA45"
Form.value = "#21BA45"
Cold.value = "#21BA45"
Up.value = "#21BA45"
Hot.value = "#21BA45"
Box.value = "#21BA45"
Hot1.value = "rgb(250, 50, 50, 45%)"
ColorTextTemp.value = 'rgb(250, 50, 50)'

let bearStyleSrc = ref("")
let bearStyleStyleHeight = ref("")
let bearStyleStyleWidth = ref("")
let bearStylePosLeft = ref("")
let bearStylePosTop = ref("")
let bearStyleStyleZ = ref("")
let bearRotate = ref("")
let RPMnumSmes = 72
let TimeStopInt = ref()

let rotateButtScont = ref()
let RPMsmesContr = ref()
let UDformOwContr = ref()
let UDformMidContr = ref()
let UDformBottContr = ref()

rotateBottomS()
SmesRPM()
let NumberPos = 1

// Функции позиций "Медведя"
// Смеситель
function pos1() {
  NumberPos = 1
  bearStyleSrc.value = 'https://media.teradom.ru/images/39/198.jpg'
  bearStylePosLeft.value = 0 + "px"
  bearStylePosTop.value = 0 + "px"
  bearStyleStyleHeight.value = 20 + "px"
  bearStyleStyleWidth.value = 120 + "px"
  RPMnumSmes = 72
  rotateBottomS()
  SmesRPM()
  HotTime = 0
}

// Формовка
function pos2() {
  NumberPos = 2
  bearStylePosLeft.value = 140 + "px"
  bearStylePosTop.value = 14 + "px"
  bearStyleStyleHeight.value = 20 + "px"
  bearStyleStyleWidth.value = 120 + "px"
  clearInterval(rotateButtScont.value)
  clearInterval(RPMsmesContr.value)
  RPMnumSmes = 0
  UDForm()

}

// Охлаждение
function pos3() {
  NumberPos = 3
  bearStylePosLeft.value = 280 + "px"
  bearStylePosTop.value = 18 + "px"
  bearStyleStyleHeight.value = 20 + "px"
  bearStyleStyleWidth.value = 120 + "px"
  RPMnumSmes = 0
  clearInterval(UDformOwContr.value)
  clearInterval(UDformMidContr.value)
  clearInterval(UDformBottContr.value)
  rotateBottomC()
  ColdHot()
  numberTime.value = 0
  let rect = udm.value.getBoundingClientRect()
  let newTop = rect.height = 90
  udm.value.style.height = newTop + 'px'
  clearInterval(rotateButtScont.value)
  clearInterval(RPMsmesContr.value)
  RPMnumSmes = 0

}

// Извлечение
function pos4() {
  NumberPos = 4
  bearStyleStyleHeight.value = 25 + "px"
  bearStyleStyleWidth.value = 40 + "px"
  bearStylePosLeft.value = 459 + "px"
  bearStylePosTop.value = -10 + "px"
  clearInterval(rotateButtCocont.value)
  HotCold()

  bearStyleSrc.value = "https://media.istockphoto.com/id/1302390177/ru/%D0%B2%D0%B5%D0%BA%D1%82%D0%BE%D1%80%D0%BD%D0%B0%D1%8F/%D0%BE%D1%80%D0%B0%D0%BD%D0%B6%D0%B5%D0%B2%D1%8B%D0%B9-%D0%BA%D0%BB%D0%B5%D0%B9%D0%BA%D0%B8%D0%B9-%D0%BC%D0%B5%D0%B4%D0%B2%D0%B5%D0%B4%D1%8C-%D0%B6%D0%B5%D0%BB%D0%B5-%D1%81%D0%BB%D0%B0%D0%B4%D0%BA%D0%B8%D0%B5-%D0%BA%D0%BE%D0%BD%D1%84%D0%B5%D1%82%D1%8B-%D1%81-%D1%83%D0%B4%D0%B8%D0%B2%D0%B8%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%BC-%D0%B2%D0%BA%D1%83%D1%81%D0%BE%D0%BC-%D0%BF%D0%BB%D0%BE%D1%81%D0%BA%D0%B8%D0%B9-%D1%81%D1%82%D0%B8%D0%BB%D1%8C-%D0%B4%D0%B8%D0%B7%D0%B0%D0%B9%D0%BD.jpg?s=612x612&w=0&k=20&c=Kd9x56zTT8NoEQPS4txp4XFVdIca29zq8MhdvuKUw38="
}

// Сушка
function pos5() {
  NumberPos = 5
  bearStyleStyleHeight.value = 25 + "px"
  bearStyleStyleWidth.value = 40 + "px"
  bearStylePosLeft.value = 603 + "px"
  bearStylePosTop.value = 0 + "px"
  bearRotate.value = "90"
  hot()
  HotTimeAndTempR()

}

// Упаковка
function pos6() {
  NumberPos = 6
  bearStyleStyleHeight.value = 45 + "px"
  bearStyleStyleWidth.value = 45 + "px"
  bearStylePosLeft.value = 747 + "px"
  bearStylePosTop.value = -39 + "px"
  bearRotate.value = "0"
  bearStyleSrc.value = "https://avatars.mds.yandex.net/get-mpic/4304254/2a0000018a5e9a3a25e166314e5f55102e92/optimize"
  clearInterval(HotContr.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  HotTime = 0

}

// Функция отвечающая за истечение таймера и повышения температуры блока "Сушка"
function HotTimeAndTempR() {
  HotTime = HotTime +6
  setTimeout(() => {
    HotTime = HotTime -1
  },900)
  setTimeout(() => {
    HotTime = HotTime -1
  },1800)
  setTimeout(() => {
    HotTime = HotTime -1
  },2700)
  setTimeout(() => {
    HotTime = HotTime -1
  },3600)
  setTimeout(() => {
    HotTime = HotTime -1
  },4500)
  setTimeout(() => {
    HotTime = HotTime -1
  },5400)
  setTimeout(() => {
    HotTempReverse()
  },6000)

  setTimeout(() => {
    HotTemp = HotTemp +1
  },100)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },200)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },300)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },400)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },500)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },600)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },700)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },800)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },900)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },1000)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },1100)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },1200)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },1300)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },1400)
  setTimeout(() => {
    HotTemp = HotTemp +1
  },1500)
}
// Функция отвечающая за понижение температуры блока "Сушка"
function HotTempReverse() {
  setTimeout(() => {
    HotTemp = HotTemp -1
  },100)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },200)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },300)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },400)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },500)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },600)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },700)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },800)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },900)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },1000)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },1100)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },1200)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },1300)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },1400)
  setTimeout(() => {
    HotTemp = HotTemp -1
  },1500)
}
bearStyleSrc.value = 'https://media.teradom.ru/images/39/198.jpg'

// Функция отвечающая за перемещение "Медведя" по канвееру
function BearTravel() {
  console.log(NumberPos)
  TimeStopInt.value = setInterval(() => {
    if (NumberPos === 1 ) {

      setTimeout(() => {
        pos2()
      }, 3000)
    }
    if (NumberPos === 2 ) {

      setTimeout(() => {
        pos3()
      }, 3000)
    }
    if (NumberPos === 3 ) {

    setTimeout(() => {
      pos4()
    },3000)
      }
    if (NumberPos === 4 ) {

      setTimeout(() => {
        pos5()
      }, 3000)
    }
    if (NumberPos === 5 ) {

      setTimeout(() => {
        pos6()
      }, 3000)
    }
    if (NumberPos === 6 ) {

      setTimeout(() => {
        pos1()
      }, 3000)
    }
},7000)

}

BearTravel()

let numberTime = ref()
let FormButtOn = ref()
let ColdButtOn = ref()
let UDButtOn = ref()
let HotButtOn = ref()
let BoxButtOn = ref()

// Функция отвечающая за изменение вида курсора при повторном наведении на уже действующую кнопку
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
    if (Smes.value === "red" || Smes.value === "black" ) {
      SmesWarnCur.value = 'not-allowed'
    }
    else {
      SmesWarnCur.value = 'pointer'
    }
    if (Form.value === "red" || Form.value === "black") {
      FormWarnCur.value = 'not-allowed'
    }
    else {
      FormWarnCur.value = 'pointer'
    }
    if (Cold.value === "red" || Cold.value === "black") {
      ColdWarnCur.value = 'not-allowed'
    }
    else {
      ColdWarnCur.value = 'pointer'
    }
    if (Up.value === "red" || Up.value === "black") {
      UPWarnCur.value = 'not-allowed'
    }
    else {
      UPWarnCur.value = 'pointer'
    }
    if (Hot.value === "red" || Hot.value === "black") {
      HotWarnCur.value = 'not-allowed'
    }
    else {
      HotWarnCur.value = 'pointer'
    }
    if (Box.value === "red" || Box.value === "black") {
      BoxWarnCur.value = 'not-allowed'
    }
    else {
      BoxWarnCur.value = 'pointer'
    }


}, 9)
}
ActionIfButt()

// Функции приводящие в работу блок "Формовка"
function UDForm() {
  UDformOwContr.value = setInterval(() => {
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
  }, 9)
  // console.log(1)
  UDformMidContr.value = setInterval(() => {
    // console.log(1.5)
      if (Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      let rect = udm.value.getBoundingClientRect()
      let newTop = rect.height + 10
      udm.value.style.height = newTop + 'px'
        numberTime.value = 1
    }
  }, 700)
  // console.log(2)
  UDformBottContr.value = setInterval(() => {
    if (Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      // console.log(2.5)
      let rect = udm.value.getBoundingClientRect()
      let newTop = rect.height - 20
      udm.value.style.height = newTop + 'px'
      numberTime.value = 0
    }

  }, 1400)
  // console.log(3)
}

//  Функции обеспечивающие запланированную остановку того или иного блока по нажатию соответствующей кнопки
function SmesStop() {
  Smes.value = 'orangered'
  clearInterval(interval.value)
  clearInterval(TimeStopInt.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"
  // clearTimeout(TimeStopInt.value)

  RPMnumSmes = 0
  RPMnumSmes = 0


}
function FormStop() {
  Form.value = 'orangered'
  clearInterval(interval2.value)
  clearInterval(TimeStopInt.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"

  RPMnumSmes = 0
  RPMnumSmes = 0

}
function ColdStop() {
  Cold.value = 'orangered'
  clearInterval(interval3.value)
  clearInterval(TimeStopInt.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"

  RPMnumSmes = 0
  RPMnumSmes = 0

}
function UpStop() {
  Up.value = 'orangered'
  clearInterval(interval4.value)
  clearInterval(TimeStopInt.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"

  RPMnumSmes = 0
  RPMnumSmes = 0

}
function HotStop() {
  Hot.value = 'orangered'
  clearInterval(interval5.value)
  clearInterval(TimeStopInt.value)
  Hot1.value = "rgb(250, 50, 50, 45%)"

  RPMnumSmes = 0
  RPMnumSmes = 0

}
function BoxStop() {
  Box.value = 'orangered'
  Hot1.value = "rgb(250, 50, 50, 45%)"
  clearInterval(interval6.value)
  clearInterval(TimeStopInt.value)

  RPMnumSmes = 0
  RPMnumSmes = 0

}

//  Функции обеспечивающие запуск того или иного блока по нажатию соответствующей кнопки
function SmesOn() {
  if (SmesButtOn.value === "not-allowed") {
    alert("Блок «Смеситель» уже включен!")
  }
  else {
    Smes.value = "#21BA45"
    clearInterval(interval.value)
    // BearTravelInterval()
    if ( Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45"
    & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      BearTravel()
    }
  }
}
function FormOn() {
  if (FormButtOn.value === "not-allowed") {
    alert("Блок «Формовка» уже включен!")
  }
  else {
    Form.value = "#21BA45"
    clearInterval(interval2.value)
    if ( Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45"
      & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      BearTravel()
    }
  }
}
function ColdOn() {
  if (ColdButtOn.value === "not-allowed") {
    alert("Блок «Охлаждение» уже включен!")
  }
  else {
    Cold.value = "#21BA45"
    clearInterval(interval3.value)
    if ( Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45"
      & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      BearTravel()
    }
  }
}
function UpOn() {
  if (UDButtOn.value === "not-allowed") {
    alert("Блок «Извлечение» уже включен!")
  }
  else {
    Up.value = "#21BA45"
    clearInterval(interval4.value)
    if ( Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45"
      & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      BearTravel()
    }
  }
}
function HotOn() {
  if (HotButtOn.value === "not-allowed") {
    alert("Блок «Сушка» уже включен!")
  }
  else {
    Hot.value = "#21BA45"
    clearInterval(interval5.value)
    if ( Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45"
      & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      BearTravel()
    }
  }
}
function BoxOn() {
  if (BoxButtOn.value === "not-allowed") {
    alert("Блок «Упаковка» уже включен!")
  }
  else {
    Box.value = "#21BA45"
    clearInterval(interval6.value)
    if ( Smes.value === "#21BA45" & Form.value === "#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45"
      & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      BearTravel()
    }
  }
}

//  Функции устанавливающие аварийный статус того или иного блока по нажатию соответствующей кнопки
function SmesWarn() {
  if (SmesWarnCur.value === "not-allowed") {
    alert("Блок «Смеситель» уже имеет аварийный статус!")
  }
  else {
    interval.value = setInterval(() => {
      if (Smes.value === 'black') {
        Smes.value = 'red'
      } else {
        Smes.value = 'black'

      }
    }, 500)
    Hot1.value = "rgb(250, 50, 50, 45%)"
    clearInterval(TimeStopInt.value)

    RPMnumSmes = 0
  }
}

function FormWarn() {
  if (FormWarnCur.value === "not-allowed") {
    alert("Блок «Формовка» уже имеет аварийный статус!")
  }
  else {
    interval2.value = setInterval(() => {
      if (Form.value === 'black') {
        Form.value = 'red'
      } else {
        Form.value = 'black'

      }
    }, 500)
    Hot1.value = "rgb(250, 50, 50, 45%)"
    clearInterval(TimeStopInt.value)

    RPMnumSmes = 0
  }
}

function ColdWarn() {
  if (ColdWarnCur.value === "not-allowed") {
    alert("Блок «Охлаждение» уже имеет аварийный статус!")
  }
  else {
    interval3.value = setInterval(() => {
      if (Cold.value === 'black') {
        Cold.value = 'red'
      } else {
        Cold.value = 'black'

      }
    }, 500)
    Hot1.value = "rgb(250, 50, 50, 45%)"
    clearInterval(TimeStopInt.value)

    RPMnumSmes = 0
  }
}
function UpWarn() {
  if (UPWarnCur.value === "not-allowed") {
    alert("Блок «Извлечение» уже имеет аварийный статус!")
  }
  else {
    interval4.value = setInterval(() => {
      if (Up.value === 'black') {
        Up.value = 'red'
      } else {
        Up.value = 'black'

      }
    }, 500)
    Hot1.value = "rgb(250, 50, 50, 45%)"
    clearInterval(TimeStopInt.value)

    RPMnumSmes = 0
  }
}
function HotWarn() {
  if (HotWarnCur.value === "not-allowed") {
    alert("Блок «Сушка» уже имеет аварийный статус!")
  }
  else {
    interval5.value = setInterval(() => {
      if (Hot.value === 'black') {
        Hot.value = 'red'
      } else {
        Hot.value = 'black'

      }
    }, 500)
    Hot1.value = "rgb(250, 50, 50, 45%)"
    clearInterval(TimeStopInt.value)

    RPMnumSmes = 0
  }
}
function BoxWarn() {
  if (BoxWarnCur.value === "not-allowed") {
    alert("Блок «Упаковка» уже имеет аварийный статус!")
  }
  else {
    interval6.value = setInterval(() => {
      if (Box.value === 'black') {
        Box.value = 'red'
      } else {
        Box.value = 'black'

      }
    }, 500)
    Hot1.value = "rgb(250, 50, 50, 45%)"
    clearInterval(TimeStopInt.value)

    RPMnumSmes = 0
  }
}

// Функция вращения лопастей смесителя
function rotateBottomS() {
  rotateButtScont.value = setInterval(() => {
    if( Smes.value === "#21BA45" & Form.value ==="#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45")
    bottomSRotate.value += 5
    else {
      bottomSRotate.value =0
    }
  }, 25)

}

// Функция вращения лопастей охлаждающего блока
let rotateButtCocont = ref()
function rotateBottomC() {
  rotateButtCocont.value = setInterval(() => {
    if( Smes.value === "#21BA45" & Form.value ==="#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45")
    bottomCRotate.value += 15
  }, 25)
}

// Функция визуализации работы блока нагрева
let HotContr = ref()
function hot() {
  HotContr.value = intervalhot.value = setInterval(() => {
    if( Smes.value === "#21BA45" & Form.value ==="#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45"){
    if (Hot1.value === "rgb(250, 50, 50, 45%)") {
      Hot1.value = "rgb(250, 50, 50, 69%)"
    }
    else {
      Hot1.value = "rgb(250, 50, 50, 45%)"

    }  }
  }, 700)

}

// Функция отвечающая за "колебания" значения RPM смесителя
function SmesRPM() {
  RPMsmesContr.value = setInterval(() => {
    if( Smes.value === "#21BA45" & Form.value ==="#21BA45" & Cold.value === "#21BA45" & Up.value === "#21BA45" & Hot.value === "#21BA45" & Box.value === "#21BA45") {
      RPMnumSmes = 72
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
    else {
      RPMnumSmes = 0
    }
},2500)
}

// Функция отвечающая за понижение температуры блока "Охлаждение"
ColdTempNum = 21
function ColdHot() {
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 1
    }, 100)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 2
    }, 300)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 3
    }, 500)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 4
    }, 700)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 5
    }, 900)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 6
    }, 1100)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 5
      ColorTextTemp.value = "cornflowerblue"
    }, 1300)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 4
    }, 1500)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 3
    }, 1700)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 3
    }, 1900)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 3
    }, 2100)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 3
    }, 2300)
    setTimeout(() => {
      ColdTempNum = ColdTempNum - 3
    }, 2500)
}

// Функция отвечающая за повышение температуры блока "Охлаждение"
function HotCold() {
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 1
  }, 100)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 2
  }, 400)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 3
  }, 700)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 4
  }, 1000)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 5
  }, 1300)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 6
  }, 1700)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 5
    ColorTextTemp.value = "rgb(250, 50, 50)"
  }, 2000)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 4
  }, 2300)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 3
  }, 2600)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 3
  }, 2900)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 3
  }, 3200)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 3
  }, 3500)
  setTimeout(() => {
    ColdTempNum = ColdTempNum + 3
  }, 3800)
}

</script>

<style scoped>


#container {
  height: 1000px;
  background-color: rgb(150, 150, 150, 18%);

}

.Txt {
  text-decoration: Canvas;
  cursor: context-menu;
}
.Con {
  background: linear-gradient(
    175deg,
    dimgray 42%,
    grey,
    dimgray
  );
  width: 1260px;
  height: 90px;
  position: absolute;
  left: 36px;
  top: 330px;
  display: flex;
  font-size: 18px;
  text-align: center;
  color: wheat;
  box-shadow: 5px 5px 5px black;
}

#ControlPanelBackGround{
  width: 1350px;
  height: 360px;
  background-color: #121212;
  position: absolute;
  z-index: -1;
  top: 350px;

}

#OwPanel {
  width: 1300px;
  height: 170px;
  background: linear-gradient(
    180deg,
    dimgray 42%,
    #FFFFFF,
    grey
  );
  position: absolute;
  bottom: 200px;
  right: 1px;
  box-shadow: 5px 5px 5px black;
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
  width: 110px;
  left: 64px;
  top: 310px;
  z-index: -2;

}
#bear1 {
  height: 20px;
  width: 115px;
}


.ControlButtonPlate {
  position: absolute;
  background-color: black;
  width: 520px;
  height: 225px;
  left: 375px;
  top: 425px;
  text-align: center;
  box-shadow: 5px 5px 5px #121212;

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
  width: 90px;
  background-color: rgb(50, 50, 50, 100%);
  position: relative;
  font-size: 15px;
  left: 15px;
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
  background: linear-gradient(
  135deg,
  #1D1D1D,
  #121212,
  #FFFFFF
  );
  height: 120px;
  width: 70px;
  box-shadow: 2px 2px 2px black;
}
#middleS {
  background: linear-gradient(
    -45deg,
    #121212,
    silver,
    #121212
  );
  width: 30px;
  height: 90px;
 left: 18%;
  position: relative;
  box-shadow: 2px 2px 2px black;
}
#bottomS{
  position: relative;
  width: 60px;
  height: 60px;
  left: 7px;
  border: #1D1D1D 1px solid;
  z-index: -1;
  box-shadow: 2px 2px 2px black;
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
  background: linear-gradient(
    -45deg,
    #121212,
    silver,
    grey
  );
  height: 120px;
  width: 70px;
  box-shadow: 2px 2px 2px black;

}
#middleF1 {
  background: linear-gradient(
    -45deg,
    #121212,
    grey
  );
  width: 30px;
  height: 90px;
  left: 18%;
  position: relative;
  box-shadow: 2px 2px 2px black;
}
#bottomF{
  position: relative;
  width: 60px;
  height: 15px;
  background: linear-gradient(
    0deg,
    orangered,
    #121212,
  black
  );
  left: 7px;
  box-shadow: 2px 2px 2px black;
}

.ColdTech {
  position: relative;
  bottom: 280px;
  left: 23px;
}
#ColdTemp {
width: 70px;
  height: 30px;
  background-color: black;
  z-index: +30;
  position: relative;
  top: 30px;
}
#TopC{
  background: linear-gradient(
    -45deg,
    slategrey 1px,
    #121212,
    grey
  );
  height: 120px;
  width: 70px;
  box-shadow: 2px 2px 2px black;
}
#middleC{
  background: linear-gradient(
    -45deg,
    #121212,
    slategrey,
   black
  );
  width: 30px;
  height: 80px;
  left: 18%;
  position: relative;
  box-shadow: 2px 2px 2px black;
}
#bottomC{
  position: relative;
  width: 45px;
  height: 45px;
  left: 14px;
  border: #1D1D1D 1px solid;
  z-index: -1;
  box-shadow: 2px 2px 2px black;
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
  background: linear-gradient(
    135deg,
    #FFFFFF,
    #1D1D1D,
    #121212,
    #FFFFFF
  );
  height: 120px;
  width: 70px;
  box-shadow: 2px 2px 2px black;
}
#middleU{
  background: linear-gradient(
    135deg,
    #FFFFFF,
    #1D1D1D,
    #121212
  );
  width: 30px;
  height: 90px;
  left: 18%;
  position: relative;
  box-shadow: 2px 2px 2px black;
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
  box-shadow: 2px 2px 2px black;
}

.HotTech{
  position: relative;
  bottom: 290px;
  left: 23px;
}
#TopH{
  background: linear-gradient(
    135deg,
    saddlebrown,
    #1D1D1D,
    #121212,
    saddlebrown
  );
  height: 120px;
  width: 70px;
  box-shadow: 2px 2px 2px black;
}
#HotTempBlock {
  width: 70px;
  height: 30px;
background-color: #121212;

  position: relative;
  top: 60px;

}
#HotTime{
  position: relative;
  top: 39px;
  width: 70px;
  height: 30px;
  background-color: black;
  font-style: italic;
  color: #C10015;
}
#middleH{
  background: linear-gradient(
    180deg,
  saddlebrown,
    #1D1D1D 75%,
    #121212,
    #002137,

    #7442c8
  );
  width: 30px;
  height: 90px;
  left: 18%;
  position: relative;
  box-shadow: 2px 2px 2px black;
}
#bottomH{
  border: orangered solid 1px;
  width: 90px;
  height: 15px;
  position: relative;
  right: 7px;
  background-color: rgb(250, 50, 50, 45%);
  box-shadow: 2px 2px 2px black;
}

.BoxTech {
  position: relative;
  bottom: 210px;
  left: 23px;
}
#TopB{
  background: linear-gradient(
    135deg,
    #1D1D1D 43%,
    darkgray,
    #121212
  );
  height: 50px;
  width: 90px;
  box-shadow: 2px 2px 2px black;
}
#middleB{
  background: linear-gradient(
    135deg,
    darkgray,
    #1D1D1D 43%,
    #121212
  );
  width: 30px;
  height: 45px;
  left: 25%;
  position: relative;
  box-shadow: 2px 2px 2px black;
}
#bottomB{
  border: rgb(150,100, 20, 85%) 1px solid;
  width: 90px;
  height: 60px;
  position: relative;
  background-color: rgb(350,100, 20, 45%);
  box-shadow: 2px 2px 2px black;
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
