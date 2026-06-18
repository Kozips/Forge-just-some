# 图片提示词模版

> 从参考提示词蒸馏提取的稳定出图结构。填空即用，不改结构只换内容。

---

## 提示词库索引（按类型分）

| 类型 | 文件 | 内容 |
|------|------|------|
| 动漫肖像 | [动漫肖像.md](动漫肖像.md) | 动漫风格角色特写、肖像、近距离人像 |
| 写实人像 | [写实人像.md](写实人像.md) | 写实摄影风格人像、自拍、时尚摄影 |
| 海报与封面 | [海报与封面.md](海报与封面.md) | 宣传海报、封面设计、品牌视觉 |
| 社交媒体与营销 | [社交媒体与营销.md](社交媒体与营销.md) | 社交媒体帖子、营销视觉、日常分享 |
| 漫画与故事板 | [漫画与故事板.md](漫画与故事板.md) | 漫画分格、故事板、角色卡片 |
| 信息图与教育 | [信息图与教育.md](信息图与教育.md) | 信息图、教育视觉、日历、杂志排版 |
| 产品与美食 | [产品与美食.md](产品与美食.md) | 产品摄影、美食摄影、电商视觉 |
| 动漫表演与舞台 | [动漫表演与舞台.md](动漫表演与舞台.md) | 偶像、演唱会、后台、舞台表演 |
| 概念艺术与奇幻 | [概念艺术与奇幻.md](概念艺术与奇幻.md) | 概念艺术、超现实、奇幻场景 |

---

## 为什么这个结构稳定出好图

参考提示词之所以"怎么换角色都是同一张图的质量"，是因为它**把所有视觉信息都压进了 Caption 一条线里**，不依赖 UserPrompt 的标签拆分。模型只需要读一段完整的自然语言描述，就能把构图、光影、特效、情绪全部对齐。

对比：

| 写法 | 效果 | 原因 |
|------|------|------|
| 标签堆砌（UserPrompt 独用） | 元素对但构图乱 | 标签之间没有空间关系，模型自由发挥 |
| Caption 独用 | 构图稳但细节丢 | 自然语言描述不够精准时模型会偷懒 |
| **UserPrompt + Caption 双路对齐** | 元素对且构图稳 | 标签锁定"有什么"，Caption 锁定"怎么排" |

**核心规则：Caption 必须是完整的、自洽的、不需要标签补充就能独立成图的描述。**

---

## Caption 结构（10步，每步一句话）

按顺序填，每步只写一句话，不跳步不合并：

```
① 开场：[画质] + [风格] + [角色识别] + [镜头类型] + [拍摄角度]
② 位置：角色在画面中的[位置] + [填充方式] + [透视效果]
③ 头发：[颜色] + [长度] + [动态] + [特殊标记]
④ 眼睛：[颜色] + [瞳孔形状] + [眼神方向] + [表情分类标签]
⑤ 面部光影：[遮挡物] + [产生的光影效果名称] + [对氛围的作用]
⑥ 服装：[层次1] + [层次2] + [颜色] + [细节] + [暗示的世界观]
⑦ 动作（左手）：[方向] + [手势] + [动态程度]
⑧ 动作（右手）：[方向] + [手势] + [动态程度]
⑨ 特效：[特效类型] + [颜色] + [运动方式] + [形状] + [与角色的空间关系]
⑩ 收尾：[画质标签] + [艺术效果] + [背景] + [光照方向和来源]
```

### 每步的写法要点

**① 开场（定基调的一句话）**
- 必须包含：画质词（an extremely detailed）+ 风格（digital illustration in anime style）+ 角色识别（features a young girl, identified as $character_1$）+ 镜头（close-up / medium shot / full body）+ 角度（Dutch angle / from below / from above）
- 示例：`An extremely detailed, vibrant, and dynamic digital illustration in anime style features a young girl, identified as $character_1$, in an extreme close-up, tight shot, captured with a dramatic Dutch angle.`

**② 位置（角色在画面哪里）**
- 必须说清楚：在前景还是背景、居中还是偏左偏右、是否填满画面
- 常用：`filling the entire frame in the center-foreground` / `positioned to the left with space on the right` / `receding into the background`
- 加透视效果词：`creating an intense, immersive perspective` / `with a foreshortened body`

