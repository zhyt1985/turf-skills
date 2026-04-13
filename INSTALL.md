# Installation 安装

## Via npm (推荐)

```bash
npm install -g turf-skills
```

> 若不想全局安装，可直接使用 `npx turf-skills <command>`。

## Via npx skills

```bash
npx skills add zhyt1985/turf-skills
```

安装后使用 `npx turf-skills --action <name> [options]`。

## Via .skill file

1. Download `turf-skills-v1.0.3.skill` from releases
2. Install in Claude Code:
   ```bash
   claude skill install /path/to/turf-skills-v1.0.3.skill
   ```

## Manual Install

```bash
git clone https://github.com/zhyt1985/turf-skills.git
claude skill install ./turf-skills
```
