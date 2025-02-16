# AegirPS

[English](README.md)

很遗憾DoctoratePy项目已停止维护。本仓库旨在为游戏新版本提供持续支持。

某动漫塔防游戏的Python服务器实现（国服TapTap版本）。

## 已测试可用的模拟器

1. MuMu Player 12（**推荐**）

2. LDPlayer9（可用，但**不推荐**）

## 使用指南

### MuMu Player 12

1. 在模拟器设置中启用root权限（ADB连接默认已开启，无需手动设置）
2. 启动MuMu Player 12
3. 运行`setup_requirements.bat`，看到"Press enter to exit..."提示即表示成功
4. 运行`start_local_server.bat`，窗口应保持开启状态（若无报错）
5. 运行`start_frida-server.bat`，窗口应保持开启状态（若无报错）
6. 运行`start_frida-hook.bat`，将自动启动游戏。窗口应保持开启状态（若无报错）

#### 实验性方案

1. 在模拟器设置中启用root权限（ADB连接默认已开启）
2. 启动MuMu Player 12
3. 运行`setup_requirements.bat`（此步骤只需执行一次），看到"Press enter to exit..."即成功
4. 运行`one_click_run.bat`，若无错误，三个窗口将保持开启

### LDPlayer9

1. 在设置中启用root权限和ADB连接
2. 启动LDPlayer9
3. 运行`setup_requirements.bat`，看到"Press enter to exit..."即成功
4. 运行`start_local_server.bat`，窗口应保持开启（若无报错）
5. 运行`start_frida-server.bat`，窗口应保持开启（若无报错）
6. 运行`start_frida-hook.bat`，将自动启动游戏。窗口应保持开启（若无报错）

## 修改危机合约赛季

修改`config\config.json`中`selectedCrisis`键值为所需赛季。可用赛季位于`data\crisis`目录下。

## 自定义干员属性

在`config\config.json`的`customUnitInfo`键中添加配置。干员关键名可参考[此文件](https://raw.githubusercontent.com/Kengxxiao/ArknightsGameData/master/zh_CN/gamedata/excel/character_table.json)。默认所有干员为满级/满潜/专三。

- `favorPoint` - 信赖值（25570对应200%信赖）[换算参考](https://gamepress.gg/arknights/core-gameplay/arknights-guide-operator-trust)
- `mainSkillLvl` - 技能等级（低于7级时专精填0）
- `potentialRank` - 潜能等级（0-5）
- `evolvePhase` - 精英化阶段（0-E0，1-E1，2-E2）
- `skills` - 各技能专精等级（从S1开始）

### 格式示例
```
"<operator_key_name>": {
    "favorPoint": 25570,
    "mainSkillLvl": 7,
    "potentialRank": 2,
    "level": 50,
    "evolvePhase": 1,
    "skills": [1, 0]
}
```

## 自定义助战单位

修改`config/assist.json`配置助战单位列表。完整干员数据参考[此处](https://raw.githubusercontent.com/Kengxxiao/ArknightsGameData/master/zh_CN/gamedata/excel/character_table.json)。

- `charId` - 干员关键名
- `skillIndex` - 使用技能序号（从0开始）
- `currentEquip` - 模组配置

### 格式示例
```
{
    "charId": "char_479_sleach",
    "skillIndex": 2,
    "currentEquip": "uniequip_002_sleach"
}
```

## 保留游戏内配置

设置`config/config.json`中：
- `"userConfig"` -> `"restorePreviousStates"` -> `"squadsAndFavs"`为`true`可保留编队/收藏配置
- `"userConfig"` -> `"restorePreviousStates"` -> `"ui"`为`true`可保留UI设置

## 重要警告！

若使用自研hook脚本将流量重定向至AegirPS（而非使用本项目frida hook），可能导致一些功能失效，例如3倍速，暂停部署，HP显示，无限活动时长，模组功能等