**③ 头发（从上往下写）**
- 顺序：颜色 → 长度 → 动态（风/飘浮/静止）→ 特殊标记（呆毛/刘海/碎发）
- 必须有动态：头发不是静物，要么风吹、要么飘浮、要么垂落
- 示例：`She has long, bright blue hair that appears to be floating dynamically around her head and shoulders, with a small ahoge visible on top.`

**④ 眼睛（传神的关键）**
- 顺序：颜色 → 瞳孔形状（sharp/round/slitted）→ 眼神方向（toward the viewer / to the side / down）→ 表情分类（jitome / sanpui / tsurime / furime）
- 用日系表情分类词比用形容词精准：jitome=半闭嫌弃眼、sanpui=三白眼、tsurime=吊眼角冷淡、furime=媚眼
- 示例：`Her intense, concerned blue eyes with sharp pupils stare directly out of the frame toward the viewer, conveying a serious and focused expression, categorized as jitome.`

**⑤ 面部光影（戏剧感来源）**
- 必须有一个遮挡物制造的光影效果：帽子阴影、头发投影、手的遮挡、窗户格栅
- 光影效果命名：cut light=切割光（明暗交界线分明）、rim light=轮廓光、chiaroscuro=明暗对比
- 示例：`The top half of her face is obscured by a shadow cast by her very large, wide-brimmed black witch hat, creating a dramatic cut light effect that enhances the intense atmosphere.`

**⑥ 服装（从外到内写）**
- 顺序：最外层 → 中间层 → 最内层 → 颜色 → 细节 → 暗示的世界观
- 必须提到服装和特效的关系：是否被特效遮挡、是否随风飘动
- **服装必须和背景有对比**：写清楚服装颜色相对于背景的反差（`bright white contrasting sharply with the turquoise ocean` / `the dark fabric stands out against the pale wall`）。浅色衣服+浅色背景=融在一起，必须强调 `defined edges, clear outline, distinct from background`
- 示例：`She is wearing a bright white string bikini, the fabric clearly defined with crisp edges and a distinct outline against her milk-white skin, the bright white contrasting sharply with the turquoise ocean and warm golden sand behind her.`

**⑦⑧ 动作（左右手分开写）**
- 每只手必须独立一句话
- 必须包含：方向（extending out / raised to / resting on）+ 手势（open and pointing / gripping / supporting）+ 动态程度（dramatically / gently / slowly）
- **手指必须写清楚**：`fingers spread naturally with detailed, correctly proportioned five fingers` / `each finger clearly rendered with correct anatomy`
- 左手通常做主要动作（指向镜头/施法/挥手），右手做辅助动作（扶帽/叉腰/托腮）
- 示例左手：`Her left arm extends dramatically out of the image plane, with her hand open, fingers spread naturally with detailed five fingers, pointing towards the camera.`
- 示例右手：`Her right hand rests confidently on her hip, each finger clearly rendered with correct anatomy.`

**⑨ 特效（让画面活起来的部分）**
- 必须包含：特效类型（fluid dynamics / vortex / particle effects / fire / lightning）+ 颜色（cerulean blue / crimson / emerald）+ 运动方式（spiraling / swirling / cascading / erupting）+ 形状（three-dimensional spiral / ring / dome）+ 与角色的空间关系（around her body / beneath her feet / emanating from her hands）
- 没有特效也要写环境动态：风、雨、灰尘飘浮、光粒子
- 示例：`The entire scene is enveloped in a powerful, dynamic effect of fluid dynamics and a vortex. Cerulean blue water, or fluid, is spiraling and swirling around her body and hand, creating a three-dimensional spiral structure that dominates the composition.`

**⑩ 收尾（打包所有技术参数）**
- 分四层收：画质标签 → 艺术效果 → 背景 → 光照
- 画质标签：`high resolution, best quality, master-level detail, sharp focus, crisp linework`
- 艺术效果：必须有至少一个（chromatic aberration / bokeh / film grain / lens flare / motion blur）。**注意：bokeh 只用于背景虚化，不要加在主体上。** 如果场景需要清晰（阳光沙滩、办公室、教室），用 `sharp focus throughout, no soft diffusion` 代替 bokeh
- 背景：必须明确写背景和主体的分离关系（`clear separation between character and background` / `the dark background further emphasizes the character`）
- 光照：必须有光源方向 + 光照类型 + 打在哪里 + 对比度。`strong golden-hour rim light from behind creating a bright, defined outline, with high contrast`

