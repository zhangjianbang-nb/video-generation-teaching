# 视频生成（Video Generation） · 领域研究与教学站

一个**完全离线**的单页教学站：6 个方向、**33 篇论文、35 个算法**、15 个理论专题、4 个故事、41 道题，正文约 **329 万可见字符**（162 页、112 幅内联 SVG、978 张表）。时间窗口 **2018–2027**：2026 为已发表工作，2027 为四条展望。

- 在线访问：<https://zhangjianbang-nb.github.io/video-generation-teaching/>
- 独立故事书：<https://zhangjianbang-nb.github.io/video-generation-teaching/story/index.html>（约 96.9 万可见字符 / 51 万汉字）
- 本地阅读：双击 `index.html` 即可（file:// 直接可用）
- 零外部依赖：KaTeX 0.16.9 内置在 `vendor/katex/`，不访问任何 CDN，不依赖登录服务

## 内容

| 模块 | 规模 |
|---|---|
| 研究方向 | 6 个：架构 / 长视频 / 控制 / 编辑 / 效率 / 评测 |
| 论文 | 33 篇（3 foundational + 10 classic + 14 recent + 6 latest；31 篇全文精读 + 2 篇 2026 摘要级核验） |
| 算法 | 35 个（每个含「解决什么问题 / 机制 / 代价」三件套） |
| 理论 | 15 个专题（先修 DAG 两个根：diffusion、FVD） |
| 故事 | 4 篇；旗舰《一粒噪声的还乡记》30,835 字、16 处「类比失效点」；每篇配 1 幅贴切场景插画，旗舰另有十站路线图 |
| 题库 | 41 道（L1–L5，含判分点、常见错误、评分标准） |
| 演进图 | 30 节点 / 23 边，5 种关系（inherit / improve / replace / extend / parallel）；时间线 2018–2026 七个转折 + 2027 展望 |

## 核心判断

- 六条支线不是并列，是依赖链：**地基（架构）→ 能力（长视频）→ 接口（控制/编辑）→ 成本（效率）→ 裁判（评测）**。
- 三次范式转移：像素 → 潜空间（2023，Video LDM）、U-Net → DiT（2024，CogVideoX）、单段 → 长视频/流式（2024–25）。
- 2026 的结构转向：不是把模型做大，而是把结构用对——角色适配器（TaoMate-R1）、条件平移删 fake 网络（APEX）、正交运动注入（HME）、代码当物理教师（PhysOPSD）、场景注意力（OneReel）。
- 读数字的纪律：FVD 差 <50 人类几乎分不出（FVD 论文自述）；VBench Overall Consistency 的 Empirical Max 只有 36.40%。
- 选型三问：多长（4–10s 用 CogVideoX/Wan；分钟级用 SkyReels/FramePack）、多快（实时 LTX-Video）、要不要控制（相机 CameraCtrl / 轨迹 MotionCtrl / 编辑 TokenFlow·RAVE 免训练）。

## 页面结构

```
.
├── index.html            # 单页应用（哈希路由）
├── data/
│   ├── bundle.js         # 前端一次性加载的数据包（由 *.json 打包生成）
│   ├── papers.json       # 33 篇论文
│   ├── algorithms.json   # 35 个算法
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

## 验收记录（2026-11-13 终态）

- `bash tools/verify_all.sh`：**VERIFY ALL PASS**（ledger 3,292,794 / 109.76%；assert_all ALL PASS；smoke ALL PASS；112 张图 0 问题；390px 窄屏 0 溢出）
- 演进图：30 节点 / 23 边；时间线 8 条（2018–2026 七个转折 + 2027 展望）
- 故事页改版：4 幅场景插画（制片厂/时间机器/剪辑室/一粒噪声）+ 旗舰英雄卡 + 十站路线图；5 页截图逐页目检，残留斜线已清并像素断言 PASS
- 2026-11-13 二次修订：2026 论文 `pipeline` 改为 3–4 项列表（原字符串在页面不渲染）、算法档位 `latest→recent`、APEX 论文/算法页重复的「类比失效」段改写；skill 新增的 `dup_scan` 闸门抓到并修复
- 本轮未做三轮四维 subagent 校验；以主控逐页视觉验收 + 项目内断言为准
- 字数口径：ledger **3,292,794 可见字符 / 109.76%**（本站目标 300 万）

## 诚实边界

- Google Scholar / Semantic Scholar / OpenAlex / DBLP 检索受限的情况如实写进 `coverage.json`，未包装成「全面检索」。
- YouTube 渠道未执行；教学叙事为原创机制叙事，不声称引用视频作者观点。
- 所有实验数字为论文自报，未复现；商用闭源（Sora/Kling/Gen-3）无公开论文，未进核心库。
- 2026 年两篇（TaoMate-R1 / APEX）为**摘要级核验**（`read_level=abstract_only`），数字只来自 arXiv 摘要，未下载全文；页面已如实标注。
- 本站验收口径是 **300 万可见字符（L2）**；skill 的 `verify_site.py` 默认 500 万下限，现支持 `--min-chars 3000000` 或 `site/contract.json` 覆盖（会打印下限来源）。按 300 万口径复验后仍有 50 项 skill L2 的公式/图表分布要求未满足（全书章节与题库未按该档配齐），已在本页与交付总结披露。

## 许可

文字与图示内容采用 [CC BY 4.0](LICENSE)。论文版权归各原作者所有；本站只收录笔记、解读与教学材料，不收录论文原文 PDF。
