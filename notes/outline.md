# 撰写大纲（Outline）

> 状态：⬜ 未开始 · 🟨 骨架已建、待材料 · 🟧 撰写中 · ✅ 初稿完成、待你审阅 · ☑️ 你已确认
> 决定、术语、符号与风险（R1–R13）见 [`discussion.md`](discussion.md)；收敛性方案见 [`convergence.md`](convergence.md)。

## 进度总览

| 部分 | 文件 | 状态 | 阶段 |
|---|---|---|---|
| Title / Abstract / Keywords | `main.tex`、`data/00-abstract.tex` | 🟧 标题改为 Hamiltonian Flow Control: An Energy-Descent Control Law for Nonlinear Systems（会话 18）；摘要与关键词待全文完成后撰写 | — |
| 1 Introduction | `data/01-introduction.tex` | 🟧 | 第一阶段：初稿完成，待确认 TODO |
| 2 Formulation | `data/02-formulation.tex` | 🟧 2.2–2.8、2.11 初稿（会话 18 按 Taylor 预瞄重写）；2.1、2.9、2.10、2.12 待写 | 第一阶段 |
| 3 Experiments | `data/03-experiments.tex` | ⬜ | 第二阶段（待结果） |
| 4 Conclusion | `data/04-conclusion.tex` | ⬜ | 第二阶段 |
| Acknowledgements / Declarations | `data/05-acknowledge.tex`、`data/06-declarations.tex` | ⬜ | 投稿前 |

---

## 1 Introduction

**目标：** 以工业界的 PID、LQR、MPC 为主线（另加 iLQR），指出"计算量 vs. 利用模型与预测的能力"之间的两极化，归纳研究空白；再由速度梯度（SG）方法与 Lan–Cvitanović 的相空间流代价引出 SEFC（会话 9 前称 HFC）。初稿完成于会话 6，会话 7 按算法细节改写了第 (8)–(13) 段；各段与 `data/01-introduction.tex` 中的注释编号一一对应。

| 段 | 内容 | 主要文献 | 状态 |
|---|---|---|---|
| (1) | 背景：工业界的 PID、LQR、MPC；计算量与利用模型能力的权衡；嵌入式平台需求 | Samad 等 2020 | ✅ |
| (2) | PID：无模型、算力低；积分记忆与 windup、微分放大噪声、只有线性外推式的预测、整定困难 | Åström & Hägglund 2001；Åström & Rundqwist 1989；Åström & Murray 2008；Ang 等 2005 | ✅ |
| (3) | LQR：Riccati 方程（离线 vs. 沿轨迹在线/增益调度）、无约束、局部有效、权重整定、LQG 无裕度保证 | Kalman 1960；Anderson & Moore 1990；Rugh & Shamma 2000；Bemporad 等 2002；Safonov & Athans 1977；Doyle 1978 | ✅ |
| (4) | MPC：约束与非线性；每步求解优化、稀疏分解、实时迭代、显式 MPC 的分区爆炸、终端条件 | Mayne 等 2000；Qin & Badgwell 2003；Rao 等 1998；Wang & Boyd 2010；OSQP；Diehl 等 2005；acados | ✅ |
| (5) | iLQR：DDP 变体、自动驾驶应用、计算量、约束扩展、局部解 | Li & Todorov 2004；Mayne 1966；Tassa 等 2012/2014；Chen 等 2017/2019 | ✅ |
| (6) | 结构化非线性设计（我补充的一段）：保证强但依赖模型结构、因系统而异 | Isidori；Krstić 等；Utkin；Ortega 等；Khalil | ✅ 待你决定是否保留 |
| (7) | 研究空白 | — | 🟧 计算量论断需实测支撑（R11）；需与 Newton–Raphson 流方法区分（Q18） |
| (8) | SG 方法：原理、优点、三条局限（第一条改用"低阶状态"表述，与 HFC 的亮点呼应） | Fradkov 1979/1996/2007；Fradkov 等 1999；Shiriaev & Fradkov 2000；Åström & Furuta 2000；Shiriaev 等 2000 | ✅ |
| (9) | Lan–Cvitanović 的变分方法：λ𝐯 − 𝐯̃ 的失配、Newton descent 下指数衰减、离散形式、高阶导数推广 | Lan & Cvitanović 2004 | ✅ 已按原文核对 |
| (10) | 最接近的已有工作：C/GMRES；Newton–Raphson 流（含四旋翼、算力受限飞行器、平坦系统稳定性）及与 HFC 的两点区别（第二点改为 Taylor 多项式的闭式预测） | Ohtsuka 2004；Wardi 等 2017/2024；Shivam 等 2019；Morales-Cuadrado 等 2024/2026；Niu 等 2025 | ✅ 会话 18 |
| (11) | HFC 概述：采样参考与第 m 个点；流代价；梯度流与每轮一次更新；与 SG 的一阶关系；Taylor 预瞄（与 Lan 的高阶导数匹配呼应）；F/2 = Q + τ𝓗 的 Hamiltonian 解释与命名；非力学意义的说明 | Lan & Cvitanović 2004；Pontryagin 1962 | ✅ 会话 18 |
| (12) | 主要贡献（5 条，会话 18 改写：Hamiltonian 形式、Taylor 预瞄、积分链与时滞、自行车直线参考的稳定性） | Graichen 等 2007；Lee 等 2010 | 🟧 待一般收敛定理、基线 |
| (13) | 文章结构（会话 18 按新的 Formulation 更新） | — | ✅ Section 2–4 定稿后复核 |
| (14) | 符号说明 | — | ⬜ Formulation 定稿后补充 |

