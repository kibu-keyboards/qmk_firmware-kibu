# KIBU P75 JIS — 0812 Corresponding Source

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-09-24. Changes: Translated and edited the release overview and customer guidance in English; added a Japanese summary. Original authorship and license notices are retained.

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-10-15. Changes: Updated repository links, the release identity, and publication navigation for the new QMK fork. Firmware, fixed dependencies, the reference BIN, the VIA definition, original authorship, licenses, and earlier modification records are retained.

This release provides the QMK/FS026 source, build dependencies, license notices, and VIA device definition corresponding to the P75 JIS PRE-FIX01 package supplied on August 12, 2026. The release tag is `p75-jis-0812-r1-20261015`.

**No firmware update is required to use this source release.** The included BIN is a reference artifact. VIA configuration requires wired USB; Bluetooth and 2.4 GHz are input connections.

This repository is a KIBU-maintained fork of [QMK Firmware](https://github.com/qmk/qmk_firmware). The `master` branch tracks the upstream snapshot taken when this fork was created; the [`p75-jis` branch](https://github.com/kibu-keyboards/qmk_firmware-kibu/tree/p75-jis) and the release tag contain the fixed P75 JIS source package. Use the tagged package to build this firmware. It is not a port to the current upstream QMK.

**Authorization clarification (October 15, 2026):** [Current source and license notice](docs/SOURCE_AND_LICENSES.md) applies the signed manufacturer agreement to the delivered P75 package, including necessary FS026 build files. It supersedes blanket authorization-pending wording in the historical release documentation. Firmware and release downloads are unchanged. [Installation instructions for modified builds](docs/INSTALLING_FIRMWARE.md) are now documented.

## Downloads and setup

- [Release files](https://github.com/kibu-keyboards/qmk_firmware-kibu/releases/tag/p75-jis-0812-r1-20261015): `KIBU-P75-JIS-0812-r1-20261015-source.zip`, the matching `kibu_p75_jis_via_pre_fix01.json`, and `SHA256SUMS.txt`.
- [VIA setup](docs/VIA_GUIDE.md): connect over USB and load the supplied device definition manually.
- [Install modified firmware](docs/INSTALLING_FIRMWARE.md): save settings, write your BIN over USB, or return to the published baseline.
- [Tagged source](https://github.com/kibu-keyboards/qmk_firmware-kibu/tree/p75-jis-0812-r1-20261015) and [exact checkout instructions](docs/GIT_IMPORT.md).
- [Build workflow](https://github.com/kibu-keyboards/qmk_firmware-kibu/actions/workflows/p75-0812.yml): see the run for the release commit.

## Source and documentation

The [firmware source](qmk_firmware/) includes USB input and the FS026-side SPI bridge for Bluetooth and 2.4 GHz operation. ChibiOS, ChibiOS-Contrib, and FS026 platform sources are included as fixed files. Internal firmware for the separate 91680 wireless controller is outside this package; see [source and licenses](docs/SOURCE_AND_LICENSES.md) for component provenance and license details.

| Reference | Contents |
| --- | --- |
| [Build instructions](docs/BUILD.md) | Toolchain, fixed dependencies, and reproducible build procedure. |
| [Version reference](docs/VERSION_AND_TESTS.md) | Baseline, artifact hashes, and device identifiers. |
| [Known issues](docs/KNOWN_ISSUES.md) | Reliability risks in the PRE-FIX01 baseline. |
| [Release notes](docs/RELEASE_NOTES.md) | Release scope and downloads. |
| [Reference BIN](artifacts/kibu_p75_jis_pre_fix01_hardware_validated.bin) and [VIA definition](artifacts/kibu_p75_jis_via_pre_fix01.json) | Firmware reference and matching device definition. |

## Support

Contact [KIBU support](https://kibushop.com/pages/contact) or [m@kibushop.com](mailto:m@kibushop.com). Include the model, connection mode, firmware and definition versions, and steps to reproduce the issue.

## 日本語

本リリースは、KIBU P75 JISの0812版PRE-FIX01に対応するQMK／FS026側のソースコード、ビルド依存ファイル、ライセンス表示、およびVIAデバイス定義を提供します。`KIBU-P75-JIS-0812-r1-20261015-source.zip` と付属のチェックサムをご利用ください。VIAの設定はUSB有線接続で行い、指定のJSONを手動で読み込みます。本資料の利用に伴うファームウェア更新は不要です。USB入力とBluetooth／2.4 GHz用のFS026側通信処理を含みますが、別体の91680無線コントローラー内部ファームウェアは公開範囲外です。ビルド方法、バージョン情報、ライセンス、既知の問題は上記の各資料をご参照ください。お問い合わせは、機種名、接続方式、使用バージョン、再現手順を添えて [KIBUサポート](https://kibushop.com/pages/contact) または [m@kibushop.com](mailto:m@kibushop.com) へお願いいたします。

変更記録：KIBU（kibu-keyboards、M@kibu.jp）が2026年9月24日に本資料の英訳・編集および日本語案内の追加を行いました。原著者の表記、著作権表示、ライセンス表示は保持しています。

公開先の変更：2026年10月15日、KIBUの新しいQMK forkへ配布先を変更しました。対象は0812版の対応ソースコードで、ファームウェア、固定依存ファイル、参照用BIN、VIA定義は変更していません。原著者・著作権・ライセンス表示および既存の変更記録を保持しています。P75 JISには上記のタグ付き配布物をご利用ください。

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-10-15. Changes: Linked the signed-agreement clarification and installation instructions. Firmware, release artifacts and existing notices are unchanged.
>
> 変更記録：KIBUが2026年10月15日に締結済み契約に基づく許諾範囲の訂正と、変更版の書き込み手順への案内を追加しました。過去の配布文書にある包括的な許諾待ちの記述は、上記の現行説明に訂正しています。ファームウェア、配布物、既存の表示は変更していません。

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-10-15. Changes: Added direct navigation to the customer firmware installation guide. Firmware, release artifacts, and existing notices retained.
>
> 変更記録：KIBUが2026年10月15日に[お客様向け変更版ファームウェアの書き込み手順](docs/INSTALLING_FIRMWARE.md)への案内を追加しました。設定の保存、USB経由の書き込み、公開版への復旧を説明しています。通常のVIAキー設定に書き込みは不要です。ファームウェア、配布物と既存の表示は保持しています。
