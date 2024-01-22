<script lang="ts">
export default {
  setup() {
    return {
      message: '插入文本',
      html: '<span style="color: red">插入内容</span>'
    }
  }
}
</script>

<template>
  <div class="tem-title">文本插值</div>
  <div>{{ message }}</div>
  <div class="tem-title">原始HTML</div>
  <div>插入HTML内容：{{ html }}</div>
  <div v-html="html"></div>
</template>
