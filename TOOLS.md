# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## 论文写作辅助规范

### 语言风格

- **默认输出**：中文解释 + 英文修改建议
- **修改格式**：表格对比 "原句 | 修改后 | 说明"
- **术语偏好**：美式英语，符合 ACS/RSC/Wiley 期刊规范
- **时态规则**：
  - Abstract：现在时（背景）+ 过去时（本文工作）
  - Introduction：现在时（背景/文献）+ 现在完成时（研究现状）
  - Methods：过去时
  - Results：过去时（观察）+ 现在时（普遍真理）
  - Discussion：现在时（解释）+ 过去时（本文发现）

### 课题组高频表达库

#### 光催化方向

- charge separation / electron–hole separation / e–h separation
- photocatalytic hydrogen evolution / water splitting / CO2 reduction
- interfacial charge transfer / interfacial electron transfer / hole transfer
- visible-light driven / under visible-light irradiation
- Schottky junction / p–n heterojunction / semiconductor–metal hybrid
- co-catalyst / sacrificial agent / hole scavenger / cocatalyst
- photocatalytic activity / efficiency / performance

#### 超快光谱方向

- femtosecond transient absorption (fs-TA) spectroscopy
- pump–probe / white-light continuum (WLC) probe
- excited-state absorption (ESA) / ground-state bleaching (GSB) / stimulated emission (SE)
- ultrafast dynamics / charge carrier dynamics / exciton dynamics
- reverse hole transfer (RHT) / reverse intersystem crossing (RISC)
- time-resolved / time-correlated single photon counting (TCSPC)
- transient absorption spectra / kinetic traces / decay dynamics

#### 荧光/量子点方向

- photoluminescence (PL) / photoluminescence quantum yield (PLQY)
- thermal quenching / fluorescence quenching / Auger recombination
- singlet fission / singlet oxygen / triplet states
- quantum confinement / exciton binding energy / hot carrier
- perovskite nanocrystals / quantum dots / carbon dots / upconversion
- luminescence intensity / emission spectrum / radiative recombination

#### 材料合成方向

- metal–organic framework (MOF) / UiO-66 / ZIF-8 / MOF-derived
- single-atom catalysts / doped nanocrystals / heterostructure
- oxygen vacancy / structural defects / surface states / trap states
- one-unit-cell layers / atomically thin / ultrathin nanosheets
- core–shell structure / heterojunction interface / surface modification
- solvothermal / hydrothermal / chemical vapor deposition

### 语言功能词速查

#### 连接与过渡 (Transitions)

while(283), however(282), moreover(177), hence(162), therefore(130), notably(102), thereby(95)

#### 强调与评价 (Emphasis)

key(225), highly(217), strong(182), mainly(135), greatly(96)

#### 描述与刻画 (Description)

new(261), achieved(94)

#### 动作与过程 (Actions)

enhanced(268), indicating(204), show(188), exhibit(172), revealed(171), exhibits(149), reported(146), exhibited(145), following(138), demonstrated(137), improved(136), showed(133), indicates(122), supported(119), indicated(117), including(114), related(114), associated(109), suggesting(99), provide(97), demonstrate(96)

#### 对比与比较 (Comparison)

corresponding(384), different(272), higher(263), similar(258), compared(207), same(196), comparison(183), lower(154), relative(129), larger(111)

#### 因果与推理 (Causality)

due(323), given(227), because(194), resulting(111), attributed(110), means(100)

#### 限定与模糊 (Hedging)

nearly(139), rather(118), relatively(108)

### 写作模板

#### Abstract

```
[背景] Recently, ... has attracted considerable attention as a promising ... for ... applications.
[问题] However, ... remains poorly understood / limited / challenging, hindering further development.
[方法] Herein, we report/present/demonstrate ... by using / via / through ...
[发现] The results show/indicate/reveal that ... exhibits/enables/demonstrates ...
[意义] This work provides deep insights into ... / offers a new strategy for ... / paves the way for ...
```

#### Introduction 段落组织

```
Para 1 [大背景]: ... has emerged as a promising candidate for ... owing to its unique ...
Para 2 [研究现状]: Numerous studies have focused on ... / Considerable efforts have been devoted to ...
Para 3 [存在问题]: Despite these advances, ... remains unclear / poorly understood / challenging.
Para 4 [本文工作]: Herein, we present ... / To address this issue, we design / In this work, we aim to ...
```

#### Methods

```
材料合成: ... was synthesized/prepared/fabricated via/by a ... method / according to a previously reported procedure with minor modifications.
表征手段: ... was characterized by ... / ... measurements were performed using ... / The ... spectra were recorded on a ... instrument.
测试条件: The ... experiments were conducted under ... conditions / at room temperature / in a ... atmosphere.
```

#### Results & Discussion

```
描述现象: As shown in Figure X, ... exhibits/displays/shows/reveals a pronounced/significant ...
解释机理: The ... can be attributed to / is ascribed to / arises from ... / This behavior originates from ...
对比讨论: Compared with ..., ... demonstrates/enables ... / In contrast to ..., ... shows ...
强调意义: These results suggest/indicate that ... plays a crucial/significant/key/pivotal role in ...
定量描述: The ... is enhanced/improved by approximately / roughly / about X-fold / X% relative to ...
```

#### Conclusion

```
总结: In summary/conclusion, we have demonstrated that ... / Taken together, our results reveal that ...
展望: This work opens up new possibilities for ... / Future work will focus on ... / These findings pave the way for ...
```

# 
---

## 消息发送工具

### message（发消息/跨通道通信）

当 main 协调者通过 sessions_send 给你下发任务，需要你往群里发消息时使用此工具。

- **用途**：主动给某个群发消息
- **⚠️ 必须参数（三个缺一不可）**：
  - `action`: **必需！** 固定填 `"send"`
  - `channel`: **必需！** 填 `"onebot"`
  - `to`: 你的默认群 → `"onebot:group:1097473921"` （那个群）
  - `message`: 要发送的内容
- **完整格式**：`action: "send", channel: "onebot", to: "onebot:group:1097473921", message: "你的消息内容"`

正确示例：
```
action: "send", channel: "onebot", to: "onebot:group:1097473921", message: "组里有人试过MOF限域单原子吗？"
```

❌ 常见错误（会导致 Validation failed）：
- 缺 action：`channel: "onebot", to: "...", message: "..."` ← 必须加 action: "send"
- 缺 channel：`action: "send", to: "...", message: "..."` ← 多通道时必须指定
- 参数名错误：用 `text` 而不是 `message`

### 群聊配置备忘

| 群 | 群号 | 用途 |
|----|------|------|
| 那个群 | 1097473921 | **你的默认群**，收到"在你所在的群发消息"指令时用这个 |

---

## 网络搜索与抓取（curl / ddgs）

### 方式1：curl 命令行

```bash
# DuckDuckGo 搜索
curl --proxy http://192.168.1.2:28002 -s -A "Mozilla/5.0" "https://html.duckduckgo.com/html/?q=关键词"

# Bing 搜索
curl --proxy http://192.168.1.2:28002 -s "https://cn.bing.com/search?q=关键词"

# 抓取任意网页
curl --proxy http://192.168.1.2:28002 -sL "https://example.com" | head -100

# 抓取维基百科
curl --proxy http://192.168.1.2:28002 -sL "https://zh.wikipedia.org/wiki/关键词"
```

### 方式2：ddgs 工具
- 直接调用 `ddgs` 工具进行DuckDuckGo搜索

---

Add whatever helps you do your job. This is your cheat sheet.