---

## 完整填空模版

```
An extremely detailed, [动态词] digital illustration in [风格] features [角色描述], identified as $character_1$, in a [镜头类型], [镜头补充], captured with a [拍摄角度][cite: 36, 38].

$Character_1$, who resembles [参考角色], is positioned to [画面位置], creating a [透视效果][cite: 15, 32]. [③头发描述][cite: 31, 32]. [④眼睛描述], categorized as [表情标签][cite: 31, 34]. [⑤面部光影描述], creating a dramatic [光影效果名] effect that [氛围作用], contributes to her [面部状态][cite: 36, 37]. She is wearing [⑥服装描述], suggesting a [世界观暗示][cite: 31]. The clothing is [与特效的关系][cite: 38]. [⑦左手动作描述][cite: 32]. [⑧右手动作描述][cite: 32]. [⑨特效描述][cite: 36, 38]. [补充特效细节], giving the scene a [特效气质][cite: 37, 38]. The art style is defined by [画质标签], with noticeable artistic effects such as [艺术效果] enhancing the [艺术效果的作用][cite: 37]. [⑩背景描述][cite: 36]. The lighting is [光照类型], with [光照细节][cite: 37]. This is an illustration with an [构图气质][cite: 36].
```

---

## UserPrompt XML 模版

```xml
<character_1>
<n>$character_1$</n>
<gender>[1girl / 1boy]</gender>
<appearance>[头发颜色+长度+动态, 眼睛颜色+瞳孔, 肤色, 特殊标记]</appearance>
<clothing>[外层+中层+内层+颜色+配饰]</clothing>
<body_type>[体型, 胸围, 身高特征]</body_type>
<expression>[表情类型+眼神+嘴型+情绪标签]</expression>
<action>[左手动作, 右手动作, 身体姿态, 动态程度]</action>
<interaction>[与镜头的关系: pointing at viewer / looking away / no eye contact]</interaction>
<position>[镜头类型, 画面位置, 拍摄角度]</position>
</character_1>
<general_tags>
<count>[1girl / 1boy / 2girls]</count>
<style>[画风标签]</style>
<background>[背景类型]</background>
<environment>[环境物件]</environment>
<perspective>[拍摄角度]</perspective>
<atmosphere>[氛围标签]</atmosphere>
<lighting>[光照类型+方向+强度]</lighting>
<quality>[画质标签]</quality>
<objects>[场景中的关键物件]</objects>
<other>[艺术效果标签]</other>
</general_tags>
```

---

## Prompt Template（系统提示词·固定不动）

```
You are an assistant designed to generate high-quality anime images with the highest degree of image-text alignment based on xml format textual prompts. <Prompt Start>
{
"character_1": {
"bbox": [
0,
0,
1000,
1000
],
"name": "$character_1$"
},
"image": {
"tags": "{user_prompt}",
"caption": "{caption}"
}
}
```

---

## 参考范例（原始提示词）

> 这就是那个"怎么换都是同一张图质量"的原始提示词。填空模版就是从它蒸馏出来的。

