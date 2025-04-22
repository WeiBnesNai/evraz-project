<template>
  <div>
    <canvas ref="canvas" width="1900" height="1000"></canvas>
  </div>
</template>
<script setup>
import { ref, onMounted } from 'vue';
import { Canvas, Rect, Text, Circle } from 'fabric';

const canvas = ref();

onMounted(() => {
  // Инициализация canvas
  const fabricCanvas = new Canvas(canvas.value);
  // Создание прямоугольника
  // const rect = new Rect({
  //   left: 100,
  //   top: 100,
  //   fill: 'blue',
  //   width: 100,
  //   height: 100,
  // });
  const oneCen = new Rect({
    left: 950,
    top: 477,
    fill: 'grey',
    width: 34,
    height: 100,
    id: 'Center_up_center',
    status: 'active'

  });
  const twoCen = new Rect({
    left: 1000,
    top: 477,
    fill: 'grey',
    width: 34,
    height: 100,
    id: 'Center_up_right',
    status: 'active'

  });
  const threeCen = new Rect({
    left: 900,
    top: 477,
    fill: 'grey',
    width: 34,
    height: 100,
    id: 'Center_up_left',
    status: 'active'

  });
  const fourCen = new Rect({
    left: 950,
    top: 597,
    fill: 'grey',
    width: 34,
    height: 100,
    id: 'Center_down_center',
    status: 'active'

  });
  const circle = new Circle({
    left: 950,
    top: 597,
    fill: 'red',
    width: 34,
    height: 100,
    id: 'Center_down_center',
    status: 'active',
    radius: 50,

  });
  // const text = new Text({
  //   left: 200,
  //   top: 200,
  //   fontSize: 15,
  // });
  // Добавление прямоугольника на canvas

  fabricCanvas.add(oneCen);
  fabricCanvas.add(twoCen);
  fabricCanvas.add(threeCen);
  fabricCanvas.add(fourCen);
  fabricCanvas.add(circle);
});

</script>
<style scoped>
canvas {
  border: 3px solid #ccc;
  background-color: rgb(20,20,20, 40%);

}
</style>
