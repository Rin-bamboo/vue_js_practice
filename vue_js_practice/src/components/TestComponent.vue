<script setup>
  import { ref } from "vue";

  defineProps({
    text: String,
  });
  const dataTest = "これはデータ";
  const imageUrl = "https://placehold.jp/150x150.png";
  const name = ref("");
  const fruitsList = [{ id: 0, name: "りんご" }, { id: 1, name: "いちご" }, { id: 2, name: "ばなな" }];

  const number = ref(0);
  function myMethod() {
    alert("ボタンが押されました");
  }

  const memberList = ref([
    { id: 0, name: "山田太郎" },
    { id: 1, name: "鈴木花子" },
    { id: 2, name: "佐藤次郎" },
  ]);
  function deleteItem(index) {
    memberList.value.splice(index, 1);
  }

</script>

<template>
  <p>{{ text }}</p> <!--テキストバインディング-->
  <!--<p v-text="dataTest"></p>--> <!--v-textディレクティブ-->

  <img v-bind:src="imageUrl" />
  <!--<img :src="imageUrl" />-->
  <br />
  <button v-on:click="myMethod">クリックしてね</button>
  <br />
  <!--<button @click="myMethod">クリックしてね</button>-->
  <p>名前入力</p>
  <label>名前:</label>
  <input type="text" id="name" v-model="name" />
  <p>入力値: {{ name }}</p>
  <ul>
    <li v-for="fruit in fruitsList" :key="fruit.id">{{ fruit.name }}</li>
  </ul>

  <p>会員リスト</p>
  <ul>
    <li v-for="(member, index) in memberList" :key="member.id">
      {{ member.name }}<br />
      備考
      <input type="text" />
      <br />
      <button @click="deleteItem(index)">削除</button>

    </li>
  </ul>

  <!--  -->
  <input type="number" id="number" v-model="number" />
  <p v-if="number < 10"> 10未満です</p>
  <p v-else>10以上です</p>

  <p v-show="number > 10">10より大きいです</p>

</template>
