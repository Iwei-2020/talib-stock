# Pandas TA Classic - 技术分析库

Pandas TA Classic 是一个基于 Pandas 的技术分析库，提供常用行情指标、K 线形态识别、统计工具和策略批量计算能力，适用于量化分析、行情研究、回测数据预处理等场景。

项目包含 224 个技术指标与工具函数，以及 62 个原生 K 线形态。核心指标默认使用 Python 原生实现，部分指标可按需启用 TA-Lib 或 Numba 加速。

## 核心能力

- 技术指标：覆盖趋势、动量、波动率、成交量、均线、统计等常用分类
- K 线形态：内置 62 个原生形态识别能力，无需依赖 TA-Lib
- Pandas 扩展：支持通过 `df.ta.<indicator>()` 直接调用指标
- 策略系统：支持批量计算多个指标，适合策略分析与特征构建
- 可选加速：可按需接入 TA-Lib 或 Numba 提升计算性能
- 示例与测试：包含示例脚本、文档和较完整的测试用例

## 安装

使用 `uv`：

```bash
uv pip install pandas-ta-classic
```

使用 `pip`：

```bash
pip install pandas-ta-classic
```

本地开发安装：

```bash
pip install -e ".[dev]"
```

安装可选能力：

```bash
pip install -e ".[optional]"
pip install -e ".[oracle]"
pip install -e ".[backtest]"
```

## 基础用法

```python
import pandas as pd
import pandas_ta_classic as ta

df = pd.read_csv("path/to/symbol.csv")

df.ta.sma(length=20, append=True)
df.ta.rsi(append=True)
df.ta.macd(append=True)
df.ta.bbands(append=True)
```

链式调用：

```python
df.ta.chain().sma(20).ta.rsi(14).ta.macd().ta.bbands(20)
```

运行内置策略：

```python
df.ta.strategy("CommonStrategy")
```

## 指标分类

- `candles`：K 线形态
- `cycles`：周期类指标
- `math`：数学工具
- `momentum`：动量指标
- `overlap`：均线与价格叠加指标
- `performance`：收益与回撤指标
- `statistics`：统计指标
- `trend`：趋势指标
- `volatility`：波动率指标
- `volume`：成交量指标

## 可选依赖

TA-Lib 和 Numba 都是可选依赖：

- 未安装 TA-Lib 时，核心指标使用原生实现
- 安装 TA-Lib 后，可通过 `talib=True` 启用部分指标的 C 库实现
- 安装 Numba 后，部分计算密集型指标可获得更好的性能
- K 线形态始终使用项目内置的原生实现

示例：

```python
df.ta.ema(length=20)
df.ta.ema(length=20, talib=True)
df.ta.cdl_pattern(name="all")
```

## 项目结构

```text
pandas_ta_classic/    核心源码
tests/                测试用例
docs/                 文档
examples/             示例代码
tools/                开发辅助工具
```

## 本地测试

```bash
pytest
```

如需运行包含可选依赖的测试，请先安装对应依赖组。

## 许可证

本项目基于 MIT License 开源，详情请查看 `LICENSE` 文件。