**Caption：**
```
An extremely detailed, vibrant, and dynamic digital illustration in an anime style features a young girl, identified as $character_1$, in an extreme close-up, tight shot, captured with a dramatic Dutch angle[cite: 36, 38]. $Character_1$, who resembles Roxy Migurdia, is positioned to fill the entire frame in the center-foreground, creating an intense, immersive perspective[cite: 15, 32]. She has long, bright blue hair that appears to be floating dynamically around her head and shoulders, with a small ahoge visible on top[cite: 31, 32]. Her intense, concerned blue eyes with sharp pupils stare directly out of the frame toward the viewer, conveying a serious and focused expression, categorized as jitome[cite: 31, 34]. The top half of her face is obscured by a shadow cast by her very large, wide-brimmed black witch hat, creating a dramatic cut light effect that enhances the intense atmosphere and contributes to her shaded face[cite: 36, 37]. She is wearing a complex, multicolored outfit that includes a high-collared garment, possibly a coat or shawl, over what appears to be a white and blue dress with intricate trim, suggesting a magical or fantasy setting[cite: 31]. The clothing is obscured in parts by the surrounding special effects[cite: 38]. Her action is highly dynamic: her left arm extends dramatically out of the image plane, with her hand open and pointing towards the camera[cite: 32]. Her right hand is used to hold or adjust the brim of the large hat on her head[cite: 32]. The entire scene is enveloped in a powerful, dynamic effect of fluid dynamics and a vortex[cite: 36, 38]. Cerulean blue water, or fluid, is spiraling and swirling around her body and hand, creating a three-dimensional spiral structure that dominates the composition[cite: 38]. Scattered among the fluid are multiple sharp, glowing blue crystal petals and shards, giving the scene a magical and crystalline quality[cite: 37, 38]. The art style is defined by high resolution, best quality, and master-level detail, with noticeable artistic effects such as chromatic aberration and bokeh enhancing the sense of motion and depth[cite: 37]. The dark, abstract background further emphasizes the character and the vibrant blue light of the surrounding magical effects[cite: 36]. The lighting is highly dramatic, with a strong, artificial light source highlighting the crystalline fluids and the bottom of her face[cite: 37]. This is an illustration with an epic composition[cite: 36].
```

**UserPrompt：**
```xml
<character_1>
<n>$character_1$</n>
<gender>1girl</gender>
<appearance>blue hair, long hair, floating hair, ahoge, blue eyes, sharp pupils, fair skin, shaded face, beauty mark, Roxy Migurdia</appearance>
<clothing>witch hat, large hat, black hat, shawl, coat, white and blue dress, multicolored clothing, high collar</clothing>
<body_type>slender, small breasts</body_type>
<expression>serious, concerned, concerned eyes, intense gaze, open mouth, slight frown, jitome</expression>
<action>pointing at viewer, hand out, hand gesture, posing, head tilt, holding hat, supporting hat, dynamic pose, mid-action</action>
<interaction>pointing towards the camera</interaction>
<position>full-frame, center, foreground, tight shot, extreme close-up</position>
</character_1>
<general_tags>
<count>1girl</count>
<artists>yoneyama mai, Mika pikazo, Rolua</artists>
<style>anime style, digital art, illustration, detailed shading, cut light, fluid dynamics, cerulean gold particle effects</style>
<background>abstract, dark background, dynamic background</background>
<environment>vortex, spiral, surrounded by floating crystal petals, caustics</environment>
<perspective>dramatic angle, dutch angle, from below, tight shot, extreme close up</perspective>
<atmosphere>intense, dynamic, magical, mysterious, epic composition, shaded</atmosphere>
<lighting>cut light, shadow, strong contrast, dramatic lighting</lighting>
<quality>masterpiece, best quality, very awa, newest, highres, absurdres, an extremely delicate and beautiful, original, illustration, amazing, detailed</quality>
<objects>crystal, crystal petals</objects>
<other>fluid dynamics, spiral, three-dimensional spiral structure, chromatic aberration, bokeh, floating, special effects covered in crystals and fluids obscure a part of the body</other>
</general_tags>
```

---

## 单输入版（只有一个输入框时用）

> 不需要三件套。把质量标签 + Caption 合成一段，直接粘贴到唯一输入框。

### 结构

```
[质量标签前缀（固定）],

[完整 Caption（按10步结构写）]

[负面提示词（如果支持 negative prompt 则单独放 negative 框，不支持就加在最后）]
```

### 质量标签前缀（固定，直接抄）

```
masterpiece, best quality, very awa, newest, highres, absurdres, an extremely delicate and beautiful, original, illustration, amazing, detailed,
```

### 填空模版

```
masterpiece, best quality, very awa, newest, highres, absurdres, an extremely delicate and beautiful, original, illustration, amazing, detailed,

An extremely detailed, [动态词] digital illustration in [风格] features [角色描述], identified as $character_1$, in a [镜头类型], [镜头补充], captured with a [拍摄角度]. $Character_1$, who resembles [参考角色], is positioned to [画面位置], creating a [透视效果]. [③头发描述]. [④眼睛描述], categorized as [表情标签]. [⑤面部光影描述], creating a dramatic [光影效果名] effect that [氛围作用], contributes to her [面部状态]. She is wearing [⑥服装描述], suggesting a [世界观暗示]. The clothing is [与特效的关系]. [⑦左手动作描述]. [⑧右手动作描述]. [⑨特效描述]. [补充特效细节], giving the scene a [特效气质]. The art style is defined by [画质标签], with noticeable artistic effects such as [艺术效果] enhancing the [艺术效果的作用]. [⑩背景描述]. The lighting is [光照类型], with [光照细节]. This is an illustration with an [构图气质].
```

