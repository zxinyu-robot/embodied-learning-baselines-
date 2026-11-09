# Embodied Learning Baselines

具身学习基线合集：三个相互独立的 Python 包，分别覆盖导航、全身运动和操作三类学习问题。每个包有自己的 `pyproject.toml`、测试和说明，可以单独安装。

| 包 | 目录 | 内容 | 验证程度 |
| --- | --- | --- | --- |
| `interrupt-nav` | [`interactive_nav/`](interactive_nav/) | 可中断交互式导航学习：人工接管、行为克隆、DAgger、在线纠正 | 单元测试 + 合成环境 |
| `terrain-carry-rl` | [`terrain_carry_rl/`](terrain_carry_rl/) | Go2 + Piper 紧耦合 whole-body RL：特权教师 → 学生蒸馏、迁移学习、Sim2Real 基础设施（不含 Isaac Lab 资产） | 单元测试 + smoke |
| `sim2skill` | [`cleanrobot_sim2real/`](cleanrobot_sim2real/) | 复合清洁机器人（底盘 + xArm + RealSense）拾放、擦拭技能与残差策略 | MuJoCo 仿真 |

没有真机数据，所有数字都来自合成环境或仿真。

三个目录分别由原仓库 [interactive-nav-learning](https://github.com/zxinyu-robot/interactive-nav-learning)、[terrain-carry-rl](https://github.com/zxinyu-robot/terrain-carry-rl)、[CleanRobot-Sim2Real-skill](https://github.com/zxinyu-robot/CleanRobot-Sim2Real-skill) 并入，原仓库已归档。

## 在三个研究尺度中的位置

- `interactive_nav/` 的人工接管与在线纠正，是“社会技术系统”尺度里人机协作的学习侧入口。
- `terrain_carry_rl/`、`cleanrobot_sim2real/` 属于“单体智能”尺度的行为学习。

## 快速开始

```bash
cd interactive_nav && pip install -e ".[dev]" && pytest
cd ../terrain_carry_rl && pip install -e ".[dev]" && pytest && terrain-carry-rl smoke --config configs/smoke.json
cd ../cleanrobot_sim2real && pip install -e ".[dev]" && pytest && sim2skill smoke
```

## 许可证

根目录与 `interactive_nav/`、`cleanrobot_sim2real/` 为 [MIT](LICENSE)；`terrain_carry_rl/` 沿用原仓库的 Apache-2.0（见 [terrain_carry_rl/LICENSE](terrain_carry_rl/LICENSE)）。
