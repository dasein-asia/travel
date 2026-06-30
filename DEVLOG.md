# 新乡 · 南太行旅游网站 — 开发记录

## 项目结构

```
G:\Claude Code\tracel-xinxiang\
├── index.html                  # 主页（景点、行程、地图、美食、费用等）
├── attraction-baligou.html     # 八里沟 · 天河瀑布
├── attraction-wanxianshan.html # 万仙山 · 郭亮挂壁公路
├── attraction-tianjieshan.html # 天界山 · 云峰画廊
├── attraction-baoquan.html     # 宝泉 · 太行碧水
├── attraction-guanshan.html    # 关山国家地质公园
├── attraction-food.html        # 新乡 · 太行美食
├── images/                     # 图片素材（Pixabay下载，无人像）
└── DEVLOG.md                   # 本文件
```

## 版本更新记录

### v2.1 — 克莱因蓝配色方案

#### 变更内容
1. **主题色从墨绿改为克莱因蓝**：主色 `#002FA7`（克莱因蓝），辅色 `#C49B3E`（金色）
2. **index.html 变量重命名**：`--green` → `--blue`, `--brown` → `--gold`，所有引用同步更新
3. **所有详情页 :root 更新**：`--green`/`--brown` 变量的色值改为蓝金配色，变量名保持兼容
4. **暖色背景调整为冷色调**：`--warm: #F0F2F8`（蓝灰暖白），`--cream: #F8F9FC`
5. **修复 tianjieshan.html 未定义 `--slate` 变量的问题**

### v2.0 — 青岛出发·4天3夜·两大一小亲子版

#### 变更内容
1. **出发地改为青岛**：全程高铁，早出发中午到新乡（参考G2078 06:48→11:27）
2. **行程扩展为4天3夜**：
   - Day 1: 青岛→新乡（高铁），下午游览比干庙/潞王陵
   - Day 2: 万仙山·郭亮挂壁公路
   - Day 3: 八里沟·天河瀑布
   - Day 4: 天界山·云峰画廊→返程
3. **两大一小（9岁）**：预算调整（儿童半价门票），贴士增加亲子建议
4. **美食图片全部更换**：旧图不正确，重搜无人物美食摄影
5. **光影太行图库扩充**：从8张增至12张，移除含人物图片（scenic_hiking.jpg）

#### 美食图片替换清单（多次精细筛选）
| 菜品 | 最终选用 | 筛选标准 |
|------|----------|----------|
| 红焖羊肉 | food_meat_stew.jpg（匈牙利炖牛肉） | 深色肉块浓汁炖菜，接近红烧色泽 |
| 获嘉饸饹面 | food_beef_noodle.jpg（牛肉面） | 中式面汤，类似饸饹面形态 |
| 地锅鸡 | food_chicken_dish.jpg（烤鸡块） | 鸡块菜品，接近地锅鸡形态 |
| 小米焖饭 | food_millet.jpg（小米谷物） | 黄小米实拍，最匹配小米焖饭 |
| 牛忠喜烧饼 | food_sesame_bread.jpg（芝麻面包） | 芝麻覆盖的烘焙面食 |
| 太行蒸野菜 | food_stir_fry.jpg（中式炒菜） | 中式烹饪绿蔬，接近蒸野菜形态 |

注：Pixabay 图库中式菜品有限，以上为经过4轮搜索后最佳匹配方案。

#### 新增风景图（无人像）
- scenic_forest.jpg — 山林湖泊
- scenic_lake.jpg — 山间湖泊倒影
- scenic_winding_road.jpg — 盘山公路
- scenic_red_cliff.jpg — 红色岩壁
- scenic_peak.jpg — 山峰云顶
- scenic_waterfall2.jpg — 瀑布（第二张）

#### 移除的含人物图片
- scenic_hiking.jpg（登山者）
- scenic_valley.jpg（背包客标签，谨慎替换）

## 开发过程

### 1. 规划与调研
- 通过 web search 收集新乡南太行旅游信息：景点、门票、行程、交通、美食
- 参考 TRAVEL 项目结构（Hero、景点卡片、行程时间线、地图、图库、美食、费用）

### 2. 图片素材（Pixabay 免费图库）
所有图片来自 Pixabay 免费 API，日限5000次，可商用无需署名。
搜索策略：先中文、无结果自动降级英文。人像关键词规避（避免people, man, woman, backpacker等）。

### 3. 主页 (index.html)
- 全屏 Hero 头图 + 云海飘移动画
- 统计条（4天行程/6+景点/总预算¥3,500/22°C均温）
- 6个景点卡片网格（可点击跳转详情页）
- 4天行程时间线（图片右侧排列）
- 路线辐射图（新乡枢纽 → 各景区）
- Leaflet.js + 高德地图瓦片（标注5个核心景点+新乡枢纽）
- 光影相册（12张图片网格，无人像）
- 美食展示（6种美食卡片，实拍美食图）
- 费用预估（2大1小明细）+ 景点一览表格
- 6个实用贴士卡片（含亲子建议）
- CTA 横幅 + 页脚

### 4. 配色方案 (v2.1)
- 主色：#002FA7（克莱因蓝）
- 辅色：#C49B3E（金色）
- 深色：#001A6E / #1A4DC4
- 冷调背景：#F0F2F8 / #F8F9FC

### 5. 技术要点
- Leaflet.js + 高德地图瓦片（无需 API Key）
- IntersectionObserver 滚动渐入动画
- 页面切换过渡动画
- 响应式布局适配移动端
- Google Fonts 字体（Noto Serif SC + Noto Sans SC + Inter）