### 范例（参考提示词的单输入版）

```
masterpiece, best quality, very awa, newest, highres, absurdres, an extremely delicate and beautiful, original, illustration, amazing, detailed,

An extremely detailed, vibrant, and dynamic digital illustration in an anime style features a young girl, identified as $character_1$, in an extreme close-up, tight shot, captured with a dramatic Dutch angle. $Character_1$, who resembles Roxy Migurdia, is positioned to fill the entire frame in the center-foreground, creating an intense, immersive perspective. She has long, bright blue hair that appears to be floating dynamically around her head and shoulders, with a small ahoge visible on top. Her intense, concerned blue eyes with sharp pupils stare directly out of the frame toward the viewer, conveying a serious and focused expression, categorized as jitome. The top half of her face is obscured by a shadow cast by her very large, wide-brimmed black witch hat, creating a dramatic cut light effect that enhances the intense atmosphere and contributes to her shaded face. She is wearing a complex, multicolored outfit that includes a high-collared garment, possibly a coat or shawl, over what appears to be a white and blue dress with intricate trim, suggesting a magical or fantasy setting. The clothing is obscured in parts by the surrounding special effects. Her action is highly dynamic: her left arm extends dramatically out of the image plane, with her hand open and pointing towards the camera. Her right hand is used to hold or adjust the brim of the large hat on her head. The entire scene is enveloped in a powerful, dynamic effect of fluid dynamics and a vortex. Cerulean blue water, or fluid, is spiraling and swirling around her body and hand, creating a three-dimensional spiral structure that dominates the composition. Scattered among the fluid are multiple sharp, glowing blue crystal petals and shards, giving the scene a magical and crystalline quality. The art style is defined by high resolution, best quality, and master-level detail, with noticeable artistic effects such as chromatic aberration and bokeh enhancing the sense of motion and depth. The dark, abstract background further emphasizes the character and the vibrant blue light of the surrounding magical effects. The lighting is highly dramatic, with a strong, artificial light source highlighting the crystalline fluids and the bottom of her face. This is an illustration with an epic composition.
```

---

## Negative Prompt（必须写，不能省）

### 通用基础（每次都带）

```
lowres, bad anatomy, bad hands, bad fingers, text, error, missing fingers, extra digit, fewer digits, cropped, worst quality, low quality, normal quality, jpeg artifacts, signature, watermark, username, blurry, deformed, extra limbs, mutated hands, poorly drawn face, ugly, disfigured, fused fingers, too many fingers, six fingers, four fingers, malformed hands, extra fingers, claw, blurry hands
```

### 按场景追加

| 场景 | 追加负面标签 |
|------|------------|
| 需要清晰的画面（海滩/办公室/教室） | `soft focus, hazy, washed out, low contrast, muddy colors, indistinct edges, blurry background` |
| 需要服装和背景分离 | `clothing blending into background, no separation between subject and background, same color subject and background` |
| 大胸禁止 | `big breasts, large breasts, huge breasts` |
| 年幼禁止 | `young, loli, child, underage` |
| 暗场景（不要过度模糊） | `overexposed, underexposed, noisy, grainy, banding` |

---

## 已知坑点与防翻车规则

> 从实际出图踩过的坑里提炼。每条都是翻过车才加的。

### 坑1：手指变形

- **症状**：多指、少指、手指融合、爪子手
- **原因**：Caption 里没描述手指细节，模型自由发挥
- **预防**：⑦⑧步必须写 `detailed five fingers, correct hand anatomy, each finger clearly rendered`；Negative 必须带 `fused fingers, six fingers, four fingers, malformed hands, extra fingers, claw, blurry hands`

### 坑2：画面模糊/像蒙了层纱

