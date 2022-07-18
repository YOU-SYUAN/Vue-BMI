<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/>    w => 寬度 -->
  <div style="text-align: center" class="mt-4">
    <div>
      <p class="text-green-400 text-3xl mb-3">BMI 計算器</p>
    </div>
    <div mb-2>
      <label class="text-[#828282] text-xl">身高</label><br />
      <input
        type="float"
        class="bg-gray-50 border border-emerald-300 text-gray-900 text-sm rounded-md p-2.5 w-60 placeholder-emerald-400"
        placeholder="公分"
        v-model="height"
        required
      />
    </div>
    <br />
    <div mb-3>
      <label class="text-[#828282] text-xl">體重</label><br />
      <input
        type="float"
        class="bg-gray-50 border border-emerald-300 text-gray-900 text-sm rounded-md p-2.5 w-60 placeholder-emerald-400"
        placeholder="公斤"
        v-model="weight"
        required
      />
    </div>
    <br />
    <div mb-3 :class="data[bmiresult].textColor">
      <label class="text-[#C0BABA] text-2xl">BMI</label>
      {{ bmi.toFixed(2) }}
    </div>
    <div class="mb-4">
      <button
        v-on:click="result"
        class="bg-[#F3E988] p-2.5 w-64 shadow-lg transition ease-in-out duration-200 translate-10"
        :class="data[bmiresult].bgColor"
      >
        您的體重是 「{{ data[bmiresult].result }}」
      </button>
    </div>
    <table align="center" class="text-xl">
      <td align="left" class="mr-10">
        <label class="text-[#F6D83B]">體重過輕 </label><br />
        <label class="text-[#00BFA5]">正常範圍 </label><br />
        <label class="text-[#F6D83B]">體重過重 </label><br />
        <label class="text-[#EA9921]">輕度肥胖</label><br />
        <label class="text-[#FC8E51]">中度肥胖 </label><br />
        <label class="text-[#F15555]">重度肥胖</label><br />
      </td>
      <td>&nbsp;&nbsp;</td>
      <td align="left" class="ml-10">
        <label class="text-[#F6D83B]">BMI &lt; 18.5 </label><br />
        <label class="text-[#00BFA5]">BMI &lt;= 18.5 &lt; 24</label><br />
        <label class="text-[#F6D83B]">BMI &lt;= 24 &lt; 27</label><br />
        <label class="text-[#EA9921]">BMI &lt;= 27 &lt; 30</label><br />
        <label class="text-[#FC8E51]">BMI &lt;= 30 &lt; 35</label><br />
        <label class="text-[#F15555]">BMI &gt;= 35</label><br />
      </td>
    </table>
    <!-- <div class="grid grid-flow-col">
    <div class="text-xl mt-10 ml-60">
      <label class="text-[#F6D83B]">體重過輕 </label><br />
      <label class="text-[#00BFA5]">正常範圍 </label><br />
      <label class="text-[#F6D83B]">過重</label><br />
      <label class="text-[#EA9921]">輕度肥胖 </label><br />
      <label class="text-[#FC8E51]">中度肥胖</label><br />
      <label class="text-[#F15555]">重度肥胖</label><br />
    </div>
    <div class="text-xl mt-10 ml-16 mr-52">
      <label class="text-[#F6D83B]">BMI &lt; 18.5 </label><br />
      <label class="text-[#00BFA5]">BMI &lt;= 18.5 &lt; 24</label><br />
      <label class="text-[#F6D83B]">BMI &lt;= 24 &lt; 27</label><br />
      <label class="text-[#EA9921]">BMI &lt;= 27 &lt; 30 </label><br />
      <label class="text-[#FC8E51]">BMI &lt;= 30 &lt; 35</label><br />
      <label class="text-[#F15555]">BMI &gt;= 35</label><br />
    </div>
  </div> -->
  </div>
</template>
<script setup>
import { ref, computed, reactive } from "vue";
const data = [
  { result: "過輕", bgColor: "bg-amber-300", textColor: "text-amber-200" },
  {
    result: "正常範圍",
    bgColor: "bg-emerald-500",
    textColor: "text-emerald-200",
  },
  { result: "過重", bgColor: "bg-yellow-400", textColor: "text-yellow-200" },
  {
    result: "輕度肥胖",
    bgColor: "bg-orange-600",
    textColor: "text-orange-400",
  },
  {
    result: "中度肥胖",
    bgColor: "bg-orange-400",
    textColor: "text-orange-200",
  },
  { result: "重度肥胖", bgColor: "bg-red-500", textColor: "text-red-200" },
];
const height = ref("");
const weight = ref("");
var bmi = ref(0);
bmi = computed(() => {
  if (height.value == 0) return 0;
  return weight.value / Math.pow(height.value / 100, 2);
});
const bmiresult = computed(() => {
  if (bmi.value < 18.5) {
    return 0;
  } else if (bmi.value >= 18.5 && bmi.value < 24) {
    return 1;
  } else if (bmi.value >= 24 && bmi.value < 27) {
    return 2;
  } else if (bmi.value >= 27 && bmi.value < 30) {
    return 3;
  } else if (bmi.value >= 30 && bmi.value < 35) {
    return 4;
  } else {
    return 5;
  }
});
</script>
<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
  background-color: mediumaquamarine;
} */
</style>
