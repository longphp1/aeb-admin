<template>
  <div class="icons-container">
    <el-tabs type="border-card">
      <el-tab-pane label="Icons">
        <div class="grid">
          <div v-for="item of svg_icons" :key="item">
            <copy-button :text="generateIconCode(item)">
              <el-tooltip effect="dark" :content="generateIconCode(item)" placement="top">
                <div class="icon-item">
                  <div :class="`i-svg:${item}`" />
                  <span>{{ item }}</span>
                </div>
              </el-tooltip>
            </copy-button>
          </div>
        </div>
      </el-tab-pane>
      <el-tab-pane label="Element-UI Icons">
        <div class="grid">
          <div v-for="(icon, name) of icons" :key="name">
            <copy-button :text="generateElementIconCode(name)">
              <el-tooltip effect="dark" :content="generateElementIconCode(name)" placement="top">
                <div class="icon-item">
                  <el-icon :size="20">
                    <component :is="icon" />
                  </el-icon>
                  <span>{{ name }}</span>
                </div>
              </el-tooltip>
            </copy-button>
          </div>
        </div>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script setup>
import * as ElementPlusIconsVue from "@element-plus/icons-vue";

defineOptions({
  name: "Icons",
  inheritAttrs: false,
});
const svg_icons = [
  "api",
  "cascader",
  "client",
  "close",
  "close_all",
  "close_left",
  "close_other",
  "close_right",
  "dict",
  "document",
  "download",
  "drag",
  "edit",
  "exit-fullscreen",
  "eye-open",
  "eye",
  "fullscreen",
  "github",
  "homepage",
  "language",
  "link",
  "menu",
  "message",
  "money",
  "monitor",
  "order",
  "password",
  "peoples",
  "perm",
  "publish",
  "role",
  "security",
  "size",
  "skill",
  "system",
  "tree",
  "user",
  "uv",
  "verify-code",
];
const icons = ref(ElementPlusIconsVue);

function generateIconCode(symbol) {
  return `<div class="i-svg:${symbol}" />`;
}

function generateElementIconCode(symbol) {
  return `<el-icon><${symbol} /></el-icon>`;
}
</script>

<style lang="scss" scoped>
.icons-container {
  margin: 10px 20px 0;
  overflow: hidden;

  .grid {
    position: relative;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
  }

  .icon-item {
    float: left;
    width: 100px;
    height: 85px;
    margin: 20px;
    font-size: 30px;
    color: var(--el-text-color-regular);
    text-align: center;
    cursor: pointer;
  }

  span {
    display: block;
    margin-top: 10px;
    font-size: 16px;
  }

  .disabled {
    pointer-events: none;
  }
}
</style>
