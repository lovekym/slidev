---
theme: ./
title: "胡乔的分享报告"
transition: fade
titleTemplate: "%s"
colorSchema: "light"
---

# 胡乔-分享报告

My Sharing Report

<div class="pt-12">
  <span @click="next" class="px-2 p-1 rounded cursor-pointer hover:bg-white hover:bg-opacity-10">
   按空格键进入下一页 <carbon:arrow-right class="inline"/>
  </span>
</div>

<BarBottom >
  <Item text="Hello World！">
  </Item>
</BarBottom>

---

## `<About Me />`

<br />
<br />

<div class="grid grid-cols-2 gap-x-4">
<div>
在试用期间的自我工作总结

1.危化安全生产一体化平台项目：

作业票模块：负责该模块的新增需求开发

知识库模块：同样负责新增需求开发

其他任务：参与了多个模块的 bug 修复工作

2.危化监管驾驶舱大屏项目：

演示版：主要负责首页引导的 UI 交互开发

正式版：人员定位和风险四色图等模块的需求迭代开发

</div>
<div>

## 🧑‍💻<span style="color:purple">擅长的前端技术</span>

<br />
```markdown
- 🌐 **HTML5** 用于构建和呈现互联网内容的核心语言

- 🎨 **CSS3** 用于描述 HTML 或 XML（包括 SVG 和 XHTML）文档
  的呈现

- 🟡 **JavaScript** 一种高级的、解释型的编程语言，主要用于 Web
  浏览器中，使用户与网页可以进行交互
- 💚 **Vue2.js** 一种用于构建用户界面的渐进式 JavaScript 框架

- 🔵 **Vue 技术栈** Vuex Vue-Router Vue-CLI Vite ElementUI

```

</div>
</div>

<BarBottom >
  <Item text="Hello World！">
  </Item>
</BarBottom>

---

# 在工作中学到了什么？

 在过去的几个月中，根据项目的实际需求学习探索了2D/3D数据可视化领域的相关技术。
-  **2D图表库** -学习了多种图表库并应用到实际项目中，如ECharts、DataV。

-  **3D地理空间数据可视化框架** - 熟悉了Cesium、L7、真趣地图SDK的3D模型加载与交互、矢量和几何图形的绘制技术。

-  **跨平台桌面应用程序框架** - 通过Electron框架提供的API来控制视频流等桌面应用特有的元素,利用Chrome开发者工具进行高效调试,成功构建和打包了跨平台的桌面应用。

-  **响应式布局** - 掌握了流体网格系统和使用相对单位（如百分比、em、rem）的技巧。

-  **AI** - 持续关注AI行业的最新动态，学习了AI模型的基本原理与使用，并探索了其在实际工作中的应用方法。

<BarBottom >
  <Item text="Hello World！">
  </Item>
</BarBottom>

---
layout: erath
imageOrder: 1
---

# Code Example
```js
const segmentProgress = (progress * totalPoints) % 1;
const lat = currentPoint[0] + (nextPoint[0]-currentPoint[0]);
const lng = currentPoint[1] + (nextPoint[1]-currentPoint[1]);
marker.setLatLng([lat, lng]);
map.panTo([lat, lng]);
if (progress < 1)
{requestAnimationFrame(animateMarker);}
```

```css
<style>
  .el-row {
    margin-bottom: 20px;
    &:last-child {
      margin-bottom: 0;
    }
  }
</style>
```

<BarBottom >
  <Item text="Hello World！">
  </Item>
</BarBottom>