<!-- README_SYNC: source=working-tree; updated=2026-09-26 -->

<p align="center"><a href="./README.md">简体中文</a> · English</p>

# Goutoujunshi Jev Chat

**Goutoujunshi beside your chat window: screen reading, analysis, and reply drafts.** This standalone project builds on [Goutoujunshi](https://github.com/shengjidaguai-china/goutoujunshi). The primary operating environment is Windows (supporting Windows 10/11 and WeChat for Windows 4.x). It supports window chat text capture, Jev strategy judgment, and reply candidate drafting. You decide whether to send every draft.

If it helps you, [Star the project](https://github.com/shengjidaguai-china/goutoujunshi-jev-chat/stargazers) so you can find it again and help others discover it.

## Windows Preview Package

Download the file for Windows from [GitHub Releases](https://github.com/shengjidaguai-china/goutoujunshi-jev-chat/releases/latest). Extract the full Windows ZIP before launching its executable. Build logs are available on the [GitHub Actions build page](https://github.com/shengjidaguai-china/goutoujunshi-jev-chat/actions/workflows/platform-build.yml).

| Platform | Artifact | Current status |
| --- | --- | --- |
| Windows | [`goutoujunshi-jev-chat-windows-preview.zip`](https://github.com/shengjidaguai-china/goutoujunshi-jev-chat/releases/latest/download/goutoujunshi-jev-chat-windows-preview.zip) | Executable-directory ZIP. Automated build passes. |

For detailed setup and source running instructions, see the [Windows guide](integrations/jev_windows/README.md).

### Quick Start (Pre-compiled ZIP)

Requires Windows 10 version 1903 or later, or Windows 11, with WeChat for Windows 4.x:

1. Download the preview ZIP, **extract the entire archive**, open the `goutoujunshi-jev-chat-windows` folder.
2. Run `goutoujunshi-jev-chat-windows.exe` (no Python installation required).
3. In Settings, configure the **Jev judgment** and **reply generation** endpoints separately.
4. Open the intended WeChat conversation and keep the window visible, then use the floating window to capture and analyze.
5. Copy candidates or fill them into drafts. Verify the conversation and recipient before sending drafts yourself.

### Run from Source

To run from source on Windows:

```cmd
cd integrations\jev_windows
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
python main.py
```

## Features and Workflow

- **Replies in your style:** It uses only verified messages attributed to you in the current conversation.
- **Clear reasons:** Expand candidate replies to inspect reasons, trade-offs, and boundary warnings.
- **Human control:** Capture and analysis are user-controlled, and candidate filling inserts into draft input only. The app never presses Send for you.

## Self-Check and Verification

To perform local checks and test suite validation:

```bash
python3 -B scripts/validate_skill.py
PYTHONPATH=. python3 -B -m unittest discover -s tests -q
```

## License and Acknowledgments

The main repository is licensed under the [MIT License](LICENSE). The Windows UI component incorporates [Jev Windows](https://github.com/jev-chat/jev-chat-windows) and PySide6-Fluent-Widgets; see [Windows NOTICE](integrations/jev_windows/NOTICE) for redistribution terms.

Special thanks to the jev-chat-jarvis project for inspiration.
