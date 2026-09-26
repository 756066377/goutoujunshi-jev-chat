<!-- README_SYNC: source=working-tree; updated=2026-09-26 -->

<p align="center">简体中文 · <a href="./README_EN.md">English</a></p>

# 狗头军师 Jev Chat

**聊天窗口旁的狗头军师：读屏、分析、生成回复草稿。** 这是从[狗头军师](https://github.com/shengjidaguai-china/goutoujunshi)延伸出来的独立项目。运行环境以 Windows 主机为主（支持 Windows 10/11 与 微信 Windows 4.x）。程序支持聊天窗口文本采集、Jev 策略判断和候选回复草稿生成。发送始终由用户决定。

如果这套聊天副驾对你有用，可以给[项目点一个 Star](https://github.com/shengjidaguai-china/goutoujunshi-jev-chat/stargazers)，方便以后找到，也让更多有相同需求的人看到它。

## Windows 预览包与构建

直接从 [GitHub Releases 下载页](https://github.com/shengjidaguai-china/goutoujunshi-jev-chat/releases/latest)下载 Windows 预览 ZIP 文件。构建记录可在 [GitHub Actions 构建页](https://github.com/shengjidaguai-china/goutoujunshi-jev-chat/actions/workflows/platform-build.yml)查看。

| 平台 | 构建产物 | 当前状态 |
| --- | --- | --- |
| Windows | [`goutoujunshi-jev-chat-windows-preview.zip`](https://github.com/shengjidaguai-china/goutoujunshi-jev-chat/releases/latest/download/goutoujunshi-jev-chat-windows-preview.zip) | 可执行目录 ZIP；自动构建通过 |

详细配置与源码开发说明请参阅 [Windows 使用说明](integrations/jev_windows/README.md)。

### 快速使用（解压预编译包）

适用于 Windows 10 (1903及以上) 或 Windows 11，目标聊天应用为微信 Windows 4.x：

1. 下载预览 ZIP，**完整解压**后进入 `goutoujunshi-jev-chat-windows` 文件夹。
2. 运行 `goutoujunshi-jev-chat-windows.exe`（无需另行安装 Python）。
3. 首次打开设置，配置 **Jev 判断接口**和**回复生成接口**。
4. 打开要处理的微信会话，保持聊天窗口可见，使用悬浮窗读取并分析。
5. 生成的候选回复可以一键复制或自动填入草稿箱。填入前请核对会话与收件人，最终由你自己发送。

### 源码运行（开发环境）

在 Windows 系统上克隆仓库并运行：

```cmd
cd integrations\jev_windows
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
python main.py
```

## 界面与工作流

### 悬浮窗与回复生成

1. 打开 Windows 微信中的目标会话，点悬浮球「读取对话」。
2. 窗口自动采集对话文本（基于 RapidOCR），并进行预校对。
3. 调用 Jev 策略判断与回复生成模型，展示对方**可能的意图**、依据与「候选回复排序」。
4. 选择候选回复一键复制，或填入微信**草稿箱**。发送始终由你自己决定。

### 接口与配置

在设置中可分别配置：
- **Jev 判断接口**：用于对对话背景、对方意图与沟通策略进行结构化判断。
- **回复生成接口**：基于判断结果与狗头军师知识库，生成多种风格与不同降压度的候选回复。

密钥保存在当前用户环境变量中（`GOUTOU_JEV_API_KEY` 与 `GOUTOU_LLM_API_KEY`），程序配置文件存放在 `integrations/jev_windows/config.json`。

## 项目特色

- **像自己说话**：只参考当前会话中经过核对、确认为「我」的原话；不训练模型，也不读取其他会话来模仿。
- **把理由讲清楚**：每条候选可展开适用理由和代价；给出建议与注意边界，避免只产出一句话术。
- **控制留给用户**：自动分析默认开启或关闭可调，填入仅写草稿；程序绝不自动替你点击发送。

## 自检与验证

本地环境可以通过以下命令进行自动化测试与规则自检：

```bash
python3 -B scripts/validate_skill.py
PYTHONPATH=. python3 -B -m unittest discover -s tests -q
```

## 许可证与致谢

仓库主体采用 [MIT 许可证](LICENSE)。Windows 界面与组件参考并集成 [Jev Windows](https://github.com/jev-chat/jev-chat-windows) 及 PySide6-Fluent-Widgets，第三方分发注意事项见 [Windows NOTICE](integrations/jev_windows/NOTICE)。

非常感谢 jev-chat-jarvis 项目，从该项目得到启发，结合 goutoujunshi 拓展而来。

联系我加入升级打怪开源群：
Email：247133278@qq.com<br>
WeChat：loonges<br>
QQ：247133278<br>
