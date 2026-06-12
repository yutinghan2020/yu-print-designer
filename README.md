# Vue3 打印模板可视化设计器

一个基于 **Vue 3 + TypeScript** 的打印模板可视化设计器插件，专为 ERP/业务系统嵌入独立的打印模板设计页而打造。支持拖拽式画布布局、多组件类型、双打印引擎（Web 打印 / LODOP 打印）、条件显示、分页预览等核心能力，让打印模板的设计像搭积木一样简单。

---

## 📸 效果预览

### 整体设计界面

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/整体.png" alt="整体设计界面" /></div>

设计器采用经典的 **三栏布局**：

| 区域             | 功能                                     |
| ---------------- | ---------------------------------------- |
| **左侧栏**       | 组件列表 + 已放置组件图层管理            |
| **中间画布**     | 可视化拖拽画布，带毫米级标尺，所见即所得 |
| **右侧属性面板** | 纸张设置 + 选中组件的属性配置            |

---

### 顶部操作区

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/顶部的操作区.png" alt="顶部操作区" /></div>

- **返回按钮**：可自定义文案与回调
- **模板名称**：显示当前正在设计的模板
- **撤销 / 重做**：完整的历史操作栈，支持多步撤销与重做
- **批量排版工具**：左对齐、水平居中、右对齐、横向分布、顶部对齐、垂直居中、底部对齐、纵向分布
- **保存按钮**：一键保存设计 JSON

---

### 左侧组件列表

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/左侧的组件列表.png" alt="左侧组件列表" /></div>

- **组件库分组展示**：支持业务自定义字段分组（如「基础组件」「订单信息」等）
- **拖拽添加**：从左侧拖拽组件到画布即可添加，支持文本、标题、日期、金额、表格、图片、条码、二维码、横线、竖线、页码等多种组件类型

---

### 左侧已放置组件（图层管理）

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/左侧的已放置的组件.png" alt="左侧已放置组件" /></div>

- **图层列表**：按 Z 轴顺序显示所有已放置的组件
- **拖拽排序**：支持拖拽调整图层顺序
- **显示/隐藏**：一键切换组件的可见性
- **锁定/解锁**：锁定后组件不可选中与移动
- **快速定位**：点击图层项自动选中对应组件

---

### 中间画布区

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/中间的画布区.png" alt="中间画布区" /></div>

- **毫米级标尺**：水平和垂直标尺，精准定位
- **毫米网格背景**：辅助对齐，可开关
- **纸张边距/页眉/页脚**：可视化区域标识
- **拖拽移动**：组件可在画布上自由拖拽移动
- **8 点缩放**：支持四角 + 四边中点拖拽缩放
- **智能对齐线**：移动/缩放时自动显示与相邻组件的对齐参考线
- **键盘操作**：方向键微调位置（1mm/步），Shift+方向键快速移动（10mm/步）
- **多选操作**：Ctrl/Shift+点击多选，支持批量移动与删除

---

### 右侧属性配置区

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/右侧的属性配置区.png" alt="右侧属性配置区" /></div>

**未选中组件时**：显示纸张设置

- 纸张尺寸（A4 / A5 / LETTER / 自定义）
- 纸张背景色
- 页边距（上下左右，精确到 0.5mm）
- 页眉/页脚配置（文本、高度、显示模式）
- 页码配置（位置、格式、字号、颜色、加粗）
- 打印补偿（上下左右）
- 打印模式（Web 打印 / LODOP 打印）

**选中组件时**：显示该组件的属性配置，分为多个配置区：

- 基础信息（组件名称、关联字段、位置尺寸等）
- 样式位置配置
- 数据配置（根据组件类型不同而不同）
- 条件显示配置

---

### 各组件的数据配置

#### 文本组件 — 基础信息 + 数据配置

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/文本组件-基础信息-数据配置.png" alt="文本组件配置" /></div>

- 组件名称、数据字段绑定
- 文本前缀/后缀拼接
- 字体、字号、颜色、对齐方式等样式设置

