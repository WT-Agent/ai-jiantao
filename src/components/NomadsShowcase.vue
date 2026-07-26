<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">深刻检讨书与反思模版库 (Nomads Showcase)</h2>
        <p class="showcase-subtitle">精选常见失误场景与反思模版，点击“一键套用”快速生成合规诚恳文案</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个实战模版</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次应用</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-meta">
            对象: {{ item.reviewTarget }} · 规格: {{ item.wordCount }}
          </p>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  reviewType: string;
  reviewTarget: string;
  wordCount: string;
  prompt: string;
  usageCount: string;
}

const emit = defineEmits<{
  (e: 'apply-template', payload: { 
    prompt: string; 
    reviewType?: string; 
    reviewTarget?: string; 
    wordCount?: string; 
  }): void;
}>();

const showcaseItems = ref<ShowcaseItem[]>([
  {
    id: 'jiantao-1',
    tag: '职场履职失误',
    title: '重大工作项目失误与补救检讨',
    reviewType: '职场工作失误与履职尽责检讨',
    reviewTarget: '单位领导主管',
    wordCount: '1000字标准版',
    prompt: '在季度关键项目中因审核不严导致预算数据偏差，请帮我撰写一份向部门总监深刻检讨的文案，重点剖析粗心与流程防范失堵。',
    usageCount: '38.2k'
  },
  {
    id: 'jiantao-2',
    tag: '校园纪律反思',
    title: '课堂玩手机与纪律违规检讨',
    reviewType: '学校学生违纪与课堂纪律反思',
    reviewTarget: '学校老师班主任',
    wordCount: '1000字标准版',
    prompt: '在自习课上偷玩手机被班主任没收，请撰写一份给班主任的深刻检讨书，剖析自控力差与对学习不负责的思想根源。',
    usageCount: '42.5k'
  },
  {
    id: 'jiantao-3',
    tag: '家庭情感沟通',
    title: '吵架失言后向伴侣真诚道歉信',
    reviewType: '夫妻与情侣家庭沟通失误致歉',
    reviewTarget: '伴侣长辈',
    wordCount: '500字精简版',
    prompt: '因为工作压力大在沟通中对伴侣态度冷漠并说了伤人的话，撰写一份真挚诚恳的致歉信，表达愧疚并提出具体的情感沟通改善承诺。',
    usageCount: '29.8k'
  },
  {
    id: 'jiantao-4',
    tag: '考勤与作风',
    title: '多次迟到早退与考勤纪律检讨',
    reviewType: '职场工作失误与履职尽责检讨',
    reviewTarget: '单位领导主管',
    wordCount: '500字精简版',
    prompt: '本月因个人时间规划不当导致连续三次上班迟到，向团队主管提交一份考勤违规检讨书，承诺严守作风纪律。',
    usageCount: '31.4k'
  },
  {
    id: 'jiantao-5',
    tag: '秩序规章维护',
    title: '驾驶违章与公共秩序承诺检讨',
    reviewType: '驾驶违章与公共秩序维护检讨',
    reviewTarget: '公职监管部门',
    wordCount: '1000字标准版',
    prompt: '因交通违章被执法部门处罚，撰写一份向交通监管部门的遵守秩序检讨与文明驾驶承诺书。',
    usageCount: '18.9k'
  },
  {
    id: 'jiantao-6',
    tag: '管理尽职反思',
    title: '团队管理失职与下属失误连带检讨',
    reviewType: '职场工作失误与履职尽责检讨',
    reviewTarget: '单位领导主管',
    wordCount: '2000字深刻版',
    prompt: '作为项目负责人，因对下属业务把关不严导致交期延误，向公司高层提交一份深刻的履职尽责与团队管理反思报告。',
    usageCount: '25.6k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    reviewType: item.reviewType,
    reviewTarget: item.reviewTarget,
    wordCount: item.wordCount
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.3rem;
}

.item-meta {
  font-size: 0.75rem;
  color: #a5b4fc;
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>
