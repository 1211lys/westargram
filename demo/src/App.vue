<template>
  <div id="app">
    <div class="container">
      <h1>VSkeletonLoader Demo</h1>
      <div>
        <div id="textInput">
          <input
            type="text"
            v-model="textInput"
            v-on:keyup.enter="submitValue"
          />
          <p>Value: {{ textInput }}</p>
        </div>
      </div>
      <div class="samples">
        <VSkeletonLoader :content="{ submitData }" />
        <h3>Case #1</h3>
        <VSkeletonLoader :content="type1" />
        <h3>Case #2</h3>
        <VSkeletonLoader :content="type2" />
        <h3>Case #3</h3>
        <VSkeletonLoader :content="type3" />
        <h3>Case #4</h3>
        <VSkeletonLoader :content="type4" />
        <h3>Case #5</h3>
        <VSkeletonLoader :content="type5" />
        <h3>Case #6</h3>
        <VSkeletonLoader :content="type6" />
        <h3>Case #7</h3>
        <VSkeletonLoader :content="type7" />
        <h3>Case #8</h3>
        <VSkeletonLoader :content="type8" />
        <h3>Case #9</h3>
        <VSkeletonLoader :content="type9" />
        <h3>Case #10</h3>
        <VSkeletonLoader :content="type10" />
        <h3>Case #11</h3>
        <VSkeletonLoader :content="type11" />
        <h3>Case #12</h3>
        <VSkeletonLoader :content="type12" />
        <h3>Case #13</h3>
        <VSkeletonLoader :content="type13" />
        <h3>Case #14</h3>
        <VSkeletonLoader :content="type14" />
        <h3>Case #15</h3>
        <VSkeletonLoader :content="type15" />
        <h3>Case #16</h3>
        <VSkeletonLoader :content="type16" />
        <h3>Case #17</h3>
        <VSkeletonLoader :content="type17" />
        <h3>Case #18</h3>
        <VSkeletonLoader :content="type18" />
        <h3>Case #19</h3>
        <VSkeletonLoader :content="type19" />
        <h3>Case #20</h3>
        <VSkeletonLoader :content="type20" />
        <h3>Case #21</h3>
        <VSkeletonLoader :content="type21" />
        <h3>Case #22</h3>
        <VSkeletonLoader :content="type22" />
        <h3>Case #23</h3>
        <VSkeletonLoader :content="type23" />
        <h3>Case #24</h3>
        <VSkeletonLoader :content="type24" />
      </div>
    </div>
  </div>
</template>

<script>
import "@/components/VSkeletonLoader";
import VSkeletonLoader from "./components/VSkeletonLoader.vue";
export default {
  name: "App",
  components: {
    VSkeletonLoader,
  },
  data() {
    return {
      type1: [["box", "text"]],
      type2: [["box", "text:2"]],
      type3: [["box", "text:3", "text:2"]],

      type4: [["circle", "text"]],
      type5: [["circle", "text:2"]],
      type6: [["circle", "text:3"]],

      type7: [["box", "title + text"]],
      type8: [["box", "title + text:2"]],
      type9: [["box", "title + text:3"]],

      type10: [["circle", "title + text"]],
      type11: [["circle", "title + text:2"]],
      type12: [["circle", "title + text:3"]],

      type13: [["box", "title + text"], ["text"]],
      type14: [["box", "title + text:2"], ["text:2"]],
      type15: [["box", "title + text:3"], ["text:3"]],

      type16: [["circle", "title + text"], ["text"]],
      type17: [["circle", "title + text:2"], ["text:2"]],
      type18: [["circle", "title + text:3"], ["text:3"]],

      type19: [["box", "title + text"], ["text"], ["text"]],
      type20: [["box", "title + text:2"], ["text:2"], ["text:2"]],
      type21: [["box", "title + text:3"], ["text:3"], ["text:3"]],

      type22: [["circle", "title + text"], ["text"], ["text"]],
      type23: [["circle", "title + text:2"], ["text:2"], ["text:2"]],
      type24: [["circle", "title + text:3"], ["text:3"], ["text:3"]],
      textInput: "",
      submitData: [],
    };
  },
  methods: {
    handler(e) {
      console.log(e);
    },
    // convertArrStrToArr(arrStr) {
    //   return Array.of(arrStr.replace(/'/g, '"')).JSON.Par;
    // },

    convertArrStrToArr(inputStr) {
      return inputStr
        .replace(/"/g, "")
        .replace(/'/g, "")
        .replace(/\[/g, "")
        .replace(/], /g, "-")
        .replace(/]/g, "")
        .split("-")
        .map((s) => s.split(",").map((v) => v.trim()))
        .filter((v) => typeof v === "string");
    },
    submitValue() {
      // console.log(this.convertArrStrToArr());
      // 빈문자열 확인
      // 정상적인 배열문장열인지 ("[]", "['ㅈㅇㅈ', 'ㅈㅇㅈㅇ']", "['ㅈㅇㅈ', 'ㅈㅇㅈㅇ', 'ㅇㅈㅇㅈㅇ']")

      // submitData
      // console.log(this.textInput.replace(/'/, /,/g, '"'));
      const result = this.convertArrStrToArr("['circle', 'text:3']");
      console.log(result);
      try {
        this.submitData = result;
        console.log(this.submitData);
        this.textInput = "";
      } catch (e) {
        console.error(e);
      }
    },
  },
};
</script>
<style>
#app {
  width: 800px;
  margin: 0 auto;
}
.container {
  margin: 20px;
}

.input {
  width: 200px;
  height: 200px;
}
</style>