#### 文本组件 — 样式位置配置 + 操作

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/文本组件-样式位置配置-操作.png" alt="文本组件样式" /></div>

- X/Y 坐标、宽高（精确到 mm）
- 锁定/解锁、显示/隐藏、复制、删除、上移/下移/置顶/置底

#### 表格组件的数据配置

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/表格组件的数据配置项.png" alt="表格组件配置" /></div>

- 表格列定义（列标题、字段名、列宽）
- 支持预设列选择（开启 `enableCustomTableColumns`）
- 表头样式、行样式、边框样式等

#### 日期组件的数据配置

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/日期组件的数据配置项.png" alt="日期组件配置" /></div>

- 日期格式（YYYY-MM-DD / YYYY年MM月DD日 等）
- 数据字段绑定

#### 金额组件的数据配置

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/金额组件的数据配置项.png" alt="金额组件配置" /></div>

- 金额格式化（千分位、小数位数）
- 大写金额转换
- 数据字段绑定

#### 图片组件的数据配置

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/图片组件的数据配置项.png" alt="图片组件配置" /></div>

- 图片 URL（支持数据字段绑定 / 静态 URL / 本地上传）
- 图片适配模式（拉伸、适应、填充等）
- 图片上传配置

#### 组件的条件显示配置

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/组件的条件显示配置项.png" alt="条件显示配置" /></div>

- 开启/关闭条件显示
- 条件字段、比较运算符（等于/不等于/大于/小于/包含/为空等）
- 条件值
- 满足条件时才显示该组件

---

### 设计打印预览

<div align="center"><img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/设计打印预览.png" alt="设计打印预览" /></div>

- 支持在设计器中直接预览打印效果
- 支持 Web 打印预览和 LODOP 打印预览
- 预览窗口可切换不同数据行查看

---

### 订单打印效果

<div align="center">
  <img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/订单打印1.png" alt="订单打印1" />
  <img src="https://raw.githubusercontent.com/yutinghan2020/yu-print-designer/main/data/images/订单打印2.png" alt="订单打印2" />
</div>

---

## ✨ 核心特性

| 特性 | 说明 |
| --- | --- |
| 🖱️ **拖拽式设计** | 从组件库拖拽到画布，自由摆放、缩放、旋转 |
| 🎨 **丰富的组件类型** | 文本、标题、日期、金额、表格、图片、条码、二维码、横线、竖线、页码共 11 种 |
| 📏 **毫米级精度** | 双标尺 + 毫米网格，精确定位到 0.5mm |
| 🔲 **智能对齐** | 拖拽/缩放时自动显示对齐辅助线 |
| 📋 **批量排版** | 多选组件后一键左对齐、居中、右对齐、横向/纵向分布 |
| ↩️ **撤销/重做** | 完整的历史操作栈，支持多步撤销与重做 |
| 🖨️ **双打印引擎** | 同时支持 Web 打印（浏览器原生）和 LODOP 精确打印 |
| 📄 **自动分页** | 根据纸张尺寸和内容自动计算分页，表格跨页自动续打表头 |
| 🔍 **条件显示** | 组件可配置条件表达式，满足条件时才显示 |
| 📸 **图片支持** | 支持静态 URL、数据字段绑定、本地上传三种方式 |
| 🏷️ **条码/二维码** | 内置 JsBarcode 和 QRCode，支持多种条码格式 |
| 🔢 **页眉/页脚/页码** | 可配置页眉页脚文本、页码位置与格式 |
| 🔌 **插件化架构** | 通过适配器模式解耦业务接口，轻松对接任意后端 |
| 🎯 **适配器模式** | 提供 `createPrintDesignerSimpleAdapter` 快速对接业务 API |
| 📱 **响应式设计** | 自适应页面高度，支持各种屏幕尺寸 |

---

## 🚀 快速开始

### 开发环境

| 环境       | 版本要求                 |
| ---------- | ------------------------ |
| Node.js    | >= 16.x                  |
| Vue        | 3.x                      |
| TypeScript | >= 4.x                   |
| 包管理器   | pnpm（推荐）/ npm / yarn |

