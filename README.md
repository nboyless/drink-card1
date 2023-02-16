# thursday-repository
<template>
  import meme-maker from source
2
  <img alt="Vue logo" src="./assets/logo.png" />
3
  <HelloWorld msg="Hello Vue 3 + Vite" />
4
  <div class="controls">
5
  <button id="cardnew" class="button">toggle clone card</button>
6
  <button id="cardtitle" class="button">change clone title</button>
7
  <button id="cardbg" class="button">toggle clone bg color</button>
8
</div>
<slot> meme-maker 
</slot>
9
<div id="cards" class="cards">
10
  <div id="card" class="card">
11
    <img src="https://media.istockphoto.com/id/1147544807/vector/thumbnail-image-vector-graphic.jpg?s=612x612&w=0&k=20&c=rnCKVbdxqkjlcs3xH87-9gocETqpspHFXu5dIGB4wuM=" id="image">
12
    <h2 id="title">Placeholder Card</h2>
13
    <p id="description">placeholder card description</p>
14
    <button id="details" class="button" onclick="toggleDescription()">details</button>
15
  </div>
16
</div>
17
​
18
</template>
19
​
20
<script setup>
21
import HelloWorld from './components/HelloWorld.vue'
22
const btn_cardnew = document.getElementById('cardnew');
23
const btn_cardtitle = document.getElementById('cardtitle');
24
const btn_cardbg = document.getElementById('cardbg');
25
const btn_details = document.getElementById('details');
26
btn_cardnew.addEventListener("click", (e) => { 
27
  if (document.getElementById('dupecard') == null) {
28
    const clone = document.getElementById('card').cloneNode(true);
29
    clone.setAttribute('id', 'dupecard');
30
    document.getElementById('cards').appendChild(clone);
31
    let btn_clonedetails = clone.children[3];
32
    btn_clonedetails.addEventListener("click", (e) => { 
33
      let desc = btn_clonedetails.previousElementSibling;
34
      (desc.style.display == 'none') ? (desc.style.display = '') : (desc.style.display = 'none');
35
    });
36
  }
37
  else {
38
    document.getElementById('cards').removeChild(document.getElementById('dupecard'));
39
  }
40
});
41
btn_cardtitle.addEventListener("click", (e) => { 
42
  if (document.getElementById('dupecard') != null) {
43
    const clone = document.getElementById('dupecard');
44
    title = prompt("Enter new title for the card");
45
    clone.children[1].innerHTML = title;
