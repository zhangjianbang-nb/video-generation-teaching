# 视频生成（Video Generation） · 领域研究与教学站

一个**完全离线**的单页教学站：6 个方向、31 篇论文、33 个算法、15 个理论专题、4 个故事、41 道题，正文约 **323 万可见字符**（158 页、106 幅内联 SVG、965 张表）。

- 在线访问：<https://zhangjianbang-nb.github.io/video-generation-teaching/>
- 独立故事书：<https://zhangjianbang-nb.github.io/video-generation-teaching/story/index.html>（约 96.9 万可见字符 / 51 万汉字）
- 本地阅读：双击 `index.html` 即可（file:// 直接可用）
- 零外部依赖：KaTeX 0.16.9 内置在 `vendor/katex/`，不访问任何 CDN，不依赖登录服务

## 内容

| 模块 | 规模 |
|---|---|
| 研究方向 | 6 个：架构 / 长视频 / 控制 / 编辑 / 效率 / 评测 |
| 论文 | 31 篇（3 foundational + 10 classic + 14 recent + 4 latest，31/31 全文精读） |
| 算法 | 33 个（每个含「解决什么问题 / 机制 / 代价」三件套） |
| 理论 | 15 个专题（先修 DAG 两个根：diffusion、FVD） |
| 故事 | 4 篇；旗舰《一粒噪声的还乡记》30,835 字、16 处「类比失效点」 |
| 题库 | 41 道（L1–L5，含判分点、常见错误、评分标准） |
| 演进图 | 27 节点 / 20 边，5 种关系（inherit / improve / replace / extend / parallel） |

## 核心判断

- 六条支线不是并列，是依赖链：**地基（架构）→ 能力（长视频）→ 接口（控制/编辑）→ 成本（效率）→ 裁判（评测）**。
- 三次范式转移：像素 → 潜空间（2023，Video LDM）、U-Net → DiT（2024，CogVideoX）、单段 → 长视频/流式（2024–25）。
- 读数字的纪律：FVD 差 <50 人类几乎分不出（FVD 论文自述）；VBench Overall Consistency 的 Empirical Max 只有 36.40%。
- 选型三问：多长（4–10s 用 CogVideoX/Wan；分钟级用 SkyReels/FramePack）、多快（实时 LTX-Video）、要不要控制（相机 CameraCtrl / 轨迹 MotionCtrl / 编辑 TokenFlow·RAVE 免训练）。

## 页面结构

```
.
├── index.html            # 单页应用（哈希路由）
├── data/
│   ├── bundle.js         # 前端一次性加载的数据包（由 *.json 打包生成）
│   ├── papers.json       # 31 篇论文
│   ├── algorithms.json   # 33 个算法
│   ├── theory.json       # 15 个理论专题
│   ├── stories.json      # 4 个故事
│   ├── assessments.json  # 41 道题
│   ├── directions.json   # 6 个方向
│   ├── evolution.json    # 演进图（SVG 自动布局）
│   └── …                 # book / appendix / summary / coverage / domain
├── vendor/katex/         # KaTeX 0.16.9（本地）
├── story/index.html      # 独立故事书《一秒的诞生 · 一家制片厂的十年》
└── DEPENDENCIES.md       # 依赖说明
```

## 路由

`#/home` `#/map` `#/algos` `#/papers` `#/evolution` `#/summary` `#/book` `#/story` `#/theory` `#/deepdive` `#/appendix` `#/exam`

方向详情 = `#/map/<id>`；domain 长文渲染在 `#/home` 末尾；coverage 长文渲染在 `#/summary` 末尾。

## 验收记录（2026-11-12 终态）

- `verify_site.py --profile L2 --phase all`：0 errors / 0 warnings PASS
- 端到端 `e2e_site.js`：21/21（27 节点 / 20 边 / 并行边虚线 / overlap=0 / 移动端 overflow=0）
- 演进图几何断言：20 条边 ×120 点采样，`hits=[]`（不穿任何节点框）
- 字数口径：ledger **3,234,804 可见字符 / 107.83%**（目标 300 万）
- 三轮四维校验：78.8 → 83.25 → **85.5 PASS**

## 诚实边界

- Google Scholar / Semantic Scholar / OpenAlex / DBLP 检索受限的情况如实写进 `coverage.json`，未包装成「全面检索」。
- YouTube 渠道未执行；教学叙事为原创机制叙事，不声称引用视频作者观点。
- 所有实验数字为论文自报，未复现；商用闭源（Sora/Kling/Gen-3）无公开论文，未进核心库。

## 许可

文字与图示内容采用 [CC BY 4.0](LICENSE)。论文版权归各原作者所有；本站只收录笔记、解读与教学材料，不收录论文原文 PDF。