### 安装依赖

插件内置了条码和二维码组件，需要安装以下依赖：

```bash
# pnpm
pnpm add jsbarcode qrcode

# npm
npm install jsbarcode qrcode

# yarn
yarn add jsbarcode qrcode
```

### 引入插件

#### 方式一：组件引入（推荐）

```ts
import { PrintDesignerPage } from '@/packages/print-designer'
```

#### 方式二：全局插件引入

```ts
// main.ts
import { createApp } from 'vue'
import App from './App.vue'
import PrintDesignerPlugin from '@/packages/print-designer/print'

const app = createApp(App)
app.use(PrintDesignerPlugin) // 注入全局方法 $printByTemplateDesign
```

#### 方式三：自定义插件参数

```ts
import { createPrintDesignerPlugin } from '@/packages/print-designer/print'

app.use(
  createPrintDesignerPlugin({
    globalPropertyName: '$customPrint',
    exposeOnWindow: true,
    windowPropertyName: 'customPrint'
  })
)
```

---

## 📦 导出能力

| 导出项                             | 类型 | 说明                             |
| ---------------------------------- | ---- | -------------------------------- |
| `PrintDesignerPage`                | 组件 | 设计器页面主组件（完整三栏布局） |
| `PrintDesignerSidebar`             | 组件 | 左侧栏组件（组件库 + 图层管理）  |
| `PrintDesignerCanvas`              | 组件 | 中间画布组件（拖拽设计区域）     |
| `PrintDesignerPropsPanel`          | 组件 | 右侧属性面板组件                 |
| `createPrintDesignerSimpleAdapter` | 函数 | 快速创建业务适配器               |
| `printByTemplateDesign`            | 函数 | 按设计 JSON 直接打印             |
| `PrintDesignerPlugin`              | 插件 | Vue 全局打印插件                 |
| `types.ts` 全部类型定义            | 类型 | 完整的 TypeScript 类型导出       |

---

## 📖 参数说明

### PrintDesignerPage Props

| 参数 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| `templateId` | `number` | - | 否 | 当前模板 ID，用于加载模板信息与设计数据 |
| `adapter` | `PrintDesignerAdapter` | 空实现 | 否 | 数据适配器，对接模板查询、字段库、设计保存 |
| `defaultFieldLibrary` | `PrintDesignerFieldGroup[]` | 内置字段库 | 否 | 默认字段库（适配器未返回时使用） |
| `enableCustomTableColumns` | `boolean` | `false` | 否 | 是否开启表格预设列选择 |
| `presetTableColumns` | `PrintDesignerTableColumnOption[]` | `[]` | 否 | 预设表格列配置 |
| `paperSizeOptions` | `Array` | `['A4', 'A5', 'LETTER']` | 否 | 纸张尺寸选项（自动追加"自定义"） |
| `printDataList` | `Record<string, any>[]` | `[]` | 否 | 预览/打印用的测试数据 |
| `title` | `string` | 模板名称 | 否 | 页面标题 |
| `showBackButton` | `boolean` | `true` | 否 | 是否显示返回按钮 |
| `backButtonText` | `string` | `返回` | 否 | 返回按钮文案 |
| `saveButtonText` | `string` | `保存` | 否 | 保存按钮文案 |
| `uploadConfig` | `PrintDesignerUploadConfig` | - | 否 | 图片上传配置 |
| `onBack` | `() => void` | - | 否 | 自定义返回逻辑 |
| `onSave` | `(context) => Promise` | - | 否 | 自定义保存逻辑 |

### 组件事件

| 事件名 | 参数                       | 说明               |
| ------ | -------------------------- | ------------------ |
| `back` | -                          | 点击返回按钮时触发 |
| `save` | `PrintDesignerSaveContext` | 保存完成时触发     |

### 暴露方法

| 方法        | 签名                           | 说明                     |
| ----------- | ------------------------------ | ------------------------ |
| `getDesign` | `() => string`                 | 获取当前设计 JSON 字符串 |
| `print`     | `(dataList, mode?) => Promise` | 使用当前设计直接打印     |

