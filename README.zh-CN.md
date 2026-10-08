# AirPods 听歌正常、打电话立即掉线：尝试 Standard／标准麦克风模式

[English](README.md) · [Codex skill](airpods-call-disconnect-fix/SKILL.md) · [MIT 许可证](LICENSE)

**如果 AirPods 听歌、刷视频正常，一开始打电话就断开，先检查该通话 App 的麦克风模式，尝试切到 `Standard／标准`。** 2026-10-08，一位使用 **iPhone Air＋AirPods 4、iOS 26.6.2** 的用户在这样修改后，立即确认问题解决。

这是一个用户实测有效的排障案例。具体的 iOS／固件故障机制尚未确定。

## 解决步骤

通话期间打开：**控制中心 → [App] 控制 → 麦克风模式 → Standard／标准**。入口可能显示为 WhatsApp 控制、电话控制，或其他受支持 App 的名称。

**如果戴上耳机就立即掉线，来不及修改：**先把 AirPods 放回充电盒，用 iPhone 本身发起通话，给该 App 选好 Standard，结束通话后重新连接 AirPods 再试。先记下原来的模式，方便恢复。

麦克风模式**按 App 分别保存**。WhatsApp 中改好，不会自动替微信、抖音或普通电话改好；其他会掉线的通话入口也要分别检查。Standard 仍使用正常语音处理，麦克风可以继续收音。上述设置与保存方式有 [Apple 官方说明](https://support.apple.com/zh-cn/101993)。

## 这次问题的完整特征

- AirPods 听歌、刷视频正常。
- 微信、WhatsApp、抖音通话开始时，耳机立即断开。
- 后续测试确认，iPhone 自带的普通电话也立即断开；FaceTime 可以通话。
- 同一副耳机在 MacBook、iPad 上可以打电话。
- 在家里出现，学校和其他一些地点通常正常。
- 从设置里关闭 Wi-Fi，改用 4G／5G，仍然掉线。
- Forget This Device、重新配对、切换蓝牙，都没有解决。
- 故障后蓝牙页面有时显示 Connected，有时显示 Not Connected，但预期的耳机音频输出不可用。
- Wi-Fi、AirDrop、蓝牙图标会一起短暂变化，随后陆续恢复。
- 最后切到 Standard，用户立即反馈问题解决。

## 案例 AP-CALL-001

| 项目 | 已记录信息 |
|---|---|
| 日期 | 2026-10-08 |
| 手机 | iPhone Air |
| 耳机 | AirPods 4；是否为 ANC 版、固件版本未记录 |
| 系统 | iOS 26.6.2；用户回忆此前其他版本也出现过 |
| 有效改动 | 麦克风模式切到 Standard |
| 结果 | 用户立即确认问题解决 |

原先的麦克风模式未记录；修改后每个 App 的独立复测结果和长期观察时间也未记录。因此，这里公开的是一个有效经验，不将某个未知的原模式写成已经确定的原因。

排查时查看了一段用户提供的私有演示视频。约 00:45，Wi-Fi、AirDrop、蓝牙均为蓝色，蓝牙显示 AirPods；约 00:46，三个图标变灰，音乐卡片里的 AirPods 图标消失；约 00:49，Wi-Fi 先恢复；约 00:50，蓝牙、AirDrop 和 AirPods 图标恢复。变化时没有看到用户点击这些连接开关，而且当时的 WhatsApp 来电还没有接听。

这些画面记录了可见的连接状态变化。仅凭画面，无法确定无线服务是否重启或硬件是否故障。公开文档以文字记录相关变化，便于分享这次经验。

## 为什么 FaceTime 正常，其他通话可能失败？

Apple 说明麦克风模式按 App 保存。不同 App 保留不同模式，是值得检查的解释方向；但本案例没有记录各 App 原来的模式，不能把这个解释当成已经证实的底层原因。

这次能够确认的是：**Standard 是成功解决该用户问题的设置改动。** 案例并未证明 Voice Isolation／语音突显、Automatic／自动模式，或某个设备型号普遍存在同一故障。

如果 Standard 有效，可以保留这个设置，再分别检查其他受影响的通话入口。如果仍失败，用另一副蓝牙耳机在同一台 iPhone 上做通话对照，会帮助缩小范围。向客服描述时提供 App、设备、系统和固件版本，以及是否伴随 Wi-Fi／蓝牙／AirDrop 的同步变化。

## 给 Codex 复用

仓库内的 [`airpods-call-disconnect-fix/SKILL.md`](airpods-call-disconnect-fix/SKILL.md) 是自包含的 skill。使用兼容的 Codex skill 安装入口时，选择这个文件夹。

可以这样提问：

> 使用 $airpods-call-disconnect-fix。我的 AirPods 听歌正常，一打微信或 WhatsApp 电话就掉线，请先检查是否符合 Standard 麦克风模式这个案例。

skill 会让 Codex 在症状匹配时优先提出这个小范围对照，同时区分实测解决办法和未确定的故障原因。

## 来源与补充案例

- ✅ 已核验：[Apple 麦克风模式与音频输入官方说明](https://support.apple.com/zh-cn/101993)。支持设置入口及按 App 保存的说明。
- ✅ 已核验：[Apple 英文说明](https://support.apple.com/en-us/101993)。
- AP-CALL-001 来自一位用户的实际排障反馈；Standard 的解决结果由该用户在 2026-10-08 确认。

欢迎通过 GitHub Issue 补充你的设备型号、iOS 和 AirPods 固件版本、App 版本、原麦克风模式（如知道）、切到 Standard 后的结果，以及 FaceTime 和普通电话是否表现不同。连接变化用简短文字描述即可。

检索关键词：AirPods 通话掉线、AirPods 4 打电话断开、iPhone Air 耳机通话、听歌正常打电话没声音、微信耳机掉线、WhatsApp 蓝牙断开、抖音通话断开、FaceTime 正常、Wi-Fi 蓝牙 AirDrop 同时断开、Standard 标准麦克风模式、Voice Isolation 语音突显、iOS 26.6.2。
