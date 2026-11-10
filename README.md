# Embodied Learning Baselines

> 具身学习基线合集：导航、全身运动和操作三个相互独立的 Python 包。

## 项目状态

| 项目 | 状态 |
| --- | --- |
| 维护状态 | Active |
| 项目类型 | 多包研究基线合集 |
| 数据范围 | 合成环境与 MuJoCo 仿真；没有真机数据 |
| 安装方式 | 每个子目录拥有独立 `pyproject.toml`、测试和说明 |

## 项目简介

本仓库将三个研究方向放在同一代码仓库中，但每个包可以独立安装和验证：

| 包 | 目录 | 内容 | 验证程度 |
| --- | --- | --- | --- |
| `interrupt-nav` | [`interactive_nav/`](interactive_nav/) | 人工接管、行为克隆、DAgger、在线纠正 | 单元测试 + 合成环境 |
| `terrain-carry-rl` | [`terrain_carry_rl/`](terrain_carry_rl/) | Go2 + Piper whole-body RL、迁移学习、蒸馏和 Sim2Real 基础设施 | 单元测试 + smoke |
| `sim2skill` | [`cleanrobot_sim2real/`](cleanrobot_sim2real/) | 复合清洁机器人拾放、擦拭技能与残差策略 | MuJoCo 仿真 |

三个目录分别由已归档的原仓库合并而来：[interactive-nav-learning](https://github.com/zxinyu-robot/interactive-nav-learning)、[terrain-carry-rl](https://github.com/zxinyu-robot/terrain-carry-rl)、[CleanRobot-Sim2Real-skill](https://github.com/zxinyu-robot/CleanRobot-Sim2Real-skill)。

## 研究尺度

- `interactive_nav/`：社会技术系统中的人机协作学习入口。
- `terrain_carry_rl/`、`cleanrobot_sim2real/`：单体智能的行为学习基础设施。

## 快速开始

```bash
cd interactive_nav
pip install -e ".[dev]"
pytest

cd ../terrain_carry_rl
pip install -e ".[dev]"
pytest
terrain-carry-rl smoke --config configs/smoke.json

cd ../cleanrobot_sim2real
pip install -e ".[dev]"
pytest
sim2skill smoke
```

每个子包的具体配置、限制和路线图以其目录 README 与 `docs/` 文档为准。

## 许可证

根目录、`interactive_nav/` 和 `cleanrobot_sim2real/` 使用 [MIT](LICENSE)；`terrain_carry_rl/` 沿用 Apache-2.0，见 [terrain_carry_rl/LICENSE](terrain_carry_rl/LICENSE)。
