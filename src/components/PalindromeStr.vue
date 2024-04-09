<script setup lang="ts">
import { ref } from 'vue'

const str = ref('abcbcad')
const targetStrArr = ref<string[]>([])
const findPalindromeStr = () => {
  const s = str.value
  targetStrArr.value = []
  const len = s.length
  const dp = new Array(len).fill(0).map(_ => new Array(len).fill(0))

  const dpStr = new Array(len).fill(0).map(_ => new Array(len).fill(0))
  for (let i = 0; i < len; i += 1) {
    for (let j = 0; j < i + 1; j += 1) { 
      dpStr[i][j] = s.substring(j, i + 1) + Array(len - 1 - (i - j)).fill(' ').join('')
    }
  }

  for (let i = 0; i < len; i += 1) {
    dp[i][i] = 1
  }

  for (let i = len - 2; i >= 0; i -= 1) {
    for (let j = i; j < len; j += 1) {
      dpStr[i][j] = s.substring(i, j + 1) + Array(len - 1 - (j - i)).fill(' ').join('')
      if (s[i] === s[j] && (j - i === 1 || dp[i + 1][j - 1])) {
        dp[i][j] = '1'
        const targetStr = s.substring(i, j + 1)
        // Filter already has
        if (targetStrArr.value.indexOf(targetStr) < 0) {
          targetStrArr.value.unshift(targetStr)
        }
      }
    }
  }
  console.log('Charming dp arr: ', dp)
  console.log('Charming dpStr arr: ', dpStr)
}

</script>

<template>
  <h1>回文字符串</h1>
  <div>
    <h4>
      待操作字符串： <input v-model="str" @keyup="findPalindromeStr" :model="str" placeholder="请输入字符串" />
    </h4>
    <p>{{ targetStrArr }}</p>
    <button @click="findPalindromeStr">点击生成回文字符串</button>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
