<script setup lang="ts">
import { ref } from 'vue'

const str = ref('abcbcad')
const targetStrArr = ref<string[]>([])

const findStr = () => {
  console.log(str.value)
  const s = str.value
  targetStrArr.value = []
  const len = s.length
  const dp = new Array(len).fill(0).map(_ => new Array(len).fill(0))

  for (let i = 0; i < len; i += 1) {
    dp[i][i] = 1
  }

  for (let i = len - 2; i > 0; i -= 1) {
    for (let j = i; j < len; j += 1) {
      if (s[i] === s[j] && (j - i === 1 || dp[i + 1][j - 1])) {
        dp[i][j] = 1
        const targetStr = s.substring(i, j + 1)
        targetStrArr.value.unshift(targetStr)
      }
    }
  }
}


</script>

<template>
  <h1>回文字符串</h1>
  <div>
    <h4>
      待操作字符串： <input v-model="str" :model="str" placeholder="请输入字符串" />
    </h4>
    <p>{{ targetStrArr }}</p>
    <button @click="findStr">点击生成回文字符串</button>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
