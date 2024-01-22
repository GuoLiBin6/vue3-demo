<script setup lang="ts">
import { defineAsyncComponent, ref } from 'vue'
import TemplateSyntax from '@/components/vueTest/TemplateSyntax.vue'
console.log(TemplateSyntax)

const items = [
  {
    name: '模板语法',
    key: 'TemplateSyntax',
  },
  {
    name: '响应式',
    key: 'ReactivityFundamentals'
  }
]

let currentComponent = ref(items[0].key)

function changeComponent(item: any) {
  currentComponent.value = item.key
}
</script>

<template>
  <div class="container">
    <div class="sidebar">
      <ul>
        <li v-for="item in items" :key="item.name" class="sidebar-item" @click="() => changeComponent(item)">{{ item.name }}</li>
      </ul>
    </div>
    <div class="content">
      <div class="tem-header">{{ currentComponent }}</div>
      <component :is="defineAsyncComponent(() => import(`@/components/vueTest/${currentComponent}.vue`))" />
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
}
.sidebar {
  flex: 0 0 200px;
}

.sidebar-item {
  padding: 5px;
  cursor: pointer;
  list-style-type: none;
}

.sidebar-item:hover{
  font-size: 1.2em;
  text-decoration: solid;
  text-decoration-line: underline;
}

.tem-header {
  font-size: 1.5em;
  margin-bottom: 20px;
}

</style>

<style>
.tem-title {
  font-size: 24px;
  font-weight: bold;
  padding: 5px 0;
  margin-top: 10px;
}
</style>
