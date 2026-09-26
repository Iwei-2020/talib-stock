<p align="center">
 <a href="https://github.com/xgboosted/pandas-ta-classic">
 <img src="https://raw.githubusercontent.com/xgboosted/pandas-ta-classic/main/docs/images/logo.png" width="150" height="150" alt="Pandas TA Classic">
 </a>
</p>

# Pandas TA Classic - 技术分析库

[![License](https://img.shields.io/github/license/xgboosted/pandas-ta-classic?style=flat)](https://github.com/xgboosted/pandas-ta-classic/blob/main/LICENSE)
[![Build Status](https://img.shields.io/github/actions/workflow/status/xgboosted/pandas-ta-classic/ci.yml?branch=main&style=flat)](https://github.com/xgboosted/pandas-ta-classic/actions/workflows/ci.yml)
[![Documentation](https://img.shields.io/badge/docs-GitHub%20Pages-blue)](https://xgboosted.github.io/pandas-ta-classic/)
[![Python Version](https://img.shields.io/pypi/pyversions/pandas-ta-classic?style=flat)](https://pypi.org/project/pandas-ta-classic/)
[![PyPI Version](https://img.shields.io/pypi/v/pandas-ta-classic?style=flat)](https://pypi.org/project/pandas-ta-classic/)
[![Package Status](https://img.shields.io/pypi/status/pandas-ta-classic?style=flat)](https://pypi.org/project/pandas-ta-classic/)
[![Downloads](https://img.shields.io/pypi/dm/pandas-ta-classic?style=flat)](https://pypistats.org/packages/pandas-ta-classic)
[![Stars](https://img.shields.io/github/stars/xgboosted/pandas-ta-classic?style=flat)](https://github.com/xgboosted/pandas-ta-classic/stargazers)
[![Forks](https://img.shields.io/github/forks/xgboosted/pandas-ta-classic?style=flat)](https://github.com/xgboosted/pandas-ta-classic/forks)
[![Dependents](https://img.shields.io/librariesio/dependents/pypi/pandas-ta-classic?style=flat)](https://libraries.io/pypi/pandas-ta-classic/dependents)
[![Contributors](https://img.shields.io/github/contributors/xgboosted/pandas-ta-classic?style=flat)](https://github.com/xgboosted/pandas-ta-classic/graphs/contributors)

![示例图表](https://raw.githubusercontent.com/xgboosted/pandas-ta-classic/main/docs/images/TA_Chart.png)

> **Pandas TA Classic** 是一个易用的技术分析库，基于 Pandas 构建，提供 **224 个指标与工具函数** 和 **62 个原生 K 线形态**（共 **284 个唯一功能**，无需 TA-Lib）。常用指标包括：_简单移动平均线_（**sma**）、_移动平均收敛发散指标_（**macd**）、_Hull 指数移动平均线_（**hma**）、_布林带_（**bbands**）、_能量潮_（**obv**）、_Aroon 与 Aroon Oscillator_（**aroon**）、_Squeeze_（**squeeze**）等。

这是流行的 `pandas-ta` 库的 **经典版 / 社区维护版本**。

## 初次使用 Pandas TA Classic？

**通过完整指南快速上手：**

- **[快速开始指南](https://github.com/xgboosted/pandas-ta-classic/blob/main/docs/quickstart.md)** - 安装、第一个指标和常见工作流
- **[教程](https://github.com/xgboosted/pandas-ta-classic/blob/main/docs/tutorials.md)** - 面向真实场景的分步教程：
 - 移动平均线交叉策略
 - 构建自定义指标策略
 - 使用性能指标进行回测
 - 集成 backtesting.py
 - 集成 backtrader
 - 集成 VectorBT
 - 集成 manifoldbt
 - 多周期分析
 - 创建自定义指标
 - K 线形态识别

**完整文档：** [**https://xgboosted.github.io/pandas-ta-classic/**](https://xgboosted.github.io/pandas-ta-classic/)

### 核心特性

- **284 个唯一指标与形态**：224 个分类指标 + 通过 `cdl_pattern()` 提供的 62 个 CDL 形态 = 284 个唯一功能（`doji` 和 `inside` 会同时出现在两个统计口径中；所有 CDL 形态均使用原生 Python 实现，无需 TA-Lib）
- **全原生 K 线形态**：全部 62 个 CDL 形态都提供原生 Python 实现，K 线形态永远不会依赖 TA-Lib
- **可选 TA-Lib 加速**：核心指标（EMA、SMA、RSI、MACD、OBV、ATR 等）默认使用原生实现；传入 `talib=True` 可使用 TA-Lib
- **明确的兼容范围**：并非所有 TA-Lib / tulipy 函数都有 pandas-ta-classic 对应实现。当前覆盖情况请查看完整指标矩阵：`docs/indicator_support_matrix.rst`
- **可选性能增强**：安装 `numba` 后，可让热点循环指标获得 6–230 倍加速（QQE、RSX、HWMA、SSF、PSAR、Supertrend、MCGD）
- **自动版本管理**：通过 git tag 和 setuptools-scm 管理版本
- **现代包管理支持**：完整支持 `uv` 和 `pip`
- **生产可用**：状态稳定，并包含基于 Hypothesis 的属性测试等完整测试覆盖
- **持续维护**：定期更新并接受社区贡献

## 快速开始

### 安装

该库同时支持现代包管理器 **uv** 和传统 **pip**。

**稳定版本**

使用 `uv`（推荐，速度更快）：
```bash
uv pip install pandas-ta-classic
```

使用 `pip`：
```bash
pip install pandas-ta-classic
```

**最新版本**

使用 `uv`：
```bash
uv pip install git+https://github.com/xgboosted/pandas-ta-classic
```

使用 `pip`：
```bash
pip install -U git+https://github.com/xgboosted/pandas-ta-classic
```

**开发环境安装**

使用 `uv`：
```bash
# 克隆仓库
git clone https://github.com/xgboosted/pandas-ta-classic.git
cd pandas-ta-classic

# 安装全部核心依赖（不包含对平台较敏感的 backtest extra，
# 如有需要请单独安装）
uv pip install -e ".[all]"

# 或安装指定依赖组：
uv pip install -e ".[dev]" # 开发工具
uv pip install -e ".[optional]" # 可选运行时功能
uv pip install -e ".[oracle]" # Oracle 对齐库：TA-Lib
uv pip install -e ".[backtest]" # 回测：backtesting、vectorbt、backtrader
```

使用 `pip`：
```bash
# 克隆仓库
git clone https://github.com/xgboosted/pandas-ta-classic.git
cd pandas-ta-classic

# 安装全部核心依赖（不包含对平台较敏感的 backtest extra，
# 如有需要请单独安装）
pip install -e ".[all]"

# 或安装指定依赖组：
pip install -e ".[dev]" # 开发工具
pip install -e ".[optional]" # 可选运行时功能
pip install -e ".[oracle]" # Oracle 对齐库：TA-Lib
pip install -e ".[backtest]" # 回测：backtesting、vectorbt、backtrader
```

### 基础用法

```python
import pandas as pd
import pandas_ta_classic as ta

# 加载你的数据
df = pd.read_csv("path/to/symbol.csv")
# 或直接使用 yfinance 获取 OHLCV 数据（pandas-ta-classic 本身不负责获取数据；
# 可参考 examples/fetch_market_data.py）：
# import yfinance as yf
# df = yf.download("AAPL", period="1y")

# 计算指标
df.ta.sma(length=20, append=True) # 简单移动平均线
df.ta.rsi(append=True) # 相对强弱指数
df.ta.macd(append=True) # MACD
df.ta.bbands(append=True) # 布林带

# 链式 API（v0.6+）
df.ta.chain().sma(20).ta.rsi(14).ta.macd().ta.bbands(20)

# 或运行包含多个指标的策略
df.ta.strategy("CommonStrategy") # 运行常用指标集合
```

## 功能

- **224 个技术指标与工具函数**，覆盖 10 个分类（Candles、Cycles、Math、Momentum、Overlap、Trend、Volume 等）
- **62 个原生 K 线形态**，全部原生实现，无需 TA-Lib
- **284 个唯一指标与形态**：224 个分类指标 + 通过 `cdl_pattern()` 提供的 62 个 CDL 形态
- **动态分类发现**：自动从文件系统中检测所有可用指标
- **可选 Numba 加速**：通过 `pip install pandas-ta-classic[performance]` 获得 6–230 倍加速
- **策略系统**：支持多进程批量处理指标
- **链式 API**：``df.ta.chain().sma(20).ta.rsi(14).ta.macd().ta.bbands(20)``，可在单个表达式中串联多个指标
- **Pandas DataFrame 扩展**：可无缝使用 `df.ta.<indicator>()`，例如 `df.ta.rsi()`
- **TA-Lib 集成（双重角色）**：**(1) 加速后端**：核心指标默认使用原生实现；传入 `talib=True` 可使用 TA-Lib 的 C 实现。**(2) Oracle 校验**：`test_oracle_talib.py` 用于验证与 TA-Lib 的一致性
- **tulipy 集成（仅冻结 Oracle）**：`test_oracle_tulipy.py` 会基于已提交的 tulipy 输出快照（`tests/fixtures/tulipy_oracle.json`）验证原生输出；测试时不再安装 tulipy，也不会把 tulipy 作为计算后端
- **Backtesting.py 集成**：提供桥接函数和可运行的 SMA 交叉示例：``examples/backtesting_py_strategy.py``
- **backtrader 集成**：采用预计算后再输入的模式，并包含动态 `PandasData` 子类；可运行示例见 ``examples/backtrader_strategy.py``
- **Vectorbt 集成**：兼容流行的回测框架
- **manifoldbt 集成**：采用预计算后注册外生序列的模式；可运行示例见 ``examples/manifoldbt_strategy.py``
- **自定义指标**：可以轻松创建并链式调用自定义指标

## 文档

**完整文档地址：** [**https://xgboosted.github.io/pandas-ta-classic/**](https://xgboosted.github.io/pandas-ta-classic/)

### 学习资源

**从这里开始：**
- [**快速开始指南**](https://github.com/xgboosted/pandas-ta-classic/blob/main/docs/quickstart.md) - 几分钟内完成上手
- [**教程**](https://github.com/xgboosted/pandas-ta-classic/blob/main/docs/tutorials.md) - 常见工作流的分步指南
- [**示例**](https://github.com/xgboosted/pandas-ta-classic/tree/main/examples) - 包含真实示例的 Jupyter Notebook

**参考文档：**
- [**使用指南**](https://xgboosted.github.io/pandas-ta-classic/usage.html) - 编程约定与基础用法
- [**策略系统**](https://xgboosted.github.io/pandas-ta-classic/strategies.html) - 多进程与批量指标处理
- [**指标参考**](https://xgboosted.github.io/pandas-ta-classic/indicators.html) - 224 个指标与 62 个 CDL 形态的完整列表（共 284 个唯一功能）
- [**DataFrame API**](https://xgboosted.github.io/pandas-ta-classic/dataframe_api.html) - 属性与方法参考
- [**性能指标**](https://xgboosted.github.io/pandas-ta-classic/performance.html) - 回测与绩效分析

## Python 版本支持

**Pandas TA Classic** 采用 **滚动支持策略**：支持最新稳定 Python 版本及其前 4 个 minor 版本。

> **注意：** Python 版本支持通过 CI/CD 工作流动态管理。新 Python 版本发布后，库会自动更新以支持最新 5 个 minor 版本。请查看 [CI workflow](https://github.com/xgboosted/pandas-ta-classic/blob/main/.github/workflows/ci.yml) 中的 `LATEST_PYTHON_VERSION` 获取当前配置。

**TA-Lib 和 tulipy 扮演不同角色**，两者都是完全可选依赖；未安装时会自动跳过相关能力。

| 库 | 角色 | 安装后的效果 |
|---------|------|-----------------------|
| TA-Lib | **加速后端 + 实时 Oracle** | 核心指标默认原生实现，可通过 `talib=True` 启用；同时在 `test_oracle_talib.py` 中用于实时一致性校验 |
| tulipy | **仅冻结 Oracle** | 不是计算后端，测试时也不会安装；`test_oracle_tulipy.py` 会与已提交的 tulipy 输出快照进行比较。只有重新生成该快照时才需要 tulipy（CPython <3.12） |

| 领域 | 未安装 TA-Lib 时 | 安装 TA-Lib 后 |
|------|--------------------------|----------------------|
| CDL 形态（62 个） | 原生 Python，始终可用 | 仍然使用原生实现，TA-Lib **永远不会** 用于 K 线形态 |
| 核心指标（59 个） | 原生 Python（默认） | 可通过 `talib=True` 使用 TA-Lib |

```python
# CDL 形态：始终使用原生实现，无需 TA-Lib
df.ta.cdl_pattern(name="all") # 运行全部 62 个形态
df.ta.cdl_pattern(name="engulfing") # 运行单个形态

# 核心指标：默认使用原生实现
df.ta.ema(length=20) # 原生实现
df.ta.ema(length=20, talib=True) # 使用 TA-Lib
```

安装 Oracle 库：
```bash
# uv
uv pip install pandas-ta-classic[oracle] # 安装 TA-Lib（实时 Oracle）
uv pip install TA-Lib # 仅安装 TA-Lib（同时启用加速后端）
# pip
pip install pandas-ta-classic[oracle] # 安装 TA-Lib（实时 Oracle）
pip install TA-Lib # 仅安装 TA-Lib（同时启用加速后端）
# tulipy 仅在重新生成冻结 Oracle 快照时需要（CPython <3.12）：
pip install tulipy && python tests/fixtures/generate_tulipy_oracle.py
```

> **注意：** 未安装 TA-Lib 时，`test_oracle_talib.py` 会自动跳过（`@unittest.skipUnless`）。`test_oracle_tulipy.py` 会在每个 Python 版本上基于已提交的 `tulipy_oracle.json` 快照运行（仅当该 fixture 缺失时跳过），不要求安装 tulipy。正常使用不需要安装二者。安装 TA-Lib 后，还可以通过 `talib=True` 为核心指标启用 C 库加速。

**性能增强：** 安装 `numba` 可为计算密集型指标带来 6–230 倍加速：
- 使用 `uv`：`uv pip install pandas-ta-classic[performance]`
- 使用 `pip`：`pip install pandas-ta-classic[performance]`

## 贡献

欢迎贡献代码！请查看 [贡献指南](https://github.com/xgboosted/pandas-ta-classic/blob/main/CONTRIBUTING.md) 和 [Issues 页面](https://github.com/xgboosted/pandas-ta-classic/issues)。

### 问题反馈
- 请先检查 [已有 Issues](https://github.com/xgboosted/pandas-ta-classic/issues)
- 提供可复现的代码示例
- 附上相关错误信息和数据样例

## 更新日志

详细的变更、改进和新功能请查看 [CHANGELOG.md](https://github.com/xgboosted/pandas-ta-classic/blob/main/CHANGELOG.md)。

## 来源

[Original TA-LIB](http://ta-lib.org/) | [TradingView](http://www.tradingview.com) | [Sierra Chart](https://search.sierrachart.com/?Query=indicators&submitted=true) | [MQL5](https://www.mql5.com) | [FM Labs](https://www.fmlabs.com/reference/default.htm) | [Pro Real Code](https://www.prorealcode.com/prorealtime-indicators) | [User 42](https://user42.tuxfamily.org/chart/manual/index.html)

## 支持

如果你觉得这个库有帮助，可以考虑支持项目：

[![Sponsor](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/xgboosted)

## 许可证

本项目基于 MIT License 开源，详情请查看 [LICENSE](https://github.com/xgboosted/pandas-ta-classic/blob/main/LICENSE) 文件。
