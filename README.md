# Skill Collection

技能集合仓库，使用 Git Submodule 管理多个独立 Skill。

## 包含的技能

| 目录 | 技能名称 | 独立仓库 |
|------|----------|----------|
| `weekly-business-brief/` | 经营周报 Skill | [weekly-business-brief](https://github.com/wensente336-maker/weekly-business-brief) |
| `mckinsey-annual-plan/` | 麦肯锡年度规划 PDCA Skill | [mckinsey-annual-plan](https://github.com/wensente336-maker/mckinsey-annual-plan) |

## 克隆方式

### 一次性克隆所有技能
```bash
git clone --recursive https://github.com/wensente336-maker/luguanlan.git
```

### 单独克隆某个技能
直接克隆对应技能的独立仓库：
```bash
# 经营周报
git clone https://github.com/wensente336-maker/weekly-business-brief.git

# 麦肯锡PDCA
git clone https://github.com/wensente336-maker/mckinsey-annual-plan.git
```

## 更新子模块
```bash
# 更新所有子模块到最新版本
git submodule update --remote
```
