<template>
  <div class="home">
    <div id="square"></div>
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<style>
body {
  margin: 0;
  position: absolute;
  top: 10px;
  width: 100%;
  text-align: center;
  z-index: 100;
  display: block;
}
</style>

<script src="js/three.js"></script>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import * as THREE from "three";

export default {
  name: "Home",
  components: {
    HelloWorld
  }
};
// Our Javascript will go here.
// ROTATING CUBE
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  1000
);

const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);
const geometry = new THREE.BoxGeometry();
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

camera.position.z = 5;
function animate() {
  requestAnimationFrame(animate);
  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;
  renderer.render(scene, camera);
}
animate();
// DRAWING LINES
// const renderer = new THREE.WebGLRenderer();
// renderer.setSize(window.innerWidth, window.innerHeight);
// document.body.appendChild(renderer.domElement);

// const camera = new THREE.PerspectiveCamera(
//   45,
//   window.innerWidth / window.innerHeight,
//   1,
//   500
// );
// camera.position.set(100, 0, 100);
// camera.lookAt(5, 2, 5);

// const scene = new THREE.Scene();
// const material = new THREE.LineBasicMaterial({ color: 0x0000ff });
// const points = [];
// points.push(new THREE.Vector3(-10, 0, 0));
// points.push(new THREE.Vector3(0, 10, 0));
// points.push(new THREE.Vector3(10, 0, 0));

// const geometry = new THREE.BufferGeometry().setFromPoints(points);
// const line = new THREE.Line(geometry, material);
// scene.add(line);
// renderer.render(scene, camera);
</script>
