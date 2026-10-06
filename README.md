# 青简安卓移植版（非官方）

把 [qingjian-team/qingjian](https://github.com/qingjian-team/qingjian)（Rust 写的拼音输入法「青简」）移植到 Android 的**爱好者非官方移植版**。原仓库只提供 macOS / Windows / Linux 版，这里是全新编写的 Android 输入法 App，通过 JNI 调用原仓库的 `qingjian-core` 引擎。

> **声明**：本移植版与 qingjian-team 官方无关；使用中遇到问题请勿打扰原作者。「青简」项目名称与官方 logo 的商标权归原作者所有，不包含在代码授权中，本移植版仅作非商业学习交流使用。

- 上游版本：`qingjian-team/qingjian` @ `c08ae57`（2026-10-05）
- 本移植版：v0.1.0，包名 `app.qingjian.ime`，仅 arm64-v8a

## 功能（v0.1.0）

- 全拼输入、候选词、候选旁译词（英语 / 日语 / 西班牙语 / 关闭，可在设置里切换）
- 词频学习（落盘到应用私有目录）、emoji 候选
- 自绘 QWERTY 键盘：大小写切换、符号页、退格连删、中/英切换
- 纯离线：不联网、不收集任何数据

首版裁剪：无整句语言模型、无云联想、无双拼 / 五笔 / 注音、无滑动输入。

## 构建

源码与构建脚本见本仓库 release 附带的源码包。构建需要：Rust（见 `jni/rust-toolchain.toml`）+ `aarch64-linux-android` target、Android SDK（platform android-34、build-tools 34.0.0、NDK r27）、JDK 17、kotlinc。把上游仓库 clone 到 `jni/` 同级并命名为 `repo/`，按 `build-apk.sh` 开头改好路径后直接运行即可。keystore 请自行生成并妥善保管，切勿提交到仓库。

## 许可

- 代码 GPL-3.0-or-later（与上游一致）；APK 内 `assets/qingjian-data/NOTICES.txt` 列出随包数据第三方许可与署名。
- 随包数据：词库字频（THUOCL，MIT）、汉字读音与 emoji（Unicode License v3）、英文词表（ESDB，Kevin Atkinson 署名要求）、误拼/术语表（typos、cspell，MIT）。
