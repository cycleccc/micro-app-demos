<template>
  <div id="app">
    <a-config-provider prefixCls="av2" :getPopupContainer="getPopupContainer">
      <router-view v-slot="{ Component }">
        <keep-alive>
          <component :is="Component" />
        </keep-alive>
      </router-view>
    </a-config-provider>
    <my-editor></my-editor>
  </div>
</template>

<script lang="ts">
import { ConfigProvider } from 'ant-design-vue'
import MyEditor from './components/MyEditor.vue'
import type Vue from 'vue'

export default {
  methods: {
    getPopupContainer(triggerNode: { parentNode: HTMLElement }): Element {
      if (triggerNode) {
        return triggerNode.parentNode
      }
      return (this as unknown as Vue).$root.$el
    }
  },
  components: {
    [ConfigProvider.name]: ConfigProvider,
    MyEditor
  }
}
</script>
<style></style>