**需要你确认：** 第 (6) 段是否保留；另请通读全文语气与论断强度。

---

## 2 Formulation

**目标：** 给出可复现的构造、严格的性质与收敛性证明，并在三个系统上推导出显式控制律。

| # | 小节 | 要点 | 状态 |
|---|---|---|---|
| 2.1 | Geometric preliminaries | 流形、切丛与余切丛、辛形式、SO(3)/SE(3) 与 hat/vee 映射；篇幅从简（R10） | ⬜ |
| 2.2 | Problem setting | 局部坐标下的被控系统、层级划分；参考为不带时间戳的离散状态采样点（间隔约等于 h）；目标为向前第 m 个采样点，τ = mh；误差 𝐞_k = 𝐱(t_k) − 𝐱_{r,k}（相对于此刻应到达的采样点）；𝐱_r 仅用于分析 | 🟧 初稿（流形版待 2.1） |
| 2.3 | The flow-based cost | F = τ²‖Γ(𝐯_τ − (𝐱_ref − 𝐱)/τ)‖²：流与指向目标采样点的割线速度之差；与 Lan 离散代价的对应；Γ = diag(√w)·Γ̄ | 🟧 初稿 |
| 2.4 | Taylor look-ahead | 定义 1（Taylor 预瞄：τ² 以内精确，更高阶在 𝐮 = 0 处线性化）；输入到达各层的阶次；仿射条件 ∂g_i g_j = 0；展开式 ρ = ½(∂𝐯)𝐯；注 1（分级形式作对照） | ✅ 初稿（会话 18） |
| 2.5 | Control law and implementation | 控制律与量纲配平系数；采样数据实现（式 update：每轮测量、前向 Euler 更新、一轮计算延迟）；高阶更新可选 | 🟧 初稿（约束的投影表述待补） |
| 2.6 | Properties of the flow cost | 命题 1（Hamiltonian 形式 F = 2Q + 2τ𝓗；与 SG 的关系；低阶误差的进入方式）；注 2（控制 Hamiltonian 与能量型结构、命名、非力学意义）；注 3 | 🟧 F 的非负性与零点集待补 |
| 2.7 | Convergence analysis | 命题 2（Taylor 预瞄的积分链：截断指数多项式）；注 4（等权重到 L ≤ 4；采样数据 τ > 1.526h）；引理 1（缺陷含 𝐮̇_r 项，θ = τ 时为三阶）；定理 1；例 1（只有时滞）；注 5 | 🟧 一般非线性定理待证（convergence.md 方案 A、C、D） |
| 2.8 | Non-uniform sample intervals | 按序号取点时 τ = mh 已是正确的；若要按时间跟踪，由采样点估计时间（弦长 / 平均速度），按时间选目标；梯度版自适应 τ 已删除（会话 18） | ✅ 初稿（仿真数值放 Experiments） |
| 2.9 | Design procedure | Algorithm 框；参数选择：Taylor 阶数 L、τ = mh（τ > 1.526h）、权重（注 4 的 Hurwitz 条件）、前向 Euler 更新；自行车另见注 6 | ⬜ |
| 2.10 | Example: double inverted pendulum | 力输入的完整 Euler–Lagrange 模型；两级层级，Taylor 预瞄到 τ²；同一控制律不切换；方案 C 的线性化判据与数值吸引域 | ⬜ |
| 2.11 | Example: kinematic bicycle | 模型与三级层级；Taylor 预瞄（式 24，三阶，略去 r̈）、代价、控制律（∂_𝐮Φ̂ 两列）；误差进入输入的路径（杠杆臂 l_r/2 + τu/6）；命题 3（直线参考，单位权重稳定，CAD 证明）；注 6（采样数据闭环的临界 κ）；跟踪误差；参考条件 | ✅ 初稿（会话 18，与代码一致） |
| 2.12 | Example: quadrotor | SE(3) 模型；4 级链，Taylor 预瞄到 τ⁴，SO(3) 上的 Magnus 型展开；等权重在 L = 4 时可行；输入在 𝐮 = 0 处线性化 | ⬜ |

