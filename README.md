# Dolphin — MemoryTalk 64タイプ診断の絵

64タイプ × 2つの姿（男性寄り / 女性寄り）で128枚。

| フォルダ | 中身 | 用途 |
|---|---|---|
| `images/` | 1024×1536 PNG（原寸） | 作り直すときの元 |
| `hero/` | 900×1350 JPEG | LINEの結果カードに出す。**文字なし** |
| `share/` | 900×1560 JPEG | 保存して貼る用。肩書きとコードを焼き込んである |

`hero/` に文字を入れていないのは、カード側（Flex Message）が肩書き・コード・
軸バーを描くためです。画像にも入れると二重になりますし、LINEが描く文字は崩れず
あとから直せます——画像に焼くと、肩書きを1つ直すだけで128枚の作り直しになります。

`share/` は逆に文字が要ります。**画像を長押しで保存すると絵だけになる**ので、
SNSに貼ったときに何のカードか分からなくなるためです。日本語は合成しているので
崩れません（画像生成には書かせていません）。

## 配信

GitHub Pages から配信しています。

```
https://yuki-ishizaka111.github.io/Dolphin/hero/INTJ-A-C-m.jpg
https://yuki-ishizaka111.github.io/Dolphin/share/INTJ-A-C-f.jpg
```

自宅のサーバーに置かないのは、負荷の話ではなく**切れないため**です。あのMacは
寝ます。寝ている間に結果カードの絵が出ないのは困るので、こちらに置いています。

## 作り直し方

元は `memorytalk-bot` 側にあります。

```bash
npx tsx scripts/type-art-prompts.ts INTJ      # 指示文を見る
npx tsx scripts/type-art-generate.ts --go     # APIでまとめて作る
python3 scripts/type-art-publish.py <元フォルダ> <出力先>   # 縮小・変換
```
