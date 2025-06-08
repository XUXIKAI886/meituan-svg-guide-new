# SVG图表生成规则文档（优化版）

## 1. 整体设计原则

### 1.1 画布设置
- 宽度：1280像素
- 高度：780像素
- 背景色：浅灰色 (#f5f5f5或#f0f0f0)
- 编码：必须使用UTF-8以正确显示中文字符

```xml
<?xml version="1.0" encoding="UTF-8"?>
<svg width="1280" height="780" xmlns="http://www.w3.org/2000/svg">
  <!-- 背景 -->
  <rect width="1280" height="780" fill="#f5f5f5"/>
  <!-- 内容元素 -->
</svg>
```

### 1.2 结构组织
- 使用清晰的视觉层级
- 标题区域位于顶部
- 主要内容区域分为多个卡片或模块
- 使用矩形区分不同功能区域
- 保持足够的空白区域提高可读性

## 2. 颜色系统

### 2.1 推荐颜色主题
- 标题区域：
  * 渐变橙红色 (从 #FF5722 到 #FF9800)
  * 纯橙红色 (#FF5722)
- 内容区域建议色：
  * 绿色系 (#4CAF50, #66BB6A, #43A047)
  * 蓝色系 (#2196F3, #42A5F5, #1E88E5)
  * 紫色系 (#9C27B0, #AB47BC, #8E24AA)
  * 橙色系 (#FF5722, #FF7043, #F4511E)
  * 金黄色系 (#FFC107, #FFB300, #FFA000)
  * 靛青色系 (#3F51B5, #5C6BC0, #3949AB)
- 子卡片颜色：
  * 绿色子卡片 (#66BB6A, #81C784)
  * 蓝色子卡片 (#64B5F6, #90CAF9)
  * 紫色子卡片 (#BA68C8, #CE93D8)
  * 橙色子卡片 (#FF8A65, #FFAB91)
  * 黄色子卡片 (#FFD54F, #FFE082)
  * 靛青子卡片 (#7986CB, #9FA8DA)
- 强调色：
  * 突出信息 (#FFC107, #FF9800)
  * 次要信息 (#90A4AE, #B0BEC5)
- 底部信息区域：
  * 浅蓝色 (#81D4FA, #B3E5FC)
  * 橙黄色 (#FFB74D, #FFD180)

### 2.2 色彩搭配建议
- 每个主题模块使用不同颜色系列区分
- 同一主题内的子元素使用相同色系但不同深浅
- 确保文字与背景有足够对比度（通常使用白色文字在深色背景上）
- 创建视觉层次感：标题区域 > 主要功能区域 > 子卡片区域 > 底部总结区域
- 相关内容使用近似色彩，增强关联性
- 使用渐变可以增强顶部或底部区域的视觉效果

### 2.3 渐变建议
```xml
<!-- 标题区域橙色渐变 -->
<linearGradient id="headerGradient" x1="0%" y1="0%" x2="100%" y2="0%">
  <stop offset="0%" style="stop-color:#FF5722"/>
  <stop offset="100%" style="stop-color:#FF9800"/>
</linearGradient>
<rect x="0" y="0" width="1280" height="110" fill="url(#headerGradient)"/>

<!-- 底部区域蓝色渐变 -->
<linearGradient id="footerGradient" x1="0%" y1="0%" x2="100%" y2="0%">
  <stop offset="0%" style="stop-color:#29B6F6"/>
  <stop offset="100%" style="stop-color:#4FC3F7"/>
</linearGradient>
<rect x="40" y="730" width="1200" height="30" fill="url(#footerGradient)" rx="10" ry="10"/>
```

## 3. 文本与排版

### 3.1 字体设置
- 字体族：Arial（无衬线字体，兼容性好）
- 标题：大小36px，粗体，白色文字
- 模块标题：大小22-24px，粗体
- 子标题：大小18-20px，粗体
- 正文内容：大小14-16px，普通
- 说明文字：大小12-14px，普通

### 3.2 文本对齐与布局
- 标题居中对齐：`text-anchor="middle"`
- 区域标题左对齐或居中
- 内容文本根据需要对齐
- 使用行距保持文本可读性
- 利用`<line>`元素作为标题下的分隔线

```xml
<text x="640" y="55" font-family="Arial" font-size="36" font-weight="bold" fill="white" text-anchor="middle">标题文本</text>
<line x1="130" y1="180" x2="350" y2="180" stroke="white" stroke-width="2"/>
```

## 4. 模块布局

### 4.1 卡片设计
- 主要区域：圆角矩形 (rx="15" ry="15")
- 子卡片：较小圆角 (rx="10" ry="10")
- 卡片内边距：约20-30px
- 卡片间距：约20px
- 使用line元素作为卡片内部分隔线

### 4.2 布局方式
- 水平排列主要模块
- 垂直堆叠相关内容
- 保持对齐（顶部对齐、底部对齐）
- 合理利用空间，避免过度拥挤

### 4.3 元素组织
- 相关元素放在一起
- 使用明确的分组
- 保持一致的间距和对齐

## 5. 常用元素设计

### 5.1 标题区域
```xml
<!-- 标准橙红色渐变标题栏 -->
<linearGradient id="headerGradient" x1="0%" y1="0%" x2="100%" y2="0%">
  <stop offset="0%" style="stop-color:#FF5722"/>
  <stop offset="100%" style="stop-color:#FF9800"/>
</linearGradient>
<rect x="0" y="0" width="1280" height="110" fill="url(#headerGradient)"/>
<text x="640" y="55" font-family="Arial" font-size="36" font-weight="bold" fill="white" text-anchor="middle">标题文本</text>
```

### 5.2 主要内容区域示例

```xml
<!-- 绿色主题区域 -->
<rect x="40" y="120" width="580" height="240" rx="15" ry="15" fill="#4CAF50"/>
<text x="330" y="155" font-family="Arial" font-size="24" font-weight="bold" fill="white" text-anchor="middle">绿色区域标题</text>
<line x1="130" y1="170" x2="530" y2="170" stroke="white" stroke-width="2"/>

<!-- 蓝色主题区域 -->
<rect x="640" y="120" width="580" height="240" rx="15" ry="15" fill="#2196F3"/>
<text x="930" y="155" font-family="Arial" font-size="24" font-weight="bold" fill="white" text-anchor="middle">蓝色区域标题</text>
<line x1="730" y1="170" x2="1130" y2="170" stroke="white" stroke-width="2"/>

<!-- 紫色主题区域 -->
<rect x="40" y="380" width="580" height="240" rx="15" ry="15" fill="#9C27B0"/>
<text x="330" y="415" font-family="Arial" font-size="24" font-weight="bold" fill="white" text-anchor="middle">紫色区域标题</text>
<line x1="130" y1="430" x2="530" y2="430" stroke="white" stroke-width="2"/>

<!-- 金黄色主题区域 -->
<rect x="40" y="380" width="1180" height="120" rx="15" ry="15" fill="#FFC107"/>
<text x="640" y="415" font-family="Arial" font-size="24" font-weight="bold" fill="white" text-anchor="middle">黄色区域标题</text>
<line x1="350" y1="430" x2="930" y2="430" stroke="white" stroke-width="2"/>

```

### 5.3 内容卡片

```xml
<!-- 绿色系子卡片 -->
<rect x="60" y="190" width="250" height="150" rx="10" ry="10" fill="#66BB6A"/>
<text x="185" y="220" font-family="Arial" font-size="20" font-weight="bold" fill="white" text-anchor="middle">卡片标题</text>
<text x="80" y="255" font-family="Arial" font-size="16" fill="white">• 内容项目1</text>
<text x="80" y="285" font-family="Arial" font-size="16" fill="white">• 内容项目2</text>

<!-- 蓝色系子卡片 -->
<rect x="60" y="190" width="250" height="150" rx="10" ry="10" fill="#64B5F6"/>
<text x="185" y="220" font-family="Arial" font-size="20" font-weight="bold" fill="white" text-anchor="middle">卡片标题</text>
<text x="80" y="255" font-family="Arial" font-size="16" fill="white">• 内容项目1</text>
<text x="80" y="285" font-family="Arial" font-size="16" fill="white">• 内容项目2</text>

<!-- 紫色系子卡片 -->
<rect x="60" y="190" width="250" height="150" rx="10" ry="10" fill="#BA68C8"/>
<text x="185" y="220" font-family="Arial" font-size="20" font-weight="bold" fill="white" text-anchor="middle">卡片标题</text>
<text x="80" y="255" font-family="Arial" font-size="16" fill="white">• 内容项目1</text>
<text x="80" y="285" font-family="Arial" font-size="16" fill="white">• 内容项目2</text>
```

### 5.4 列表与项目符号
```xml
<text x="80" y="255" font-family="Arial" font-size="16" fill="white">• 列表项目1</text>
<text x="80" y="285" font-family="Arial" font-size="16" fill="white">• 列表项目2</text>
<text x="80" y="315" font-family="Arial" font-size="16" fill="white">• 列表项目3</text>
```

### 5.5 数字标记与圆形背景
```xml
<!-- 带数字的圆形标记 -->
<circle cx="170" cy="430" r="25" fill="#333"/>
<text x="170" y="435" font-family="Arial" font-size="16" fill="white" text-anchor="middle">1</text>

<circle cx="280" cy="430" r="25" fill="#333"/>
<text x="280" y="435" font-family="Arial" font-size="16" fill="white" text-anchor="middle">2</text>

<circle cx="390" cy="430" r="25" fill="#333"/>
<text x="390" y="435" font-family="Arial" font-size="16" fill="white" text-anchor="middle">3</text>

<circle cx="500" cy="430" r="25" fill="#333"/>
<text x="500" y="435" font-family="Arial" font-size="16" fill="white" text-anchor="middle">4</text>
```

## 6. 常用布局模式

### 6.1 多卡片横向排列
```xml
<!-- 四个横向排列的彩色卡片 -->
<rect x="100" y="130" width="250" height="180" rx="15" ry="15" fill="#4CAF50"/>
<!-- 绿色卡片内容 -->

<rect x="370" y="130" width="250" height="180" rx="15" ry="15" fill="#2196F3"/>
<!-- 蓝色卡片内容 -->

<rect x="640" y="130" width="250" height="180" rx="15" ry="15" fill="#9C27B0"/>
<!-- 紫色卡片内容 -->

<rect x="910" y="130" width="250" height="180" rx="15" ry="15" fill="#FF5722"/>
<!-- 橙色卡片内容 -->
```

### 6.2 步骤/流程布局
```xml
<rect x="100" y="340" width="1080" height="160" rx="15" ry="15" fill="#FFC107"/>
<text x="640" y="380" font-family="Arial" font-size="28" font-weight="bold" fill="#333" text-anchor="middle">流程标题</text>

<circle cx="200" cy="430" r="25" fill="#333"/>
<text x="200" y="435" font-family="Arial" font-size="16" fill="white" text-anchor="middle">1</text>
<text x="200" y="480" font-family="Arial" font-size="16" fill="#333" text-anchor="middle">步骤1说明</text>

<circle cx="400" cy="430" r="25" fill="#333"/>
<text x="400" y="435" font-family="Arial" font-size="16" fill="white" text-anchor="middle">2</text>
<text x="400" y="480" font-family="Arial" font-size="16" fill="#333" text-anchor="middle">步骤2说明</text>

<circle cx="600" cy="430" r="25" fill="#333"/>
<text x="600" y="435" font-family="Arial" font-size="16" fill="white" text-anchor="middle">3</text>
<text x="600" y="480" font-family="Arial" font-size="16" fill="#333" text-anchor="middle">步骤3说明</text>

<circle cx="800" cy="430" r="25" fill="#333"/>
<text x="800" y="435" font-family="Arial" font-size="16" fill="white" text-anchor="middle">4</text>
<text x="800" y="480" font-family="Arial" font-size="16" fill="#333" text-anchor="middle">步骤4说明</text>
```

### 6.3 双模块并排布局
```xml
<rect x="40" y="520" width="580" height="200" rx="15" ry="15" fill="#5C6BC0"/>
<text x="330" y="555" font-family="Arial" font-size="24" font-weight="bold" fill="white" text-anchor="middle">左侧模块标题</text>
<line x1="130" y1="570" x2="530" y2="570" stroke="white" stroke-width="2"/>
<!-- 左侧内容 -->

<rect x="640" y="520" width="580" height="200" rx="15" ry="15" fill="#7B1FA2"/>
<text x="930" y="555" font-family="Arial" font-size="24" font-weight="bold" fill="white" text-anchor="middle">右侧模块标题</text>
<line x1="730" y1="570" x2="1130" y2="570" stroke="white" stroke-width="2"/>
<!-- 右侧内容 -->
```

### 6.4 底部总结区域
```xml
<rect x="40" y="740" width="1200" height="30" rx="10" ry="10" fill="#FF9800"/>
<text x="640" y="760" font-family="Arial" font-size="18" font-weight="bold" fill="white" text-anchor="middle">总结文字或关键要点</text>
```

## 7. 注释与文档

### 7.1 SVG注释
- 使用XML注释标记不同区域
- 每个主要区域前添加注释
- 保持注释简洁明了

```xml
<!-- 区域描述 -->
```

### 7.2 元素组织
- 相关元素放在一起
- 按从上到下、从左到右的顺序排列元素
- 使用空行分隔不同区域

## 8. 最佳实践

### 8.1 简化与兼容性
- 避免使用复杂的SVG功能（如复杂渐变、滤镜、动画）
- 使用基本形状和元素（矩形、圆形、线条、文本）
- 保持SVG结构清晰、简洁
- 测试在不同浏览器和查看器中的显示效果

### 8.2 组织与维护
- 使用注释标记不同区域
- 按逻辑组织相关元素
- 使用一致的命名和属性顺序
- 保持代码整洁易读

### 8.3 优化建议
- 使用明确的颜色对比
- 控制文本数量，保持简洁
- 每个图表聚焦于一个主题
- 使用直观的视觉层次引导阅读流程

## 9. 实际应用示例

### 9.1 产品介绍图
- 顶部：产品名称和标题（橙色渐变背景）
- 中间：主要特点和功能（多彩色卡片）
- 底部：使用步骤或总结（浅色背景或橙色背景）

### 9.2 数据对比图
- 顶部：对比主题（橙色或紫色背景）
- 中间：不同类别的数据展示（多彩色卡片）
- 底部：结论或建议（浅色背景）

### 9.3 流程指南图
- 顶部：流程名称（橙色渐变背景）
- 中间：步骤说明（黄色背景配黑色数字标记）
- 底部：补充信息或建议（浅蓝色背景）

## 10. 建议使用的配色方案

### 10.1 产品与功能介绍配色
- 标题：橙红色渐变 (#FF5722 到 #FF9800)
- 主要功能区块：绿色 (#4CAF50)、蓝色 (#2196F3)、紫色 (#9C27B0)、橙色 (#FF5722)
- 次要内容区块：黄色 (#FFC107)
- 底部区域：浅蓝色 (#81D4FA) 或橙色 (#FF9800)

### 10.2 流程与步骤配色
- 标题：橙红色渐变 (#FF5722 到 #FF9800)
- 流程主区域：黄色 (#FFC107)
- 步骤编号：黑色圆圈 (#333333) 配白色数字
- 步骤说明：黑色文字 (#333333)
- 底部总结：蓝色 (#2196F3) 配白色文字

### 10.3 对比与数据配色
- 标题：橙红色渐变 (#FF5722 到 #FF9800)
- 左侧数据区域：深蓝色 (#3F51B5)
- 右侧数据区域：深紫色 (#7B1FA2)
- 数据卡片：蓝色系 (#5C6BC0)、紫色系 (#BA68C8)
- 底部总结：橙色 (#FF9800) 配白色文字

## 11. 元素坐标参考

### 11.1 标准布局坐标
- 标题区：x=0, y=0, width=1280, height=110px
- 第一行内容：x=40-60, y=120-130
- 第二行内容：x=40-60, y=340-360
- 第三行内容：x=40-60, y=520-540
- 底部区域：x=40, y=740, width=1200, height=30

### 11.2 子元素布局
- 子元素间水平间距：20-25px
- 子元素间垂直间距：15-20px
- 子元素宽度：根据内容和布局灵活调整（200-280px较为常见）
- 子元素高度：根据内容灵活调整（100-180px较为常见）

## 12. 品牌标签与版权声明

### 12.1 品牌标签
- 位置：左上角，通常在x=20, y=20位置
- 背景：半透明黑色背景 (rgba(0,0,0,0.6))
- 文字：白色 (#ffffff)，大小16-18px，粗体
- 形式：圆角矩形，rx=5, ry=5

```xml
<!-- 品牌标签示例 -->
<rect x="20" y="20" width="110" height="30" rx="5" ry="5" fill="rgba(0,0,0,0.6)"/>
<text x="75" y="40" font-family="Arial" font-size="16" font-weight="bold" fill="white" text-anchor="middle">呈尚策划</text>
```

### 12.2 版权声明
- 位置：右上角，通常在x=1100, y=20位置
- 背景：半透明黑色背景 (rgba(0,0,0,0.6))
- 文字：白色 (#ffffff)，大小14-16px
- 形式：圆角矩形，rx=5, ry=5

```xml
<!-- 版权声明示例 -->
<rect x="1100" y="20" width="160" height="30" rx="5" ry="5" fill="rgba(0,0,0,0.6)"/>
<text x="1180" y="40" font-family="Arial" font-size="14" fill="white" text-anchor="middle">版权所有 盗版必究</text>
```

### 12.3 使用规范
- 所有SVG图表必须包含品牌标签和版权声明
- 保持半透明效果，确保可读性的同时不遮挡主要内容
- 保持位置一致性，始终放置在左上角和右上角
- 确保文本清晰可见，与背景有足够对比度
- 根据实际图表内容可微调位置，避免与重要内容重叠