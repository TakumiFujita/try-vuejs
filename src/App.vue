<script setup>
import { computed, ref } from 'vue'
import ResetButton from './components/ResetButton.vue'

const vueURL = ref('https://vuejs.org')
const userInput = ref('')
const score = ref(0)
const evaluation = computed(() => {
  return score.value > 3 ? 'Good' : 'Bad'
})
const awesome = ref(true)
const fruits = ref(['Apple', 'Banana', 'Grape'])
const user = ref({
  name: 'Tom',
  age: 18,
  gender: 'man'
})
const name = ref('Vue.js')
function greet(event) {
  alert(`Hello ${name.value}!`)
  if (event) {
    alert(event.target.tagName)
  }
}
const count = ref(0)
const toggle = ref()
// function onReset(value) {
//   count.value = value
// }

</script>

<template>
<h2>■v-bind</h2><br>
<a v-bind:href="vueURL">Vue.js</a><br>

<h2>■v-model</h2><br>
<input v-model="userInput" type="text" /><br>
<p>{{ userInput }}</p><br>

<h2>■computed</h2><br>
<p>score : {{ score }}</p><br>
<p>evaluation(score > 3?) : {{ evaluation }}</p><br>
<p>※算出プロパティとメソッドの違い</p><br>
<p>算出プロパティ：</p><br>
<p>・リアクティブな依存関係にもとづきキャッシュされる。算出プロパティは、リアクティブな依存関係が更新されたときにだけ再評価される。逆にどこからも監視されていない場合、実行されなくなる。処理をまとめたいときは基本的にこちらを使う。</p><br>
<p>メソッド：</p><br>
<p>・template内のどれか1つでも更新されて再レンダリングが行われた場合、再レンダリングごとに毎回メソッドが呼び出される。</p><br>

<h2>■v-if</h2><br>
<div v-if="awesome">Vue is awesome!</div>
<div v-else>Oh no 😢</div><br>
<button @click="awesome = !awesome">Toggle</button><br>

<h2>■v-for</h2><br>
<button @click="fruits.shift()">delete</button><br>
<ul>
  <li v-for="(fruit, index) in fruits" :key="fruit"><input type="text">{{ index }}:{{ fruit }}</li>
</ul><br>
<ul>
  <li v-for="(value, key, index) in user" :key="key">{{index}}:{{key}}:{{ value }}</li><br>
</ul><br>

<h2>■v-on</h2><br>
<button @click="greet">Greet</button><br>
<p>Vue.js</p><br>

<h2>■イベント修飾子</h2><br>
<p>リンクが機能しなくなる</p><br>
<a href="https://vuejs.org" @click.prevent>Vue.js</a><br>
<p>カウント：{{ count }}</p><br>
<div @click="count++">
  <button>カウントアップが親要素に伝播するボタン</button><br>
  <button @click.stop>カウントアップのイベントが親要素に伝播させないボタン</button><br>
  <a href="https://vuejs.org" @click.prevent.stop>リンク無効+親要素に伝播させないリンク</a>
</div><br>

<h2>■チェックボックスの値を自由に決める</h2><br>
<input
  type="checkbox"
  v-model="toggle"
  true-value="yes"
  false-value="no" />
  {{ toggle }}<br>

<h2>■子コンポーネントから親コンポーネントに対して通信する</h2><br>
<p>count: {{ count }}</p><br>
<button @click="count++">+1</button><br>
<ResetButton @reset="count = 0" /><br>
<!-- 子コンポーネントの第２引数を受け取って、リセット時にセットする -->
<ResetButton @reset="count = $event" /><br>
<!-- 別の書き方 -->
<!-- <ResetButton @reset="onReset" /><br> -->



</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