---

## 🧩 组件类型详解

设计器支持 **11 种**画布组件类型：

| 组件类型   | `itemType`   | 说明                                          |
| ---------- | ------------ | --------------------------------------------- |
| **文本**   | `field`      | 普通数据字段文本，支持前缀/后缀拼接           |
| **标题**   | `title`      | 自定义标题文本，可独立设置样式                |
| **日期**   | `date`       | 日期组件，支持多种日期格式                    |
| **金额**   | `amount`     | 金额组件，支持千分位格式化与大写转换          |
| **表格**   | `table`      | 列表表格组件，支持自定义列、跨页续打表头      |
| **图片**   | `image`      | 图片组件，支持远程URL、本地上传、数据字段绑定 |
| **条码**   | `barcode`    | 一维条码，基于 JsBarcode（CODE128、EAN13 等） |
| **二维码** | `qrcode`     | 二维码，基于 QRCode                           |
| **横线**   | `hline`      | 水平分割线                                    |
| **竖线**   | `vline`      | 垂直分割线                                    |
| **页码**   | `pageNumber` | 页码组件，支持自定义格式                      |

---

## 🔌 适配器说明

设计器通过适配器模式与业务层解耦，你需要实现 `PrintDesignerAdapter` 接口：

```ts
interface PrintDesignerAdapter {
  // 返回左侧字段库
  getFieldLibrary(): Promise<PrintDesignerFieldGroup[]> | PrintDesignerFieldGroup[]

  // 返回模板快照（模板信息 + 设计数据）
  getTemplateSnapshot(templateId: number): Promise<PrintDesignerTemplateSnapshot>

  // 保存设计 JSON（可选）
  saveDesign?(params: {
    templateId: number
    templateDesignId?: number
    design: string
  }): Promise<{ id?: number }>
}
```

### 快速创建适配器

推荐使用 `createPrintDesignerSimpleAdapter` 快速生成适配器：

```ts
import { createPrintDesignerSimpleAdapter } from '@/packages/print-designer'

const adapter = createPrintDesignerSimpleAdapter({
  // 字段库
  fieldLibrary: [
    {
      name: '订单字段',
      fields: [
        { key: 'orderNo', label: '订单号', itemType: 'field' },
        { key: 'customerName', label: '客户名称', itemType: 'field' },
        { key: 'items', label: '商品明细', itemType: 'table' }
      ]
    }
  ],
  // 查询模板信息
  getTemplate: (id) => PrintTemplateApi.getPrintTemplate(id),
  // 查询设计数据
  getDesignByTemplateId: (id) => PrintTemplateDesignApi.getDesignByTemplateId(id),
  // 新增设计
  createDesign: (params) => PrintTemplateDesignApi.create(params),
  // 更新设计
  updateDesign: (params) => PrintTemplateDesignApi.update(params)
})
```

---

## 🖨️ 打印引擎

### Web 打印

- 基于浏览器原生打印能力
- 将设计 JSON 渲染为 HTML，通过 `window.print()` 输出
- 支持预览、直接打印、获取 HTML 内容三种模式

### LODOP 打印

- 基于 LODOP 云打印控件
- 毫米级精确定位，适合票据、运单等精确打印场景
- 需要业务系统自行保证 LODOP 运行环境

### 直接打印 API

```ts
import { printByTemplateDesign } from '@/packages/print-designer'

// Web 打印预览
await printByTemplateDesign(designJson, dataList, 'web')

// LODOP 打印预览
await printByTemplateDesign(designJson, dataList, { mode: 'lodop', action: 'preview' })

// 直接打印
await printByTemplateDesign(designJson, dataList, { mode: 'web', action: 'print' })

// 获取打印 HTML 内容
const html = await printByTemplateDesign(designJson, dataList, { mode: 'web', action: 'content' })
```

---

## 📁 项目结构

