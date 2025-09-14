# Quant Research & Backtest Framework

本项目是一个基于 **Python** 的量化研究与回测框架，强调 **模块化、可复现、易扩展**。  
主要功能包括：数据获取、因子研究、组合构建、回测与绩效分析。

---

## 目录结构

```text
quant/                      # 框架核心代码
├─ __init__.py              # 包初始化
├─ config/                  # 配置文件 (YAML)，实验参数独立管理
│  ├─ base.yaml             # 基础配置示例
│  └─ hs300_example.yaml    # HS300 因子实验示例
├─ data/                    # 数据层
│  ├─ __init__.py
│  ├─ providers.py          # 数据源适配器 (AkShare/YFinance/CSV)
│  ├─ bundle.py             # 本地缓存管理 (Parquet/DuckDB)
│  └─ calendar.py           # 交易日历 & 日期对齐工具
├─ factors/                 # 因子层
│  ├─ __init__.py
│  ├─ base.py               # 因子基类定义
│  ├─ transforms.py         # 因子处理工具 (去极值/标准化/中性化)
│  ├─ momentum.py           # 动量因子实现
│  ├─ value.py              # 价值因子实现
│  └─ quality.py            # 质量因子实现
├─ pipeline/                # 因子流水线
│  ├─ __init__.py
│  ├─ engine.py             # 因子处理流水线引擎 (串接多个步骤)
│  └─ neutralize.py         # 行业/市值中性化方法
├─ portfolio/               # 投资组合层
│  ├─ __init__.py
│  ├─ sizing.py             # 权重生成方法 (Top-Bottom, 风险平价, 优化)
│  ├─ constraints.py        # 投资组合约束条件 (行业/杠杆/换手率)
│  └─ risk.py               # 风险模型 (波动率缩放, 协方差矩阵)
├─ backtest/                # 回测引擎
│  ├─ __init__.py
│  ├─ vectorized.py         # 向量化日频回测引擎
│  └─ slippage.py           # 手续费/滑点/冲击成本模型
├─ perf/                    # 绩效评估
│  ├─ __init__.py
│  ├─ metrics.py            # 常用指标 (年化, 夏普, 回撤, IC/RankIC)
│  └─ tearsheet.py          # 报告生成 (图表 & 表格)
├─ utils/                   # 工具函数
│  ├─ __init__.py
│  ├─ io.py                 # IO 工具 (读写路径, 缓存)
│  ├─ logging.py            # 日志工具
│  └─ seeds.py              # 随机种子管理
└─ cli/                     # 命令行入口
   ├─ __init__.py
   └─ run.py                # 命令行入口脚本 (读取 YAML, 跑实验)

tests/                      # 单元测试，保证模块正确性
notebooks/                  # 研究用 Jupyter Notebook (探索因子/画图)