**结构建议（待你决定）：** ND 篇幅宽松，三个算例可以写得较完整。若推导较长，可把 2.10–2.12 单独成节（例如 "Application to benchmark systems"），让 Formulation 专注于一般理论。章节标题 "Formulation" 也可以考虑改为 "Hamiltonian flow control" 或 "Problem formulation and main results"。（会话 18：方法已改名 HFC。）

**需要你提供：**倒立双摆与四旋翼的模型、分级方式与权重（尚未准备，算例章节暂缓）。

---

## 3 Experiments（第二阶段，先预留）

三个系统都做仿真和实物实验，后续有实验团队参与（会话 4）。

- 仿真设置：模型参数、初值、积分格式与步长、控制器参数
- 评价指标：跟踪误差、收敛时间、超调、控制能量、计算耗时等
- 对比基线：见 discussion R6
- 鲁棒性测试：参数摄动、测量噪声、外部扰动
- 自行车：按注 5 选步长 h 与 m，使预瞄距离 Uτ 不超过约一个轴距（R16）；小车平台轴距短，尤其要注意
- 实物实验：平台、传感器、控制频率；倒立双摆如何施加并标定小车上的力、摩擦是建模还是补偿、模型参数辨识、小车最大位移与实际轨道长度（R4）
- 图表清单：（待定）

## 4 Conclusion（第二阶段，先预留）

- 方法特点总结
- 局限性
- 推广方向与可能的变体（例如自适应版本，见 Q8）

---

## 期刊要求：Nonlinear Dynamics（Springer）

细节以官方 Submission guidelines 为准，投稿前核实。

| 事项 | 要求 / 现状 |
|---|---|
| 引用样式 | 方括号顺序编号 [1]、[1, 2]、[1–4]，按首次引用排序 —— 已配置 |
| 篇幅 | 相对宽松 |
| LaTeX 模板 | Springer Nature 模板（`sn-jnl`）；目前用通用 article 格式，投稿时如有需要再迁移 |
| 声明 | Statements and Declarations：Funding、Competing interests、Data availability 等 —— 已在 `data/06-declarations.tex` 预留 |
| 摘要与关键词 | 字数与个数以官方要求为准 |