```
print-designer/
├── index.ts                          # 包入口，统一导出
├── print.ts                          # 打印引擎入口
├── simple.ts                         # 简易适配器工厂函数
├── types.ts                          # 完整类型定义
├── components/                       # 视图组件
│   ├── PrintDesignerPage.vue         # 主页面（三栏布局容器）
│   ├── PrintDesignerSidebar.vue      # 左侧栏（组件库 + 图层管理）
│   ├── PrintDesignerCanvas.vue       # 中间画布（拖拽设计区）
│   ├── PrintDesignerPropsPanel.vue   # 右侧属性面板
│   ├── PrintDesignerColorPicker.vue  # 颜色选择器
│   └── PrintDesignerSvgIcon.vue      # SVG 图标组件
├── composables/                      # 组合式 API
│   ├── useDesignerContext.ts         # 设计器核心上下文
│   ├── useCanvasItems.ts             # 画布组件增删改查
│   ├── useComponentStyles.ts         # 组件样式管理
│   ├── useDragResize.ts              # 拖拽缩放交互
│   ├── useHistory.ts                 # 撤销/重做历史栈
│   ├── usePaperConfig.ts             # 纸张配置管理
│   ├── useLocalStorage.ts            # 本地存储
│   ├── useLodopPrint.ts              # LODOP 打印
│   └── useNativeMessage.ts           # 消息提示
└── print/                            # 打印引擎子模块
    ├── units.ts                      # 单位转换工具
    ├── paper.ts                      # 纸张尺寸处理
    ├── normalize.ts                  # 参数规范化
    ├── data.ts                       # 数据解析与条件判断
    ├── table.ts                      # 表格数据处理
    ├── pagination.ts                 # 分页计算
    ├── styles.ts                     # 组件样式工具
    ├── barcode.ts                    # 条码/二维码处理
    ├── html-builder.ts               # HTML 生成
    ├── web-print.ts                  # Web 打印
    └── lodop.ts                      # LODOP 打印
```

---

## 🎯 适用场景

- **ERP 系统**：采购单、销售单、入库单、出库单等单据打印
- **WMS 系统**：库位标签、商品标签、装箱单打印
- **物流系统**：运单、快递面单打印
- **财务系统**：凭证、发票、对账单打印
- **任何需要自定义打印模板的业务系统**

---

## 📝 完整使用示例

```vue
<template>
  <PrintDesignerPage
    :template-id="templateId"
    :adapter="designerAdapter"
    :print-data-list="printDataList"
    :enable-custom-table-columns="true"
    :preset-table-columns="presetTableColumns"
    :upload-config="uploadConfig"
    title="采购订单打印模板"
    back-button-text="返回列表"
    save-button-text="保存模板"
    @save="handleSaveEvent"
    @back="handleBackEvent"
  />
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { PrintDesignerPage, createPrintDesignerSimpleAdapter } from '@/packages/print-designer'
import { PrintTemplateApi } from '@/api/erp/print/template'
import { PrintTemplateDesignApi } from '@/api/erp/print/printTemplateDesign'

const templateId = 12

// 打印测试数据
const printDataList = [
  {
    orderNo: 'PO20260530001',
    customerName: '测试客户',
    totalPrice: 1280.5,
    items: [
      { name: '商品A', spec: 'XL', count: 2, price: 100 },
      { name: '商品B', spec: 'L', count: 3, price: 200 }
    ]
  }
]

// 预设表格列
const presetTableColumns = [
  { title: '商品名称', field: 'name' },
  { title: '规格', field: 'spec' },
  { title: '数量', field: 'count' },
  { title: '单价', field: 'price' }
]

// 图片上传配置
const uploadConfig = {
  url: '/admin-api/infra/file/upload',
  headers: { Authorization: 'Bearer token-demo' },
  responseUrlField: 'data'
}

// 创建适配器
const designerAdapter = createPrintDesignerSimpleAdapter({
  fieldLibrary: [
    {
      name: '订单字段',
      fields: [
        { key: 'orderNo', label: '订单号', itemType: 'field' },
        { key: 'customerName', label: '客户名称', itemType: 'field' },
        { key: 'totalPrice', label: '订单金额', itemType: 'amount' },
        { key: 'items', label: '商品明细', itemType: 'table' }
      ]
    }
  ],
  getTemplate: (id) => PrintTemplateApi.getPrintTemplate(id),
  getDesignByTemplateId: (id) => PrintTemplateDesignApi.getPrintTemplateDesignByTemplateId(id),
  createDesign: (params) => PrintTemplateDesignApi.createPrintTemplateDesign(params),
  updateDesign: (params) => PrintTemplateDesignApi.updatePrintTemplateDesign(params)
})

const handleSaveEvent = (context) => {
  console.log('保存成功', context.design)
}

const handleBackEvent = () => {
  console.log('点击了返回')
}
</script>
```

