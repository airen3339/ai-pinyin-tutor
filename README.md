<!--
  用途：GitHub 仓库发布/宣传页（README 风格）。
  发布方式：把本文件内容复制为仓库根目录的 README.md 即可被 GitHub 渲染为项目首页；
  也可直接作为项目的对外介绍文档使用。所在位置：ai-pinyin-tutor/docs/。
-->

<div align="center">

# 🐼 AI 汉语拼音学习助手

**AI Chinese Pinyin Tutor · ai-pinyin-tutor**

*看到拼音 → 听标准音 → 看口型与声调曲线 → 跟读录音 → AI 评分 → 定位错误 → 针对性训练*

一套面向 **儿童启蒙 / 成人外国人 / 教育机构** 的汉语拼音学习与**可解释发音评测**系统。

[![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.110%2B-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Vue](https://img.shields.io/badge/Vue-3-4FC08D?logo=vuedotjs&logoColor=white)](https://vuejs.org/)
[![Vite](https://img.shields.io/badge/Vite-4-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![Element Plus](https://img.shields.io/badge/Element%20Plus-2-409EFF?logo=element&logoColor=white)](https://element-plus.org/)
[![Database](https://img.shields.io/badge/DB-SQLite%20%7C%20PostgreSQL%2015-4169E1?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![MiniProgram](https://img.shields.io/badge/WeChat-MiniProgram-07C160?logo=wechat&logoColor=white)]()
[![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)](https://docs.docker.com/compose/)

[![Tests](https://img.shields.io/badge/tests-55%20passed-success?logo=pytest&logoColor=white)]()
[![Smoke](https://img.shields.io/badge/e2e-50%20steps%20passed-success)]()
[![AUC](https://img.shields.io/badge/scoring%20AUC-0.793-blue)]()
[![Latency](https://img.shields.io/badge/latency-P95%2015ms-blue)]()
[![License](https://img.shields.io/badge/license-TBD-lightgrey)]()

**[功能说明](功能说明.md)** · **[搭建文档](搭建文档.md)** · **[进度台账](可行实施计划与进度跟踪_V1.0.md)**

</div>

---

## 📖 目录

- [为什么做这个项目](#-为什么做这个项目)
- [核心特性](#-核心特性)
- [技术亮点：声调是怎么被判出来的](#-技术亮点声调是怎么被判出来的)
- [系统架构](#-系统架构)
- [快速开始](#-快速开始)
- [目录结构](#-目录结构)
- [技术栈](#-技术栈)
- [数据资产](#-数据资产)
- [API 一览](#-api-一览)
- [质量证据](#-质量证据)
- [运行模式](#-运行模式)
- [路线图](#-路线图)
- [文档索引](#-文档索引)
- [贡献指南](#-贡献指南)
- [License](#-license)

---

## 💡 为什么做这个项目

市面上的拼音学习 App，大多止步于"**给一个分数**"：

> 点喇叭 → 孩子跟读 → 弹出 "85 分" → **然后呢？**

85 分错在哪里？声母？韵母？还是声调？下次怎么改？——**没有人告诉你。**

`ai-pinyin-tutor` 要解决的就是最后这一公里：**把"跟读"变成"知道错在哪、为什么错、怎么改"的闭环。**

- ✅ 分数拆成 **4 个维度**（声母 / 韵母 / 声调 / 流畅度），不是一个笼统的总分；
- ✅ 不只说"错了"，而是给出**错误类型**（如 `zh → z 混淆`、`声调被判为阳平`）；
- ✅ 成因与纠正话术来自**规则化教学知识库**，模型只做检测、不编故事；
- ✅ 根据历史错误推荐**针对性训练词**与 **7 天学习计划**。

---

## ✨ 核心特性

<table>
<tr>
<td width="50%" valign="top">

**🎧 学习闭环**

- 拼音表 / 音节详情 / 声调学习
- 汉字 → 词语 → 例句 + 配图 + 笔顺
- 标准音播放 / 慢速 / 分解播放
- 用户与标准**声调曲线叠加对比**

</td>
<td width="50%" valign="top">

**🤖 可解释发音评测**

- 加权评分引擎（权重单一来源）
- 五度标记法声调判决
- 音素级 GOP、错误诊断引擎
- 母语负迁移规则（日 / 韩 / 英…）

</td>
</tr>
<tr>
<td width="50%" valign="top">

**🧑‍🏫 AI 中文老师**

- 4 个儿童童趣角色 + 3 种成人模式
- 意图路由：讲解 / 纠音 / 闲聊 / 规划
- 7 天个性化学习路径
- 关闭时零网络请求（确定性话术兜底）

</td>
<td width="50%" valign="top">

**👨‍👩‍👧 多角色平台**

- 教师后台：班级 / 学生 / CSV 报告
- 家长端：学习天数 / 薄弱项 / 建议
- 儿童游戏化：星星 / 熊猫币 / 徽章 / 地图
- 多角色权限隔离（成人·儿童·教师·家长·管理）

</td>
</tr>
<tr>
<td width="50%" valign="top">

**🌏 多端覆盖**

- Web 学习平台（Vue 3，12 视图）
- 微信小程序（免安装快体验）
- Flutter APP（规划中，见文档）
- i18n：中 / 英 / 日 / 韩

</td>
<td width="50%" valign="top">

**⚙️ 工程严谨**

- 一套代码三种运行模式（桩 / 开发 / 生产）
- 降级不失败，绝不返回假数据
- 开源许可红线（GPL 隔离）
- Docker Compose 一键部署 + 监控告警

</td>
</tr>
</table>

---

## 🔬 技术亮点：声调是怎么被判出来的

这是整个项目最有意思的部分，也是踩坑最多的地方。

### 问题：阳平(35) 与 上声(214) 天然难分

最初我们用最直观的 **L1 距离**——把用户 F0 轮廓和参考轮廓做距离比对，谁近算谁。

结果：**阳平/上声混淆率高达 62%**。原因是两者的音高轮廓**都表现为"先低后高"**，形状距离天生分不开。

### 解法：用五度标记法的可解释特征

| 特征 | 含义 | 区分能力 |
|---|---|---|
| `span` | 音高跨度（半音） | 一声最平 |
| `slope` | 整体斜率 | 二声上滑 / 四声下滑 |
| `p_min` / `p_max` | **谷底 / 峰值位置** | 四声谷底靠后 |
| `start_drop` | **起音相对谷底的落差** | **区分阳平 / 上声的关键** |

判决顺序（**上声优先**）：`平 → 去 → 上(start_drop 大) → 阳 → 上 → 去 → 平`

> **核心洞察**：阳平"起点即谷底"（`start_drop ≈ 0`）；上声"先降再升"（`start_drop` 大）。

**成效**：声调自分类 **62% → 78.8%**，规范四声参考曲线 **4/4 自洽**。

> ⚠️ **踩过的坑**：`slope` / `p_min` 必须算在**原始半音轮廓**上，而非归一化 0–1 轮廓。
> 混用会导致网格搜索 81.7%、上线后仅 60.9%（阈值永不触发）。
>
> 全部阈值、网格搜索脚本与日志保留在 [`eval/tuning/`](../eval/tuning/)，**结论可复现**。

评分权重：**声母 25% · 韵母 25% · 声调 35% · 流畅度 15%**（唯一来源 `config.settings.scoring`，业务代码零硬编码）。

---

## 🏗 系统架构

```
                          ┌─────────────────────────────────────────┐
                          │              客户端（多端）               │
                          │  Web 学习平台(Vue3)  小程序   Flutter APP │
                          │   浏览/学习/报告     快体验   录音+评分    │
                          └───────────────┬─────────────────────────┘
                                          │ HTTP /api/*（统一信封）
                                          ▼
┌───────────────────────────────────────────────────────────────────────────┐
│  backend/  · FastAPI                                                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌───────────────┐  │
│  │  api/  接口层 │  │ services/ 业务│  │  core/ 基础   │  │  db/ ORM 层   │  │
│  │ content tts  │  │ content 课程  │  │ 配置 日志     │  │  14 张表      │  │
│  │ search auth  │  │ 账号 记录     │  │ 统一响应 错误 │  │  SQLite/PG    │  │
│  │ practice     │  │ 练习 导师     │  │ 配额 安全     │  │               │  │
│  │ course users │  │ 存储 游戏     │  │              │  │               │  │
│  │ teacher      │  │              │  │              │  │               │  │
│  │ parent game  │  │              │  │              │  │               │  │
│  └──────┬───────┘  └──────┬───────┘  └──────────────┘  └───────────────┘  │
└─────────┼─────────────────┼───────────────────────────────────────────────┘
          │                 ▼
          │   ┌──────────────────────────────────────────────────────────┐
          │   │  speech/  · 语音与评测引擎（与 Web 框架解耦，可独立调用）   │
          │   │  audioproc  f0  tone  scoring  asr  align  phoneme  tts   │
          │   │  llm(Teacher/PathPlanner)   pipeline   tasks(队列)         │
          │   │  feedback/{diagnose, error_db.json, l1_rules.json}        │
          │   └──────────────────────────────────────────────────────────┘
          ▼
┌───────────────────────────────────────────────────────────────────────────┐
│  data/  · 数据资产（离线构建，产物入库；构建脚本可复现）                      │
│  pinyin_table(音节表) lexicon(字/词) audio(标准音) images(配图)             │
│  stroke(笔顺) courses(444 课) scripts(校验)                                 │
└───────────────────────────────────────────────────────────────────────────┘
          +
  eval/    评测基准 + 调参工作台 + 性能压测
  deploy/  Dockerfile / nginx / Prometheus / Grafana / 告警
```

---

## 🚀 快速开始

### 方式一：桩模式（3 分钟，CPU 即可，无需 GPU / 联网）

```bash
git clone <仓库地址> && cd ai-pinyin-tutor
python -m venv .venv && . .venv/Scripts/activate     # Windows
# source .venv/bin/activate                          # macOS / Linux
pip install -r requirements.txt

python -m uvicorn backend.app.main:app --reload      # 启动后端
# 浏览器打开 http://127.0.0.1:8000/docs （Swagger 文档）
```

### 方式二：构建数据资产 + Web 前端

```bash
python scripts/check_env.py                          # 环境自检
python data/pinyin_table/build.py                    # 拼音音节表（410）
python data/lexicon/build.py                         # 字音 / 词库
python data/scripts/validate_data.py                 # 数据完整性校验
python data/audio/build.py --voice zh-CN-XiaoxiaoNeural   # 标准音（需联网）

cd frontend && npm install && npm run dev            # Web 学习平台
```

### 方式三：Docker Compose 一键部署

```bash
docker compose up -d
# 后端 :8000 · Web :8080 · Prometheus :9090 · Grafana :3000
```

> 详细步骤、验证清单与 FAQ 见 **[搭建文档.md](搭建文档.md)**。

### 运行测试

```bash
# 单元测试（离线、无副作用）
CODEBUDDY_SAFE_DELETE_ENABLED=0 APT_TTS_PROVIDER=none python -m pytest -q

# 端到端冒烟（50 步全链路）
python scripts/smoke_e2e.py

# 评分评测 / 性能压测
python eval/run_scoring_eval.py && python eval/perf_test.py
```

---

## 📂 目录结构

```
ai-pinyin-tutor/
├── app/            Flutter 应用（Android/iOS/平板）
├── frontend/       Web 学习平台 + 教师/家长后台（Vue3）
├── miniprogram/    微信小程序
├── backend/        FastAPI 业务后端
├── speech/         AI 语音服务（ASR / 对齐 / 评测 / TTS / LLM）
├── data/           数据构建与产物（音节表 / 字音 / 词库 / 配图 / 音频）
├── eval/           评测基准集与评测脚本 + 调参工作台
├── deploy/         Docker / Compose / Nginx / 监控
├── docs/           设计文档 / ADR / 许可清单 / 验收报告 / 传播文案
└── scripts/        运维与校验脚本
```

---

## 🛠 技术栈

| 层 | 技术 |
|---|---|
| **后端** | Python 3.11+ · FastAPI · SQLAlchemy 2 · Pydantic 2 · Uvicorn |
| **语音** | pyworld（F0，MIT） · FunASR（主 ASR） · Whisper（兜底） · edge-tts |
| **前端** | Vue 3 · Vite · Element Plus · Pinia · vue-router |
| **小程序** | 微信原生小程序 |
| **数据库** | SQLite（开发） / PostgreSQL 15（生产） |
| **存储 / 缓存** | MinIO（对象存储） · Redis（可选） |
| **部署** | Docker · Docker Compose · Nginx · Prometheus · Grafana |
| **质量** | pytest · 自研评测基准 · 性能压测 |

> **许可红线**：GPL 组件（Praat / parselmouth）不得与商业服务同进程链接；
> 主链路 F0 换用 MIT 许可的 `pyworld`；无 LICENSE 的语料仅离线对照。
> 详见 [开源许可与合规清单.md](开源许可与合规清单.md)。

---

## 📊 数据资产

| 资产 | 规模 | 达标 |
|---|---|---|
| 拼音音节表 | **410 音节**（23 声母 / 24 韵母 / 16 整体认读 / 5 声调） | ✅ |
| 汉字库 | **3500 字**（含多音候选、笔顺引用） | ✅ |
| 分级词库 | **5371 词**（启蒙 / 一级…/ HSK1–6） | ✅ |
| 课程体系 | **444 课**（L1 100 · L2 100 · L3 64 · L4 180） | ✅ |
| 标准音音频 | **1517 条**（含男声学习单元 + 慢速版） | ✅ **96.1%** 音节覆盖 |
| 汉字笔顺 | 3500 字 | ✅ |
| 词条配图 | 241 张（OpenMoji 可商用） | 🟡 目标 ≥1500 |

---

## 🔌 API 一览

统一响应信封（字段 camelCase，带 `X-Trace-Id` / `X-Cost-Ms`）：

```json
{ "code": 0, "message": "ok", "data": { }, "traceId": "a1b2c3d4e5f6a7b8" }
```

| 分组 | 接口数 | 鉴权 | 示例 |
|---|---|---|---|
| 内容 | 8 | 否 | `/api/pinyin/list`、`/api/word/detail` |
| 音频播放 | 5 | 否 | `/api/tts/play`、`/api/tts/variants` |
| 检索 | 1 | 否 | `/api/search`（拼音/汉字双模） |
| 账号 | 3 | 部分 | `/api/auth/register`、`/api/auth/login` |
| 练习闭环 | 7 | 是 | `/api/practice/submit`、`/api/practice/weakness` |
| 课程 / AI 教师 | 6 | 部分 | `/api/course/list`、`/api/tutor/chat` |
| 教师后台 | 7 | 教师 | `/api/teacher/class/report.csv` |
| 家长端 | 2 | 家长 | `/api/parent/report` |
| 游戏化 | 1 | 是 | `/api/game/state` |
| 健康 / 指标 | 3 | 否 | `/health`、`/metrics`（Prometheus） |

启动后访问 `/docs`（Swagger）或 `/redoc` 查看在线文档。

---

## ✅ 质量证据

| 项 | 结果 |
|---|---|
| 单元测试 | **55 项全绿** |
| 端到端冒烟 | **50 步全通过**（探活 → 浏览 → 播放 → 检索 → 练习闭环 → 教师 → 游戏化 → 家长 → 负向用例） |
| 评分区分度 | **AUC 0.793**（仅自洽参考音） |
| 延迟 | **P95 = 15 ms**（目标 ≤2500 ms） |
| 前端构建 | ✓ 通过（1700 模块） |

> 评测报告：[../eval/report_scoring.md](../eval/report_scoring.md) · [../eval/report_perf.md](../eval/report_perf.md) · [端到端冒烟报告.md](端到端冒烟报告.md)

---

## 🔀 运行模式

同一套代码，靠环境变量切成三种形态：

| 维度 | ① 桩模式（CI / 无 GPU） | ② 开发模式 | ③ 生产模式 |
|---|---|---|---|
| `APT_ASR_PROVIDER` | `dummy` | `dummy` / `whisper` | `funasr` |
| `APT_TTS_PROVIDER` | `none` | `edge` | `cloud` |
| `APT_LLM_ENABLED` | `0` | `0` / `1` | `1` |
| `APT_DATABASE_URL` | 临时 SQLite | `var/app.db` | PostgreSQL 15 |
| 声母 / 韵母评分 | ❌ | ❌ | ✅ |
| 声调 + 流畅度 | ✅ | ✅ | ✅ |

> **降级不失败**：任一通道异常，系统切到降级通道并置 `degraded=True`，
> 在结果里**明确告知用户"本次不评测声母/韵母"**，而非伪造分数。

---

## 🗺 路线图

- [x] **P0** 前置准备 —— 架构 / 许可 / 骨架 / CI / ADR
- [x] **P1** 基础版 —— 数据层 + 后端 + TTS + 声调曲线
- [x] **P2** AI 语音练习版 —— 评分闭环 + 错误诊断
- [x] **P3** AI 中文老师版 —— 教师 / 课程 / 后台 / 小程序 / 部署监控
- [ ] **P4** 商业化 —— 订阅支付 / B 端机构 / 海外本地化 / 智能硬件
- [ ] 音素级 GOP 接入（需 GPU + FunASR）
- [ ] 评分-专家分相关性评测（需人工双盲标注）
- [ ] Flutter APP 端落地（需 Flutter SDK）
- [ ] 词条配图扩充至 ≥1500 张

> 完整 74 项任务台账与 Gate 状态见 **[进度跟踪文档](可行实施计划与进度跟踪_V1.0.md)**。

---

## 📚 文档索引

| 文档 | 内容 |
|---|---|
| [功能说明.md](功能说明.md) | 项目定位 / 架构 / 功能清单 / 环境变量 / API / 表结构 / 缺口 |
| [搭建文档.md](搭建文档.md) | 三种从零搭建路线 / 验证清单 / FAQ |
| [可行实施计划与进度跟踪_V1.0.md](可行实施计划与进度跟踪_V1.0.md) | 74 项任务台账与 Gate 状态 |
| [宣传文档.md](宣传文档.md) | 面向公众号等平台的推广文章 |
| [需求基线_V1.0.md](需求基线_V1.0.md) | 用户画像与"不做"清单 |
| [开源许可与合规清单.md](开源许可与合规清单.md) | 组件 / 模型 / 数据集许可与风险 |
| [数据来源与许可说明.md](数据来源与许可说明.md) | 每类数据来源可追溯 |
| [部署手册.md](部署手册.md) | Compose 一键部署与运维 |
| [角色话术设计.md](角色话术设计.md) | AI 教师人设与话术 |
| [adr/](adr/) | 评测路线 / 对齐 / TTS / F0 与许可隔离 |
| [P1_验收.md](P1_验收.md) · [P2](P2_验收.md) · [P3](P3_验收.md) | 分阶段验收（含未达标项，诚实标注） |

---

## 🤝 贡献指南

欢迎 Issue 与 PR。提交前请确保：

1. `python -m pytest -q` 全绿（**不允许弄红**）；
2. `python scripts/smoke_e2e.py` 全链路通过；
3. 新增接口遵循统一信封与 camelCase 别名规范，并补充对应单测；
4. 新增第三方依赖前，先在 [开源许可与合规清单.md](开源许可与合规清单.md) 登记许可与风险等级；
5. 改动重大设计时，同步更新 `功能说明.md` 与对应 ADR。

> ⚠️ 注意历史约定：`/teacher/*` 接口查询参数用 **snake_case**（`class_id` / `student_id`），
> 其余多为 camelCase。新增接口前请先阅读现有代码。

详见 [../CONTRIBUTING.md](../CONTRIBUTING.md)。

---

## 📄 License

本工程自身许可证**尚未选定**（建议采用 MIT 或 Apache-2.0，待项目维护者确认后补充 `LICENSE` 文件）。
第三方组件、模型与数据集的许可情况见 [开源许可与合规清单.md](开源许可与合规清单.md)。

---

<div align="center">

**如果这个项目对你有帮助，欢迎点一个 ⭐ Star 支持我们！**

*让机器不仅听懂声调，更能讲清错在哪。*

</div>

---

## 🏢 关于我们

<p align="center">
  <a href="http://www.net188.net">
    <img src="http://www.net188.net/images/logo1.png" alt="Net188 Logo" width="200" />
  </a>
</p>

<p align="center">
  <strong>Net188 · 互联网技术服务</strong>
</p>

<p align="center">
  专注于跨平台应用开发、AI Agent 集成与大模型应用落地。<br/>
  提供从产品设计、开发实施到部署运维的全栈技术解决方案。
</p>

<p align="center">
  🌐 <a href="http://www.net188.net"><strong>www.net188.net</strong></a>
</p>

---
