# P75 JIS — Installing Modified Firmware

> Written by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-10-15. Changes: Added customer instructions for installing a modified P75 JIS build and returning to the published 0812 baseline. Existing authorship, copyright, license notices, and earlier modification records are retained.

Use this guide when you choose to install firmware built from the **P75 JIS 0812 PRE-FIX01 source**. Ordinary VIA remapping does not require a firmware update. The steps below use Windows File Explorer and the keyboard's USB bootloader, a small program that accepts a firmware BIN file.

## 1. Prepare the files and save your settings

- Use a **KIBU P75 JIS** matching this source package, a computer, and a USB cable that supports data transfer. These instructions are for the keyboard's FS026 firmware. Do not use this BIN for another keyboard, the wireless controller, or a USB receiver.
- Save your current keymap with VIA. Record macros and lighting or other settings separately if they are not included in your export. Entering the bootloader or installing a different build can reset settings; saving the firmware file alone does not save your personal settings.
- Keep both your modified BIN and a copy of the [published reference BIN](https://raw.githubusercontent.com/kibu-keyboards/qmk_firmware-kibu/376f7618b9e785aa09fe2e7b125205322951760a/artifacts/kibu_p75_jis_pre_fix01_hardware_validated.bin) on your computer. Download the reference through this link or open its [GitHub file page](../artifacts/kibu_p75_jis_pre_fix01_hardware_validated.bin) and choose **Download raw file**. It is also included in the [source release ZIP](https://github.com/kibu-keyboards/qmk_firmware-kibu/releases/tag/p75-jis-0812-r1-20261015).

| File | Purpose |
| --- | --- |
| Your build output: `p75_jis_p75_jis_via.bin` | The modified firmware to copy to the keyboard's bootloader drive. |
| `kibu_p75_jis_pre_fix01_hardware_validated.bin` | The published 0812 reference firmware, for returning to that baseline. It does not restore your personal settings or every component of the keyboard. |
| `kibu_p75_jis_via_pre_fix01.json` | The VIA device definition, loaded in VIA after installation. It is not firmware or a backup of your settings. |

Copy only the intended **`.bin`** file to the keyboard. Do not copy a ZIP, JSON, HEX, ELF, or GitHub web page to the bootloader drive.

### If you are building the modified firmware yourself

Follow the [manual build instructions](BUILD.md#manual-build) for the required tools and environment. Start with the fixed P75 source package and target `p75_jis/p75_jis:via`. After editing the source, run the following from the package root in the configured Bash environment:

```bash
P75_BUILD_DIR=.build_custom_01 bash tools/build.sh
```

The output is `qmk_firmware/.build_custom_01/p75_jis_p75_jis_via.bin`. Use a new build-directory name for each attempt, such as `.build_custom_02`; the script stops if that directory already exists. Continue only after the build finishes successfully and produces the BIN.

`tools/ci-build.ps1` is an unchanged-baseline reproduction check: it expects the original BIN's size and hash and will report a mismatch for a changed image. Use the manual build path for modifications. Your modified BIN normally has a different SHA-256 from the reference; do not change or reuse the reference checksum to label a modified build. Keep the default build date unless changing it deliberately, because a different date can reset VIA keymaps and macros. See [build-date behavior](BUILD.md#why-the-build-date-is-fixed).

## 2. Open the keyboard's bootloader drive

1. Close VIA and any other keyboard configuration application.
2. Select **wired USB mode** on the keyboard, then disconnect its USB cable.
3. Hold **Esc** on the keyboard while connecting the USB data cable to the computer.
4. When a new removable drive appears in **File Explorer → This PC**, release Esc.

The drive name and letter can vary. Identify the drive that appeared when this keyboard entered the bootloader; do not assume a particular letter such as `E:`. The keyboard's normal typing interface is unavailable while it is in the bootloader. Keep your own firmware files; do not rely on the bootloader drive for a backup of the installed firmware.

## 3. Copy the BIN and wait for restart

1. In File Explorer, select the modified `p75_jis_p75_jis_via.bin` saved on your computer.
2. Copy that one BIN file into the **top level of the keyboard's bootloader drive**. Do not put it inside a folder.
3. Keep the USB cable connected and wait for programming and the keyboard's automatic restart to finish. Do not format the drive, disconnect power, or copy another firmware file while programming.
4. After the keyboard restarts, its normal USB typing interface should return. The temporary bootloader drive may disappear; this is expected during restart.

If the drive remains visible and the keyboard does not restart, leave it connected and use the troubleshooting guidance below. Do not assume that the end of the file-copy dialog alone proves programming has finished.

## 4. Check input and restore compatible settings

Test normal typing over USB before opening VIA. If your modifications preserve the baseline VIA protocol, layout, and custom keycodes, load the [matching VIA JSON](../artifacts/kibu_p75_jis_via_pre_fix01.json) using the [VIA setup guide](VIA_GUIDE.md), then restore your saved settings and check them. If your changes alter those interfaces, use a definition that matches your modified firmware; do not force the baseline JSON or an incompatible backup onto it.

Check each connection mode and feature you intend to use. VIA configuration uses wired USB; Bluetooth and 2.4 GHz are input connections. Successful copying or USB typing alone does not establish that every function of a modified build works. The published baseline's [known issues](KNOWN_ISSUES.md) also remain relevant unless your changes address them.

## Return to the published 0812 baseline

If a modified build starts but does not work as expected, repeat steps 2–4 using `kibu_p75_jis_pre_fix01_hardware_validated.bin` instead of your modified BIN. Do this only after any previous programming has finished. The reference file is **80,860 bytes** and its SHA-256 is:

```text
21DE5AAFA6684B72AD797C47C61712F8D40F5762477DCBA483DC7BB53A4332B2
```

To check the reference download on Windows, open PowerShell in the folder containing it and run:

```powershell
Get-FileHash -LiteralPath .\kibu_p75_jis_pre_fix01_hardware_validated.bin -Algorithm SHA256
```

The returned hash must match the value above. This checksum is for the reference BIN only. Returning to the reference installs the published FS026 baseline; it does not recreate an earlier personal configuration, restore an unknown factory image, or reprogram the separate wireless controller or receiver. Restore compatible settings separately.

## Troubleshooting and support

| What you see | What to do |
| --- | --- |
| No bootloader drive appears, and no programming has started | Confirm wired mode, use a data-capable cable and another direct USB port, then repeat the Esc connection procedure. If the drive still does not appear, contact KIBU. |
| Windows asks to format the drive, or copying reports an error | Do not format it or keep retrying firmware copies. Leave the keyboard connected if programming may be in progress and contact KIBU. |
| The copy dialog closes, but the drive stays visible and the keyboard never restarts | Leave the keyboard connected. Do not disconnect power or repeatedly copy files while programming status is uncertain. Contact KIBU. |
| The keyboard restarts, but the modified firmware does not type correctly | If programming is complete and the Esc bootloader remains accessible, install the reference BIN using the steps above. If the bootloader cannot be opened, contact KIBU. |
| USB typing works, but VIA does not recognize the keyboard | Use wired mode, load the definition matching the installed firmware, and check browser device permission. Follow the VIA guide; reflashing is not the first troubleshooting step. |

Contact [KIBU support](https://kibushop.com/pages/contact) or [m@kibushop.com](mailto:m@kibushop.com). Include the model, source revision and build target, BIN filename and SHA-256 if available, the step where the problem occurred, and whether the keyboard appears as a bootloader drive or a normal USB keyboard. Keep your modified source and build log for troubleshooting. Customer modifications can change behavior beyond the published baseline.

## 日本語：P75 JISの変更版ファームウェアを書き込む

本手順は、**P75 JISの0812版PRE-FIX01ソース**から作成した変更版を、ご自身の判断でインストールする場合の説明です。通常のVIAによるキー変更にファームウェア更新は不要です。Windowsのエクスプローラーと、BINファイルを受け付けるキーボード内のUSBブートローダーを使用します。

### 1. ファイルと設定を準備する

対応するKIBU P75 JIS、パソコン、データ通信対応USBケーブルをご用意ください。書き込む対象はキーボードのFS026側です。他機種、無線コントローラー、USBレシーバーには使用しないでください。

VIAで現在のキーマップを保存し、エクスポートに含まれないマクロ、照明などの設定は別途記録してください。ブートローダーへの移行やビルドの変更によって、設定が初期化される場合があります。BINの保存だけでは個人設定のバックアップになりません。

変更版の`p75_jis_p75_jis_via.bin`と、復旧用の[公開版参照BIN](https://raw.githubusercontent.com/kibu-keyboards/qmk_firmware-kibu/376f7618b9e785aa09fe2e7b125205322951760a/artifacts/kibu_p75_jis_pre_fix01_hardware_validated.bin)をパソコンに保存してください。GitHubのファイルページを使う場合は **Download raw file** で実ファイルをダウンロードします。参照BINはソース配布ZIPにも含まれます。`kibu_p75_jis_via_pre_fix01.json`はVIA用のデバイス定義であり、ファームウェアや個人設定のバックアップではありません。キーボードへコピーするのは対象の**BIN一つだけ**です。ZIP、JSON、HEX、ELF、Webページはコピーしないでください。

ご自身でビルドする場合は、[手動ビルド手順](BUILD.md#manual-build)に従って環境を準備し、ソースの変更後にパッケージのルートで次を実行します。

```bash
P75_BUILD_DIR=.build_custom_01 bash tools/build.sh
```

出力は`qmk_firmware/.build_custom_01/p75_jis_p75_jis_via.bin`です。再試行時は`.build_custom_02`など未使用の出力先を指定し、ビルドが正常に完了したことを確認してください。`tools/ci-build.ps1`は未変更版の再現確認用であり、変更版のサイズ・ハッシュが元と異なれば不一致になります。変更版には手動ビルドを使用し、元のチェックサムを変更版の識別に流用しないでください。ビルド日付の変更はVIAのキーマップやマクロを初期化する原因になるため、意図して変更する場合を除き既定値を維持してください。

### 2. ブートローダーのドライブを開く

1. VIAなどのキーボード設定アプリを閉じます。
2. キーボードを**USB有線モード**に切り替え、USBケーブルを外します。
3. キーボードの**Escを押しながら**USBデータケーブルをパソコンへ接続します。
4. **エクスプローラー → PC**に新しいリムーバブルドライブが表示されたらEscを離します。

ドライブ名や文字は環境によって異なります。`E:`などに決めつけず、今回の操作で追加されたキーボードのドライブを確認してください。ブートローダー動作中は通常のキー入力が使えません。元のファームウェアファイルはご自身で保管し、ブートローダー用ドライブをインストール済みファームウェアのバックアップ手段として使用しないでください。

### 3. BINをコピーして再起動を待つ

1. パソコンに保存した変更版の`p75_jis_p75_jis_via.bin`を選びます。
2. キーボードのブートローダー用ドライブの**直下**へ、そのBIN一つをコピーします。フォルダー内には入れません。
3. USBを接続したまま、書き込みとキーボードの自動再起動が完了するまで待ちます。ドライブをフォーマットせず、電源を切ったり別のBINをコピーしたりしないでください。
4. 再起動後に通常のUSBキーボードとして戻ることを確認します。再起動時に一時的なドライブが消えることがあります。

コピー画面が閉じただけでは書き込み完了を断定できません。ドライブが残ったまま再起動しない場合は、接続を維持し、追加コピーや電源の切断をせずKIBUへお問い合わせください。

### 4. 入力とVIA設定を確認する

まずUSBで通常の文字入力を確認します。変更版が元のVIAプロトコル、配列、カスタムキーコードを維持している場合は、[VIA設定手順](VIA_GUIDE.md)に従って対応するJSONを読み込み、保存済み設定を復元して確認してください。それらの仕様を変更した場合は、変更版に合う定義を使用し、元のJSONや互換性のないバックアップを無理に読み込まないでください。

利用する接続モードや機能をそれぞれ確認します。VIA設定はUSB接続のみで行い、Bluetooth／2.4 GHzは入力用です。コピー成功やUSB入力だけで変更版の全機能の動作が確認できたことにはなりません。変更で対処していない[公開版の既知の問題](KNOWN_ISSUES.md)も引き続き該当します。

### 公開0812版へ戻す

変更版で正常に動作しない場合は、前の書き込みが完了していることを確認したうえで、`kibu_p75_jis_pre_fix01_hardware_validated.bin`を使用して手順2～4を繰り返します。参照BINは**80,860バイト**で、SHA-256は次の値に一致します。

```text
21DE5AAFA6684B72AD797C47C61712F8D40F5762477DCBA483DC7BB53A4332B2
```

参照BINを保存したフォルダーでPowerShellを開き、次のコマンドで確認できます。

```powershell
Get-FileHash -LiteralPath .\kibu_p75_jis_pre_fix01_hardware_validated.bin -Algorithm SHA256
```

このチェックサムは参照BIN専用です。変更版のハッシュがこの値と異なること自体は異常ではありません。

公開版への復旧はFS026側を公開0812基準へ戻す操作です。以前の個人設定、特定できない工場出荷イメージ、別体の無線コントローラーやレシーバーまで復元するものではありません。互換性のある設定は別途復元してください。

### 困ったときは

ドライブが表示されず書き込みが始まっていない場合は、有線モード、データ通信対応ケーブル、パソコンの別のUSBポートを確認してEscでの接続をやり直してください。フォーマット要求、コピーエラー、再起動しない状態ではフォーマットやコピーの繰り返しを行わず、書き込み状況が不明な間は電源を維持してKIBUへお問い合わせください。再起動した変更版の入力に問題がある場合は、前の書き込みが完了し、Escでブートローダーへ入れることを確認して参照BINへ戻します。ブートローダーへ入れない場合はKIBUへご連絡ください。USB入力ができてVIAだけが認識しない場合は、再書き込みの前に接続モード、対応JSON、ブラウザーのアクセス許可を確認します。

[KIBUサポート](https://kibushop.com/pages/contact)または[m@kibushop.com](mailto:m@kibushop.com)へ、機種名、使用ソースのリビジョンとビルド対象、BINのファイル名と可能であればSHA-256、問題が起きた手順、ブートローダー用ドライブ／USBキーボードとして認識されるかをお知らせください。変更したソースとビルドログも保管してください。お客様による変更によって、公開版とは動作が異なる場合があります。

変更記録：KIBU（kibu-keyboards、M@kibu.jp）が2026年10月15日にP75 JIS変更版のインストールと公開0812版への復旧手順を英語・日本語で作成しました。原著者・著作権・ライセンス表示および既存の変更記録は保持しています。
