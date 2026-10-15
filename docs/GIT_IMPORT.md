# Source Provenance and Exact Checkout

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-09-24. Changes: Translated and clarified the English source-provenance and exact-checkout instructions. Original authorship and license notices are retained.

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-09-24. Changes: Updated branch references after renaming the P75 JIS maintenance branch and removing the unused kibu branch. The release tag and download links are unchanged.

> Modified by KIBU (kibu-keyboards) (M@kibu.jp) on 2026-10-15. Changes: Updated repository links, the release identity, and publication navigation for the new QMK fork. Firmware, fixed dependencies, the reference BIN, the VIA definition, original authorship, licenses, and earlier modification records are retained.

The release tag `p75-jis-0812-r1-20261015` is the fixed reference for this publication in [KIBU's QMK fork](https://github.com/kibu-keyboards/qmk_firmware-kibu). Ongoing P75 JIS maintenance uses the `p75-jis` branch. This branch preserves the earlier supplied-source snapshot and its publication commits; it does not reconstruct production Git history or claim ancestry from the current upstream tree. The `master` branch retains the upstream snapshot captured at fork creation. Do not build P75 JIS from `master` or substitute its dependencies. See [source and licenses](SOURCE_AND_LICENSES.md) for the baseline and component provenance.

Source is under `qmk_firmware/`; build entry points are under `tools/`. Dependencies are ordinary files included in the release. The historical `qmk_firmware/.gitmodules` is retained for provenance: **do not run `git submodule update` to replace the fixed dependencies.** No private dependency repository is required.

## Preserve exact file bytes

The source retains its original `.gitattributes` and `.gitignore`. A normal checkout may transform file bytes according to those attributes. To verify the release manifest, download the release ZIP or run the following in Bash using a new directory:

```bash
git clone --no-checkout --branch p75-jis-0812-r1-20261015 https://github.com/kibu-keyboards/qmk_firmware-kibu.git p75-jis-0812-r1-20261015
cd p75-jis-0812-r1-20261015
printf '* -text -eol -filter -ident\n' > .git/info/attributes
git checkout --detach p75-jis-0812-r1-20261015
```

These attributes apply only to this clone. No submodule checkout is required. The build workflow also extracts `git archive HEAD` over its checkout to preserve the committed bytes.

[The release manifest](../metadata/release-manifest.csv) records the size and SHA-256 of every release file except itself. The ZIP checksum covers the complete package, including the manifest. Original-input records in `metadata/` describe the supplied baseline; use the release manifest for the current files.

公開先の変更：2026年10月15日、KIBUの新しいQMK forkへ配布先を変更しました。対象は0812版の対応ソースコードで、ファームウェア、固定依存ファイル、参照用BIN、VIA定義は変更していません。原著者・著作権・ライセンス表示および既存の変更記録を保持しています。P75 JISには上記のタグ付き配布物をご利用ください。