---
## 适用行业与场景

### 适用行业

- ERP
- WMS
- SCM
- 电商后台
- 制造业系统
- 仓储物流系统
- 供应链系统
- 门店零售系统

### 适用单据

- 采购订单
- 销售订单
- 销售出库单
- 采购入库单
- 发货单
- 配送单
- 物流面单
- 商品标签
- 条码标签
- 财务打印单据
- 自定义业务单据

---

## 为什么值得买

### 不是从零开发

你买到的不是一个思路，而是一套已经具备完整打印设计链路的能力。

### 能直接放进项目里

它本身就是按“业务系统接入”思路设计的，模板加载、保存、字段库、打印都已经考虑到了。

### 支持二次开发

适合交付型团队、外包团队、独立开发者、企业内部研发团队基于源码继续扩展。

### 可复用价值高

同一套能力可以在多个项目里重复使用，越往后越省开发成本。

### 商业场景友好

对于需要经常做打印模块的项目来说，这类能力属于高频复用模块，投入一次，后续持续受益。

---

## 适合哪些人购买

- 正在做 ERP、WMS、进销存、供应链系统的开发者
- 需要快速交付客户项目的外包团队
- 需要可二次开发源码的技术团队
- 希望把打印能力做成内部基础模块的公司
- 需要支持多种单据模板的 SaaS 或后台系统团队

---

## 交付内容

默认可提供：

- 打印模板设计器源码
- 组件接入说明
- 基础使用文档
- 示例接入方式
- 打印调用说明

根据授权方案可提供：
- 源码授权
---

## 可定制内容

如有项目需求，可额外支持定制：

- 按业务字段定制字段库
- 增加新的组件类型
- 打印样式定制
- 模板初始化能力
- 特殊纸张格式支持
- 与现有系统深度集成
- 项目交付协助

---

## 授权方式

本项目用于商业授权合作。
可支持以下授权模式：
- 源码授权版(<span style="color:#e60000;">**￥499**</span>，无票)

具体价格、授权范围、更新方式、售后支持，请联系作者沟通。

---

## 售后支持

可提供以下服务：

- 接入指导
- 问题答疑
- 缺陷修复
- 项目落地支持

说明：

- 默认售后内容以约定方案为准
- 深度定制需求需单独评估工时
- 商业授权与定制服务可分别报价

---

## 联系方式

如需购买、咨询、试用、演示、定制开发，请联系作者：

- 微信：YTHfmr

![微信图片_20260525212142_13_9.png](https://raw.gitcode.com/user-images/assets/9951208/97fd7d24-bcf9-4d98-99ed-b6bc40f0f443/微信图片_20260525212142_13_9.png '微信图片_20260525212142_13_9.png')

建议联系时直接说明：

- 你的项目类型
- 需要打印哪些单据
- 当前技术栈
- 是否需要源码
- 是否需要二次开发或定制支持

---

## 购买建议

如果你现在的需求属于以下任意一种，建议直接联系：

- 想快速给后台系统增加打印模板设计能力
- 想减少每个单据模板重复开发的成本
- 想让打印模板支持业务配置而不是写死代码
- 想兼容 Web 与 LODOP
- 想购买一套可商用、可扩展、可交付的源码方案

---

## 声明

本页内容用于项目能力展示与商业合作说明，最终授权内容、交付范围、价格与服务内容，以实际沟通结果为准。
