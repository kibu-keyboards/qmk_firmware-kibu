# KIBU P75 JIS — Downloads and setup

This is KIBU's fork of QMK Firmware. **For P75 JIS, use the 0812 PRE-FIX01 source release and matching VIA definition below.** The upstream QMK files on this `master` branch are reference material; the P75 source and fixed build dependencies are in the tagged release.

| What you need | Direct link |
| --- | --- |
| Complete P75 JIS source package with fixed dependencies | [Download source ZIP](https://github.com/kibu-keyboards/qmk_firmware-kibu/releases/download/p75-jis-0812-r1-20261015/KIBU-P75-JIS-0812-r1-20261015-source.zip) · [Browse tagged source](https://github.com/kibu-keyboards/qmk_firmware-kibu/tree/p75-jis-0812-r1-20261015/qmk_firmware) |
| Matching VIA device definition | [Download VIA JSON](https://github.com/kibu-keyboards/qmk_firmware-kibu/releases/download/p75-jis-0812-r1-20261015/kibu_p75_jis_via_pre_fix01.json) |
| Configuration instructions | [VIA setup guide — USB connection and manual JSON loading](https://github.com/kibu-keyboards/qmk_firmware-kibu/blob/p75-jis-0812-r1-20261015/docs/VIA_GUIDE.md) |
| Build instructions and version | [Build the fixed source](https://github.com/kibu-keyboards/qmk_firmware-kibu/blob/453be76d41336997d0566f4dac47ac4ba8a2ca98/docs/BUILD.md) · [Version and device identifiers](https://github.com/kibu-keyboards/qmk_firmware-kibu/blob/p75-jis-0812-r1-20261015/docs/VERSION_AND_TESTS.md) |
| Release files and checksums | [P75 JIS release](https://github.com/kibu-keyboards/qmk_firmware-kibu/releases/tag/p75-jis-0812-r1-20261015) · [SHA256SUMS.txt](https://github.com/kibu-keyboards/qmk_firmware-kibu/releases/download/p75-jis-0812-r1-20261015/SHA256SUMS.txt) |
| License information and known issues | [Source and licenses](https://github.com/kibu-keyboards/qmk_firmware-kibu/blob/453be76d41336997d0566f4dac47ac4ba8a2ca98/docs/SOURCE_AND_LICENSES.md) · [Known issues](https://github.com/kibu-keyboards/qmk_firmware-kibu/blob/p75-jis-0812-r1-20261015/docs/KNOWN_ISSUES.md) |

**VIA configuration uses wired USB.** Bluetooth and 2.4 GHz are input connections. No firmware update is required solely to use this source release or setup guide. Load the linked external VIA JSON; do not use the historical JSON embedded in the source tree. Manual loading does not imply inclusion in VIA's official device database.

The source package includes the QMK/FS026 firmware and Bluetooth/2.4 GHz bridge code. Internal firmware for the separate 91680 wireless controller is outside the package. This fork is maintained by KIBU and is not an upstream QMK product-support commitment. Contact [KIBU support](https://kibushop.com/pages/contact) or [m@kibushop.com](mailto:m@kibushop.com).

**Authorization clarification — October 15, 2026:** The [current source and license notice](https://github.com/kibu-keyboards/qmk_firmware-kibu/blob/453be76d41336997d0566f4dac47ac4ba8a2ca98/docs/SOURCE_AND_LICENSES.md) applies the signed manufacturer agreement to the delivered P75 package, including necessary FS026 build files, and supersedes blanket authorization-pending wording in historical documentation. [Installation of modified builds](https://github.com/kibu-keyboards/qmk_firmware-kibu/blob/453be76d41336997d0566f4dac47ac4ba8a2ca98/docs/BUILD.md#installing-a-locally-modified-build-p75-jis) is documented. Firmware, the release tag, and download files are unchanged.

**許諾範囲の訂正（2026年10月15日）：** 締結済み契約に基づく[現行の許諾・ライセンス説明](https://github.com/kibu-keyboards/qmk_firmware-kibu/blob/453be76d41336997d0566f4dac47ac4ba8a2ca98/docs/SOURCE_AND_LICENSES.md)をご参照ください。正式納品済みのQMK側コードと必要なFS026ビルドファイルを対象とし、過去の配布文書にある包括的な許諾待ちの記述を訂正しています。変更版の書き込み手順も追記しました。ファームウェア、リリースタグ、配布ファイルは変更していません。

## 日本語

P75 JISをご利用の方は、上表の[ソースZIP](https://github.com/kibu-keyboards/qmk_firmware-kibu/releases/download/p75-jis-0812-r1-20261015/KIBU-P75-JIS-0812-r1-20261015-source.zip)、[VIA定義JSON](https://github.com/kibu-keyboards/qmk_firmware-kibu/releases/download/p75-jis-0812-r1-20261015/kibu_p75_jis_via_pre_fix01.json)、[設定手順](https://github.com/kibu-keyboards/qmk_firmware-kibu/blob/p75-jis-0812-r1-20261015/docs/VIA_GUIDE.md)をご利用ください。対象は0812版PRE-FIX01です。VIA設定はUSB有線接続で行い、指定の外部JSONを手動で読み込みます。ソース内の旧JSONは使用しないでください。Bluetooth／2.4 GHzは入力用です。本資料の利用だけを目的としたファームウェア更新は不要で、VIA公式データベースへの登録を意味しません。FS026側の無線通信処理を含みますが、別体の91680内部ファームウェアは対象外です。以下のmaster内のQMK資料とP75用の固定ソースを区別し、お問い合わせはKIBUへお願いいたします。

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-10-15. Changes: Added P75 JIS customer download and setup navigation above the upstream README. The original README bytes, authorship and license notices are retained below.
>
> 変更記録：KIBU（kibu-keyboards、M@kibu.jp）が2026年10月15日にP75 JISのダウンロード・設定案内を追加しました。以下の上流README、原著者およびライセンス表示は保持しています。

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-10-15. Changes: Linked the signed-agreement clarification and installation guidance; upstream README bytes and original notices retained.
>
> 変更記録：KIBUが2026年10月15日に締結済み契約の適用範囲の訂正と書き込み手順への案内を追加しました。以下の上流READMEと既存の表示は保持しています。

---

# Quantum Mechanical Keyboard Firmware

[![Current Version](https://img.shields.io/github/tag/qmk/qmk_firmware.svg)](https://github.com/qmk/qmk_firmware/tags)
[![Discord](https://img.shields.io/discord/440868230475677696.svg)](https://discord.gg/qmk)
[![Docs Status](https://img.shields.io/badge/docs-ready-orange.svg)](https://docs.qmk.fm)
[![GitHub contributors](https://img.shields.io/github/contributors/qmk/qmk_firmware.svg)](https://github.com/qmk/qmk_firmware/pulse/monthly)
[![GitHub forks](https://img.shields.io/github/forks/qmk/qmk_firmware.svg?style=social&label=Fork)](https://github.com/qmk/qmk_firmware/)

This is a keyboard firmware based on the [tmk\_keyboard firmware](https://github.com/tmk/tmk_keyboard) with some useful features for Atmel AVR and ARM controllers, and more specifically, the [OLKB product line](https://olkb.com), the [ErgoDox EZ](https://ergodox-ez.com) keyboard, and the Clueboard product line.

## Documentation

* [See the official documentation on docs.qmk.fm](https://docs.qmk.fm)

The docs are powered by [VitePress](https://vitepress.dev/). They are also viewable offline; see [Previewing the Documentation](https://docs.qmk.fm/#/contributing?id=previewing-the-documentation) for more details.

You can request changes by making a fork and opening a [pull request](https://github.com/qmk/qmk_firmware/pulls).

## Supported Keyboards

* [Planck](/keyboards/planck/)
* [Preonic](/keyboards/preonic/)
* [ErgoDox EZ](/keyboards/ergodox_ez/)
* [Clueboard](/keyboards/clueboard/)
* [Cluepad](/keyboards/clueboard/17/)
* [Atreus](/keyboards/atreus/)

The project also includes community support for [lots of other keyboards](/keyboards/).

## Maintainers

QMK is developed and maintained by Jack Humbert of OLKB with contributions from the community, and of course, [Hasu](https://github.com/tmk). The OLKB product firmwares are maintained by [Jack Humbert](https://github.com/jackhumbert), the Ergodox EZ by [ZSA Technology Labs](https://github.com/zsa), the Clueboard by [Zach White](https://github.com/skullydazed), and the Atreus by [Phil Hagelberg](https://github.com/technomancy).

## Official Website

[qmk.fm](https://qmk.fm) is the official website of QMK, where you can find links to this page, the documentation, and the keyboards supported by QMK.
