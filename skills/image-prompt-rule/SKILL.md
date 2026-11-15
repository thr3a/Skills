---
name: image-prompt-rule
description: 英語の画像生成プロンプトを書くときのルール。描く場面がすでに決まっているときに、それを画像生成モデル向けの英語の描写一段落に書き起こす。
---

# 画像プロンプトの書き方

呼び出し側から「場面の内容」と「比率」を受け取り、完成した画像をそのまま描写する英語の一段落にする。
何を描くかは呼び出し側が決める。このスキルが決めるのは書き方だけである。

## 入力の扱い

- 指定された人物・物・人数・色・位置・場所・季節・時間帯・スタイルは制約として守る。言い換えたり、別のものに置き換えたりしない。
- 人物の外見を表す文が渡されたら、一字一句そのまま使う。
- 指定のない部分は、指定と矛盾しない範囲で書き手が決める。候補を並べず、一つに決めて書く。
- 足す細部には目的を持たせる。動作が読み取れる、素材感が出る、奥行きが出る、光が伝わる、のどれかに役立たないものは足さない。主役級の人物や物を勝手に増やさない。

## 構図

- 比率は向きを表す言葉で冒頭に示す。`1:1` は square、`2:3` `3:4` は vertical、`9:16` は tall vertical、`3:2` `4:3` は horizontal、`16:9` は wide horizontal。数値や解像度は書かない。
- 冒頭の一文で、向き・スタイル・媒体（photo、illustration など）・主題を示す。
- 視点（目の高さ、俯瞰、横からなど）と、何がフレームに収まるか（全身、上半身、手元など）を書く。
- 左右・手前と奥・視線の先・動きの向きを決めたら、最後まで食い違わせない。

## 場面を物理的に成り立たせる

- 一瞬を切り取った静止した場面として書く。連続した動作や時間経過は書かない。
- 人物はカメラから見た体の向き、見えている面、手の位置、何に触れているか、何に体重を預けているかが噛み合うようにする。
- 物との接触は、どの手のどこが、物のどこに触れているかまで書く。
- 光は光源・方向・質を書き、時間帯・季節・屋内外と一致させる。

## 書き方

- 現在形・三人称の平叙文で、フレームに見えているものだけを書く。ユーザーや画像生成モデルへの指示（`create`、`please`、`make sure` など）は書かない。
- 断定する。`perhaps`、`seems to`、`A or B` のようなぼかしや二択は使わない。
- `masterpiece`、`8K`、`best quality` のような品質ブースターは使わない。代わりに素材・光・質感を具体的に書く。
- 「いくつかの小物」のようにまとめず、何がいくつあるかを書く。年齢は `a woman in her thirties` のように年代で表す。
- ブランド名は呼び出し側が指定した場合だけ使う。
- 文字は入れない。看板・画面・ラベル・服のプリントなどは無地や判読できない状態として書き、最後に `No text or logos appear.` のような一文を置く。
- 長さは場面に合わせる。静かな単一の被写体なら短く、人や物が多い場面なら長めにする。同じ内容を繰り返さない。

## 出力形式

- 改行を含まない英語の一段落のプレーンテキストだけを返す。
- HTML 属性に埋め込むため、ダブルクォート `"` は使わない。

## 書き終えたら確認すること

- 指定された内容・人数・位置・季節・時間帯がすべて入っているか
- 左右・手前奥・視線・接触が食い違っていないか
- 文字・ブランド・品質ブースター・ぼかし表現が入っていないか
- 改行と `"` がないか

## 例

入力: 場面「陶芸家の女性がろくろで器を成形している。日の差す工房。左側から。手元を強調」、比率 `3:2`

```text
A horizontal naturalistic photograph of a woman potter in her forties seated at a pottery wheel in a sunlit workshop, viewed from her left side at hand level. The frame holds her profile, shoulders, forearms, hands, and the complete bowl on the wheel, with enough of the stool and wheel visible to show her working posture. She leans slightly forward with relaxed shoulders and looks down at the clay. Her left hand supports the outer wall of the bowl while the fingertips of her right hand press the inner surface near the rim, the two hands gently opposing each other across the same section of clay. Wet slip coats her fingertips and gathers in fine concentric ridges on the rounded bowl, which stays centered on the wheel head. Soft sunlight from a side window behind her catches the moisture on the clay and casts gentle shadows beneath her wrists. A worn wooden workbench and shelves of unglazed pots recede out of focus in the background. Warm earth tones and believable skin texture give the scene a tactile, unposed quality. No text or logos appear.
```
