# Source Provenance and License Notices

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-09-24. Changes: Translated and clarified the English provenance and component-license documentation. Original authorship and license notices are retained.

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-10-15. Changes: Applied the confirmed signed agreement to the delivered P75 scope and corrected obsolete authorization-pending statements. Original notices and the recovery history are retained.

## Baseline and scope

This package derives from `qmk_firmware_pre_fix01_exact_source_20260807.zip`, SHA-256 `B5432FB8B39ADFD91D3196C08056C09BC3D90542B151631B6AFB9C87A8119846`, supplied with the August 12, 2026 PRE-FIX01 package.

The publication copy includes attribution and documentation/comment updates and excludes unusable Git pointer files. Executable code is unchanged; the publication ZIP is not byte-identical to the original archive. A production Git commit and complete dependency Git revisions have not been established. Dependencies are provided as fixed files.

The [QMK/FS026 source](../qmk_firmware/) includes product code, platform support, USB input, the SPI protocol, and Bluetooth/2.4 GHz mode and report bridging. Internal firmware for the separate 91680 wireless controller is not included and has not been audited. The source release covers the FS026 firmware, not every firmware component in the keyboard.

## Authorization for the delivered P75 package

The signed manufacturer agreement, in the October 10, 2026 revision confirmed by KIBU, covers formally delivered KIBU QMK-side source, custom code, configuration, interface code, and necessary build files. Previously delivered packages are included automatically under its delivery-scope clause; this includes the 0812 package identified above. The agreement also permits provision to and publication by KIBU株式会社.

For portions the supplier owns or is authorized to license, the agreement grants public release under **GPL-2.0-or-later**, including modification, redistribution, and commercial use. This covers the delivered product-specific code and accompanying configuration/VIA definition within that scope. Necessary FS026 build files are included; they do not require a separate script authorization. Existing third-party licenses remain applicable to their respective components rather than being replaced by the supplier's grant.

This clarification supersedes the earlier blanket statements that product changes, the VIA JSON, and the supplied FS026 build files were awaiting authorization. It applies to the same source baseline; executable source, dependencies, the reference BIN, and the VIA definition are unchanged. Earlier tags and downloadable archives retain their historical documentation.

## Retained authorship and notices

| Component | Notices and treatment |
| --- | --- |
| QMK | Retain the [GPL v2 text](../qmk_firmware/LICENSE) and each file's copyright/license notices. Individual component declarations remain authoritative. |
| P75 product code and VIA definition | The supplier's own or authorized delivered portions are covered by the signed GPL-2.0-or-later grant above. Retain existing Finalkey, LiWenLiu, Yiancar, and other author notices. |
| P75 encoder excerpts | Four excerpts correspond to the bundled [encoder_quadrature.c](../qmk_firmware/drivers/encoder/encoder_quadrature.c). Attribution to Jack Humbert (2018), Nick Brassel (2018–2023), and the GPL-2.0-or-later source was added while retaining the product authors. |
| ChibiOS | Retain the [original license information](../qmk_firmware/lib/chibios/license.txt), file headers, and accompanying notices, including the GPLv3 declarations in ChibiOS/RT. |
| ChibiOS-Contrib / FS026 | Retain the [Contrib documentation](../qmk_firmware/lib/chibios-contrib/README.md), Apache notices, and other file-level licenses. The supplied necessary build files fall within the agreement's delivery scope, subject to existing third-party rights. |
| rdr_common | The [C implementation](../qmk_firmware/lib/rdr_lib/rdr_common.c) carries GPL-2.0-or-later. The supplier's own or authorized delivered integration is covered by the agreement; retain original notices and the recovery history below. |

This document does not replace original license texts or reattribute the package to KIBU. All existing copyright and license notices are retained. A missing per-file SPDX identifier is not, by itself, evidence that the signed grant does not apply. The FS026 GPIO files retain their existing Apache-2.0 text and year-only copyright line; no author name has been invented.

## rdr recovery and reimplementation

`lib/rdr_lib/rdr_common.c` is a recovered/reimplemented C replacement for `librdrcommon.a`, compiled directly from source. It covers QMK report forwarding, wireless-controller SPI communication, mode/pairing commands, battery and power handling, USB suspend/wake, and persistence. It is not a newly obtained copy of the manufacturer's original C source. The published build uses this C implementation, not the former private archive or object.

The signed agreement supplies the authorization basis for the supplier's own or authorized delivered portions. Recovery history remains a provenance fact; it is not a separate outstanding request for permission to publish those covered portions. The agreement does not override another rights holder's license.

See the bundled [reimplementation record](../qmk_firmware/REIMPLEMENTATION_STATUS.md), [implementation notes](../qmk_firmware/lib/rdr_lib/README.md), and [static verification record](../qmk_firmware/VERIFICATION.txt) for technical background. Build and installation instructions are in [BUILD.md](BUILD.md).

## Current scope and limitations

The review of the published FS026 build has not identified a specific missing product source/archive, a supplier-disclosed exclusion affecting a required file, or an incompatible third-party license requiring an outstanding authorization request. This is a conclusion about the reviewed package, not a claim that the supplier can relicense all third-party code.

The separate 91680 firmware remains outside the reviewed source scope described above. Fixed dependency files are supplied even where their original Git revisions are unknown. [Known reliability issues](KNOWN_ISSUES.md) and the [recorded test coverage](VERSION_AND_TESTS.md), including untested 2.4 GHz operation, remain documented. These limitations are not described as missing permission for the covered files.

## 日本語

2026年10月10日改訂版の締結済み契約に基づき、正式納品されたQMK側ソース、製品固有コード、設定・VIA定義、インターフェース、および必要なFS026ビルドファイルについて、供給者が権利を有する部分または許諾権限を有する部分をGPL-2.0-or-laterで公開します。既に正式納品された0812パッケージも対象であり、KIBU株式会社への提供・公開が認められています。第三者のコードには各々の元のライセンスが適用され、著作権表示とライセンス表示を保持します。

製品コード、JSON、FS026ビルドファイルを一律に「許諾確認待ち」としていた旧説明を訂正しました。rdrの復元・再実装という来歴、91680内部ファームウェアの対象範囲、既知の不具合、および未実施の2.4 GHz試験は引き続き明示します。実行コード、依存ファイル、参照用BIN、VIA定義、既存のタグと配布アーカイブは変更していません。過去の配布物に含まれる包括的な許諾待ちの記述については、本説明をご参照ください。

変更記録：KIBU（kibu-keyboards、M@kibu.jp）が2026年10月15日に締結済み契約の適用範囲と第三者ライセンスの扱いを明確化しました。原著者・著作権・ライセンス表示および既存の変更記録は保持しています。