- **症状**：整体发虚、细节糊、像低分辨率放大
- **原因**：正面写了太多 soft/bokeh/dreamy/hazy/luminous mist，负面没有防模糊标签
- **预防**：⑩收尾加 `sharp focus, crisp linework, sharp focus throughout the entire image`；需要清晰的场景**不要用 bokeh**，改用 `sharp focus, no soft diffusion`；Negative 必须带 `blurry, soft focus, hazy, washed out`

### 坑3：衣服和背景融在一起

- **症状**：白色衣服+白色沙滩=人变成一坨、深色衣服+暗背景=人消失
- **原因**：没写服装和背景的颜色对比关系
- **预防**：⑥服装必须写 `contrasting sharply with [背景颜色]` + `defined edges, clear outline, distinct from background`；⑩收尾加 `clear separation between character and background`

### 坑4：特效太强盖住角色

- **症状**：特效（火焰/水流/粒子）把角色脸和身体遮完了
- **原因**：⑨特效描述没有控制特效和角色的遮挡关系
- **预防**：⑨特效必须写 `surrounding but not obscuring the character's face` 或 `the clothing is partially obscured but the face remains clearly visible`

### 坑5：同一构图但每次出图差异大

- **症状**：换了角色描述但构图完全变了
- **原因**：Caption 里构图描述不够精确（位置、角度、镜头类型没写死）
- **预防**：①②步必须写死镜头类型和位置，不能用模糊词（"a girl standing" → "a girl filling the center of the frame in the foreground, in a medium shot, captured from a slightly low angle"）

---

## 选类型决策树

> 用户说"画一张XX"时，按下面的判断流程选择类型。从上往下匹配，命中即停。

```
用户需求
  │
  ├─ 含"角色卡/人物/外貌描写" → 问：要动漫风还是写实风？
  │    ├─ 动漫/二次元/插画 → 动漫肖像
  │    └─ 照片/写实/摄影 → 写实人像
  │
  ├─ 含"海报/封面/宣传图/主视觉" → 海报与封面
  │
  ├─ 含"发朋友圈/小红书/抖音/自拍/日常" → 社交媒体与营销
  │
  ├─ 含"漫画/分格/四格/表情包/角色卡/故事板" → 漫画与故事板
  │
  ├─ 含"信息图/教程/日历/杂志排版/教育" → 信息图与教育
  │
  ├─ 含"产品/食物/美食/电商/广告" → 产品与美食
  │
  ├─ 含"偶像/演唱会/舞台/后台/表演" → 动漫表演与舞台
  │
  ├─ 含"概念/奇幻/超现实/IP改编/幕后" → 概念艺术与奇幻
  │
  └─ 无法判断 → 问用户："你想要什么风格？动漫/写实/海报/社交媒体？"
```

**判断优先级**：关键词命中 > 风格偏好 > 场景类型。如果同时命中多个（如"动漫偶像海报"），按主要目的选——这里"海报"优先于"偶像"，选海报与封面。

---

## 人物卡→提示词转换规则

> 从 forge 的角色卡（人物/references/ 下的各种角色描述）转换为图片提示词的规则。

### 转换流程

1. **读角色卡**：从 `人物/references/research/` 或小说目录下的角色卡提取外貌/服装/性格
2. **映射到提示词结构**：按下面的对应表转换
3. **选择类型**：用决策树判断属于哪个类型
4. **套用该类型的通用写法**：读对应子文件的填空模版

### 字段映射表

| 角色卡字段 | → 提示词对应位置 | 转换要点 |
|-----------|-----------------|---------|
| 外貌描写 | ② 主体外貌 | 提取发型/发色/眼色/肤质/身高/体型，去掉文学性描写，换成视觉描述词 |
| 服装描写 | ③ 服装道具 | 逐件列出（上衣→下衣→鞋子→配饰），补充材质和颜色 |
| 表情习惯 | ② 或 ④ 表情 | 从神态描写模块取对应情绪的视觉描述（如"嫌弃"→ 神态描写/嫌弃厌恶.md） |
| 性格特征 | 氛围/情绪层 | 不直接写"傲娇"，转化为视觉行为（"下巴微翘，嘴角下撇但眼神偷瞄"） |
| 身体描写 | ② 主体外貌 | 从 设定参考/身体描写/ 取体型/肤色/体态的视觉词 |
| 职业/身份 | ③ 服装道具 | 从 设定参考/服饰穿搭/ 取职业对应的服装/配饰 |

