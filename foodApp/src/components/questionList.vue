<template>
  <div :class="[$style.listWrapper]">
    <!--  質問１ -->
    <template v-if="arrayNum.length === 0">
      <h1 :class="[$style.title]">質問1</h1>
      <ul :class="[$style.questionList]">
        <li
          :class="[$style.questionList_item]"
          v-for="(firstQ, index) in firstQs"
          :key="index.category"
          v-on:click="() => showNext(firstQ.item, index)"
        >
          {{ firstQ.item }}
        </li>
      </ul>
      <router-link to="/">
        <button :class="[$style.backBtn]">戻る</button>
      </router-link>
    </template>
    <!-- 質問２ -->
    <template v-else-if="arrayNum.length === 1">
      <h1 :class="[$style.title]">質問2</h1>
      <ul :class="[$style.questionList]">
        <li
          :class="[$style.questionList_item]"
          v-for="(secoundQ, index) in secoundQs[arrayNum[0]]"
          :key="secoundQ.item"
          v-on:click="showOutcome(secoundQ.item, index)"
        >
          {{ secoundQ.item }}
        </li>
      </ul>
      <button
        :class="[$style.backBtn]"
        v-on:click="arrayNum = []"
        style="display: block; margin: 0 auto"
      >
        戻る
      </button>
    </template>
    <!-- 質問３ -->
    <template v-else-if="arrayNum.length === 2">
      <h1 :class="[$style.title]">結果・・・</h1>
      <p
        :class="[$style.outcome]"
        v-text="outcomes[this.arrayNum[0]][this.arrayNum[1]]"
      ></p>
    </template>
  </div>
</template>

<script>
export default {
  name: "questionList",
  data: () => {
    return {
      // 選択された答えとindex番号を入れる配列
      answers: [],
      arrayNum: [],
      // 問題１
      firstQs: [
        { item: "パン" },
        { item: "ご飯" },
        { item: "パスタ" },
        { item: "フルーツ" },
      ],
      // 問題２
      secoundQs: [
        [
          { item: "ジャム" },
          { item: "バター" },
          { item: "チョコ" },
          { item: "チーズ" },
        ],
        [
          { item: "ミソ" },
          { item: "シャケ" },
          { item: "ふりかけ" },
          { item: "納豆" },
        ],
        [
          { item: "ペスカトーレ" },
          { item: "ミートパスタ" },
          { item: "ペペロンチーノ" },
          { item: "カルボナーラ" },
        ],
        [
          { item: "リンゴ" },
          { item: "ブドウ" },
          { item: "レモン" },
          { item: "スイカ" },
        ],
      ],
      // 結果
      outcomes: [
        [
          "あなたはAタイプです",
          "あなたはBタイプです",
          "あなたはCタイプです",
          "あなたはDタイプです",
        ],
        [
          "あなたはAタイプです",
          "あなたはBタイプです",
          "あなたはCタイプです",
          "あなたはDタイプです",
        ],
        [
          "あなたはAタイプです",
          "あなたはBタイプです",
          "あなたはCタイプです",
          "あなたはDタイプです",
        ],
        [
          "あなたはAタイプです",
          "あなたはBタイプです",
          "あなたはCタイプです",
          "あなたはDタイプです",
        ],
      ],
    };
  },
  methods: {
    showNext: function (item, index) {
      this.answers.push(item);
      this.arrayNum.push(index);
    },
    showOutcome: function (item, index) {
      this.answers.push(item);
      this.arrayNum.push(index);
      setTimeout(() => {
        this.$router.push("/");
        this.answer = [];
        this.arrayNum = [];
      }, 2000);
    },
  },
};
</script>

<style module>
.title {
  text-align: center;
  padding: 20px 0;
  margin: 0 auto 20px;
  color: #fff;
}
.listWrapper {
}
.questionList {
  margin-bottom: 40px;
  padding: 0;
}
.questionList_item {
  list-style: none;
  width: 80%;
  margin: 0 auto;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 4px;
  border: 1px solid black;
  background-color: #fff;
  font-size: 20px;
  cursor: pointer;
}
.questionList_item + .questionList_item {
  margin-top: 20px;
}
.backBtn {
  display: flex;
  width: 100px;
  height: 40px;
  font-size: 20px;
  font-weight: bold;
  background-color: #fff;
  margin: 0 auto;
  justify-content: center;
  align-items: center;
  border-radius: 4px;
  text-decoration: none;
  cursor: pointer;
}
.outcome {
  font-size: 20px;
  text-align: center;
  font-weight: bold;
}
</style>
