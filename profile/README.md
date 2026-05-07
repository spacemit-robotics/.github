[English](./README.md) | [简体中文](./README_cn.md)

# Platform Overview

**Integrate RISC‑V edge compute, AI, and ROS2 engineering into a reusable robotics foundation.**

SpacemiT Robot SDK targets **RISC‑V robotics platforms** with a unified stack from **system & peripherals**, **multimedia & acceleration**, **AI inference & interaction**, through **ROS2 feature packages**—so you can turn capabilities into runnable whole‑robot solutions faster.

You do not need to assemble a complex software environment or master every detail of the build chain or ROS2 build mechanics. Robot SDK exposes a single set of shortcut commands for **full builds** and **per‑component builds**, turning repetitive steps into reusable workflows so you can focus on features and source changes.

## 1. What You Get

<!-- GitHub strips most CSS (e.g. display:grid on divs); use HTML tables for a 2-column layout. -->
<table>
  <tr>
    <td align="center" valign="top" width="50%">
      <img src="https://cdn-resource.spacemit.com/file/product/K3/assets/robot_nav2.gif" alt="Wheeled robot patrol demo" width="420" /><br />
      Wheeled robot patrol
    </td>
    <td align="center" valign="top" width="50%">
      <img src="https://cdn-resource.spacemit.com/file/product/K3/assets/lerobot.gif" alt="Manipulator pick-and-place demo" width="420" /><br />
      Manipulator pick‑and‑place
    </td>
  </tr>
  <tr>
    <td align="center" valign="top" width="50%">
      <img src="https://cdn-resource.spacemit.com/file/product/K3/assets/robot_dance_demo.gif" alt="Humanoid dance demo" width="420" /><br />
      Humanoid dance demo
    </td>
    <td align="center" valign="top" width="50%">
      <img src="https://cdn-resource.spacemit.com/file/product/K3/assets/reachy_mini.gif" alt="Reachy Mini gesture tracking" width="420" /><br />
      Reachy Mini gesture tracking
    </td>
  </tr>
</table>

- **Reproducible end‑to‑end reference designs**: Humanoids, wheeled robots, desktop robots, arms, quadrupeds, and other typical forms—aligned engineering composition and practice paths.
- **Reusable on‑device AI**: Vision / speech / LLM / VLM / Agent delivered as components and examples—validate standalone, then integrate on the robot.
- **Composable ROS2 pipelines**: Perception, control, SLAM, navigation, planning as packages—pick and extend by scenario.
- **Product‑grade reproducible configuration**: Combine repo/manifest selections for hardware/product targets—make “it runs” the default: maintainable and upgradable.
- **Customizable system & platform base**: Peripheral drivers, system services, shared memory / multimedia acceleration for edge real‑time and performance.

## 2. Start in 30 Seconds

- **Get something running first (shortest path)**: [02 — Quick start (overview)](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/02-%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8)
- **Reproduce an end‑to‑end design**: [03 — Reference designs (overview)](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/03-%E5%8F%82%E8%80%83%E6%96%B9%E6%A1%88)
- **Browse by capability / module**: topic hubs
  - [04 — AI and algorithms](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/04-AI%E4%B8%8E%E7%AE%97%E6%B3%95) (speech / vision / LLM / VLM / Agent)
  - [05 — Robotics development](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/05-%E6%9C%BA%E5%99%A8%E4%BA%BA%E5%BC%80%E5%8F%91) (perception / control / SLAM / navigation / planning)
  - [06 — System & platform](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/06-%E7%B3%BB%E7%BB%9F%E4%B8%8E%E5%B9%B3%E5%8F%B0) (system services / peripherals / multimedia)
- **Full TOC or other topics**: [ROS / SDK documentation hub (community)](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/root_overview.md) — root of the doc tree; open sections beyond the quick links above.

## 3. Architecture & Layers

![System architecture](assets/robot-arch-en.jpg)

How to read the diagram (top to bottom):

- **Application & reference designs**: End‑to‑end apps and whole‑robot references (see [03 — Reference designs](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/03-%E5%8F%82%E8%80%83%E6%96%B9%E6%A1%88)).
- **Full‑stack toolchain**: One‑click deploy, cloud‑native dev environments, production‑grade build tools, simulation & migration, on‑device AI deployment—to speed up development, verification, and delivery.
- **Polymorphic middleware**: ROS2 / DDS / custom protocols / multi‑process IPC / no‑middleware direct modes—for different system shapes and comms needs (see [05 — Robotics development](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/05-%E6%9C%BA%E5%99%A8%E4%BA%BA%E5%BC%80%E5%8F%91)).
- **Core capability suite**: AI components for vision / speech / LLM / VLM / Agent (see [04 — AI and algorithms](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/04-AI%E4%B8%8E%E7%AE%97%E6%B3%95)); platform services, peripherals, multimedia (see [06 — System & platform](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/06-%E7%B3%BB%E7%BB%9F%E4%B8%8E%E5%B9%B3%E5%8F%B0)).
- **OS layer**: Ubuntu / Bianbu / Buildroot and runtime environments.
- **Kernel layer**: Linux kernel / RTOS kernel.
- **Compute platform**: SpacemiT RISC‑V AI CPU.

```text
spacemit_robot/
├── application/                 # Application recipes (case aggregation)
│   ├── native/                  # Non‑ROS2 applications
│   │   ├── reachy_mini/
│   │   ├── lerobot_app/
│   │   ├── omni_agent/
│   │   └── humanoid_*/
│   └── ros2/                    # ROS2 reference apps
│       └── linksee/
├── middleware/
│   └── ros2/                    # ROS2 middleware layer
│       ├── perception/ planning/ slam/
│       ├── control/ peripherals/ interfaces/
│       └── multimedia/ mpp/ gui/ tools/
├── components/                  # Shared capability components
│   ├── peripherals/ multimedia/ model_zoo/
│   ├── control/ ai-gateway/ agent_tools/
│   └── simulation/ system/ rvv_libs/ thirdparty/
├── target/                      # Hardware / product configuration
└── build/                       # One‑shot build scripts
```

Directory layout highlights:

- **Capabilities vs framework—not locked into ROS2**: `components/` holds devices, models, multimedia, control, etc.; `middleware/` adapts and orchestrates transports (e.g. ROS2). Ship native first, then add ROS2, Fast DDS, custom stacks, or direct modes—without upfront middleware coupling.
- **Apps decoupled from capabilities**: Apps (`reachy_mini`, `humanoid_*`, `application/ros2` such as `linksee`) share the same bottom layers; new form factors are mostly swapping application bundles, not rewriting capabilities.
- **Composable checkout**: `repo init -g` groups let you fetch humanoid / wheeled / desktop / perception / planning‑control slices—smaller trees and faster iteration.
- **Fast composition for solutions**: New products assemble selected components + middleware + app shell + `target` profile—demonstrable, iterative, and maintainable vs. greenfield stacks.

## 4. Releases & Changes

- **Release notes & compatibility**: [07 — Version notes](https://www.spacemit.com/community/document/info?lang=en&nodepath=software/SDK/ros/k3/07-%E7%89%88%E6%9C%AC%E8%AF%B4%E6%98%8E)
