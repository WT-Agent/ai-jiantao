<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[生成成功]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 138****5829 成功生成了 职场工作失误深刻检讨书 (态度诚恳度 98分)' },
  { text: '用户 159****4102 成功生成了 学生违纪与课堂纪律反思报告 (思想根源剖析度 96分)' },
  { text: '用户 186****9238 成功生成了 夫妻吵架向伴侣诚恳致歉信 (消除顾虑度 97分)' },
  { text: '用户 133****7712 成功生成了 驾驶违章与公共秩序维护检讨书 (语体规范度 99分)' },
  { text: '用户 177****3650 成功生成了 项目进度延误复盘致歉检讨 (整改措施落地性 95分)' },
]);
</script>

<style scoped>
.ticker-card {
  padding: 0.5rem 1rem;
  margin-bottom: 1.25rem;
  overflow: hidden;
  background: rgba(0, 0, 0, 0.2);
}

.ticker-wrapper {
  display: flex;
  gap: 2rem;
  white-space: nowrap;
  animation: ticker 25s linear infinite;
}

.ticker-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.8rem;
  color: var(--text-secondary);
}

@keyframes ticker {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(-100%);
  }
}
</style>