### 注意事项

- **不要照抄角色卡原文**：角色卡是文学描写（"她笑起来像春风"），提示词需要视觉描写（"嘴角上扬，眼睛微弯，露出酒窝"）
- **神态描写模块是桥梁**：人物/references/神态描写/ 里的8种情绪描写本身就是视觉语言，可以直接转化为提示词
- **服装要具体化**：角色卡写"穿得很酷"，提示词要写"黑色oversized皮衣，银色拉链，铆钉装饰"
- **{argument}参数化**：将可替换的部分（发色、服装、场景）设为 `{argument name="..." default="..."}`，提高复用性

---

## Forge模块联动

> 提示词不是孤立生成的——forge 的其他模块提供了大量可直接使用的视觉素材。

### 可联动的模块

| Forge模块 | 路径 | 喂给提示词的哪个部分 |
|-----------|------|---------------------|
| 神态描写（8种情绪） | `人物/references/神态描写/` | ② 主体外貌 → 表情/情绪 |
| 身体描写参考 | `设定参考/身体描写/身体描写参考.md` | ② 主体外貌 → 体型/肤色/面部特征 |
| 服饰穿搭（10个部位） | `设定参考/服饰穿搭/` | ③ 服装道具 → 按部位查找具体单品 |
| 配饰速查 | `设定参考/服饰穿搭/配饰/配饰速查.md` | ③ 服装道具 → 首饰/包/手表/穿孔 |
| 世界观模板 | `设定参考/世界观/` | ⑤ 背景环境 → 场景风格/建筑/科技水平 |
| 各国拟实 | `设定参考/各国家拟实/` | ⑤ 背景环境 → 真实国家的城市/街道/文化细节 |
| 武器速查 | `设定参考/武器/` | ③ 服装道具 → 角色手持武器/装备 |

### 联动示例

**输入**："画一个嫌弃表情的职场女性"

1. 读 `人物/references/神态描写/嫌弃厌恶.md` → 取"鼻翼微皱，上唇微掀，下巴微翘" → 转化为提示词表情描述
2. 读 `设定参考/服饰穿搭/上衣/` → 取"西装=职场/气场/权力" → 转化为服装描述
3. 读 `设定参考/身体描写/` → 取"高挑型：腿长、肩平、姿态挺拔" → 转化为体型描述
4. 套用 `写实人像.md` 的通用写法填空模版

---

## 使用流程

### 第0步：问用户（必须先问，用 AskUserQuestion 一次问完）

同时问三个问题：

| 问题 | 选项 |
|------|------|
| 输入格式 | 双路输入 / 单输入 / 两个都要 |
| 语言 | 中文 / 英文 / 两个都要 |
| 是否要负面提示词 | 要 / 不要 |

根据回答决定输出哪些版本：

| 输入格式 × 语言 | 输出 |
|----------------|------|
| 双路 + 英文 | UserPrompt XML + Caption（英文） |
| 双路 + 中文 | UserPrompt XML + Caption（中文） |
| 单输入 + 英文 | 质量标签前缀 + Caption 合成一段（英文） |
| 单输入 + 中文 | 质量标签前缀 + Caption 合成一段（中文） |
| 两个都要 × 两个都要 | 四个版本全出 |

### 三件套版（ComfyUI 有 tags + caption 双路输入）

1. **先问用户**（第0步）
2. 确定角色（外貌/服装/动作/表情）
3. 确定场景（背景/环境/光照/特效）
4. 按10步结构填写 Caption（最关键，必须完整自洽）
5. 从 Caption 提取标签填入 UserPrompt XML
6. Prompt Template 不动
7. 按用户要求的语言输出

### 单输入版（只有一个输入框）

1. **先问用户**（第0步）
2. 确定角色 + 场景
3. 把质量标签前缀 + 按10步结构写完整 Caption 合成一段
4. 直接粘贴到唯一输入框
5. Negative 单独放 negative 框（没有就加在最后）
6. 按用户要求的语言输出

**铁律：Caption 写不好，标签再多也没用。Caption 是骨架，标签是肌肉。只有一个输入口时，骨架比肌肉重要。**
