# NEON 777 CRUISE

**A portrait-mode pachislot (slot machine) game in a single HTML file.**
**単一HTMLファイルで動く縦画面パチスロゲーム。**
**单个 HTML 文件实现的竖屏老虎机游戏。**

🇯🇵 [日本語](#日本語) · 🇬🇧 [English](#english) · 🇨🇳 [中文](#中文)

Game file: `index.html`

---

## 日本語

### 概要

ブラウザだけで遊べる縦完結レイアウトのパチスロゲームです。インストール不要、外部ライブラリ不要、オフラインでも動作します。

- **ファイル**: `index.html` 1ファイルだけ(約46KB)
- **画面**: スマホでは縦全屏、PCでは中央に縦レイアウトで表示
- **言語**: 日本語 / English / 中文(ヘッダーのボタンで切替、初回は端末の言語を自動検出)
- **サウンド**: Web Audio APIによる合成音。ヘッダーの 🔊 / 🔇 でON/OFF(設定は保存)
- **セーブ**: 端末の localStorage に自動保存(アカウント・通信なし)
- **台**: 全14台(1/3/5/9ライン、4タイプ)
- 実際の金銭は一切関係ありません(架空のメダルゲーム)

### 遊び方

1. `index.html` をブラウザに開く(ダブルクリックでOK、スマホに転送してもOK)
2. 最初に **500メダル** 所持、解放済み台は3台
3. ホームで台をタップ → **BET** を−/+で調整 → **SPIN**(キーボード: `Space` / `S`)
4. 左右の数字ドットがラインを示します。ライン上の3つ揃いで配当
5. **AUTO** = 100スピンまで連続回転 / **TURBO** = 高速回転 / **配当表** = 台の配当とルール

### 配当・特別なルール

| 記号 | 内容 |
|---|---|
| 図柄3つ揃い | 配当表の配当 × ユニット(ユニット = BET ÷ ライン数) |
| 低ランク図柄 2つ揃い | ライン上で少量配当(1〜2ユニット) |
| 🔄 3つ(どの行でも) | リプレイ: BET還元(A/RJタイプ)後、即フリーチャンス。最大12連鎖。RJタイプは **2倍** 還元 |
| 🎰 3つ(どの行でも) | ボーナスゲーム(約1/200)。BBタイプ=12枚のカードから3枚選ぶBIG BONUS(0〜40×BET)。ATタイプ=高確率10回転のASSIST TIME |
| MEGA JACK | 全スピンに約1/1500の確率で発生、40×BET |

- メダルが尽きても、60秒ごとに **+300メダル** を受け取れます(ホームまたはSPIN時に案内)
- 実測RTP(ペイアウト率): 全14台で **92.6%〜99.1%**(1台あたり10万スピンでシミュレーション検証済み)

### 台一覧(全14台)

タイプ: **A** = リプレイ型 / **BB** = BIG BONUS(カード選択) / **AT** = ASSIST TIME(フリースピン) / **RJ** = リプレイ2倍還元

| 台名 | タイプ | ライン | ベット | 解放コスト | TOP図柄(1ユニットあたり) |
|---|---|---|---|---|---|
| CLASSIC 777 | A | 1 | 1〜10 | 無料 | 7️⃣ ×750 |
| FRUIT PARADISE | A | 3 | 1〜10 | 無料 | 🍍 ×600 |
| SAKURA FESTIVAL | BB | 3 | 1〜10 | 無料 | 🌸 ×1000 |
| NEON DRIVE | AT | 5 | 1〜10 | 200 | 🏎️ ×900 |
| DRAGON'S HOARD | RJ | 5 | 1〜10 | 300 | 🐉 ×825 |
| OCEAN TREASURE | AT | 9 | 1〜5 | 400 | 🐬 ×950 |
| LUCKY CAT | BB | 5 | 1〜10 | 500 | 🐱 ×1000 |
| SPACE ODYSSEY | AT | 9 | 1〜5 | 700 | 🚀 ×1000 |
| PIRATE GOLD | BB | 9 | 1〜5 | 900 | 🏴‍☠️ ×1050 |
| CYBER NINJA | RJ | 9 | 1〜5 | 1100 | 🥷 ×750 |
| ICE FORTRESS | AT | 9 | 1〜5 | 1300 | ❄️ ×950 |
| JUNGLE BEAT | BB | 9 | 1〜5 | 1600 | 🦁 ×1000 |
| WIZARD CASTLE | RJ | 9 | 1〜5 | 1900 | 🧙 ×825 |
| MEGA VOLCANO | BB | 9 | 1〜10 | 2400 | 🌋 ×1400 |

### セーブデータ

- 保存先: ブラウザの localStorage(キー `neon777cruise_v1`)
- 保存内容: メダル数、解放済み台、台ごとのベット・スピン数・最大WIN・ボーナス回数、言語、サウンド、TURBO、最終プレイ台
- ホームの「セーブデータ削除」ボタンで全削除できます
- ブラウザのデータを消去するとセーブも消えます

### 動作環境

JavaScript・localStorage・Web Audio APIが使える最近のブラウザ(Chrome / Edge / Firefox / Safari、iOS・Android含む)。インターネット接続は不要です。

### 技術

依存ゼロの素の HTML + CSS + JavaScript。サウンドはすべて Web Audio API でリアルタイム合成しており、画像・音声ファイルもライブラリも一切使いません。

---

## English

### Overview

A portrait-layout pachislot game that runs in the browser — no install, no libraries, works offline.

- **File**: just `index.html` (~46 KB)
- **Screen**: full-height portrait layout on phones, centered portrait column on desktop
- **Languages**: 日本語 / English / 中文 — switch in the header; auto-detected on first launch
- **Sound**: all synthesized live with the Web Audio API. Toggle 🔊 / 🔇 in the header (setting is saved)
- **Save**: auto-saved to local storage on the device (no account, no network)
- **Machines**: 14 machines (1 / 3 / 5 / 9 paylines, 4 machine types)
- Completely fictional — no real money involved

### How to play

1. Open `index.html` in a browser (double-click; works on phones too)
2. You start with **500 medals** and 3 unlocked machines
3. Tap a machine → adjust **BET** with −/+ → press **SPIN** (keyboard: `Space` / `S`)
4. The numbered dots on the left/right edges mark the paylines. Match 3 on a line to win
5. **AUTO** = up to 100 spins / **TURBO** = fast reels / **PAY TABLE** = payouts & rules per machine

### Pays & special rules

| Symbol | Rule |
|---|---|
| 3-of-a-kind on a line | table payout × unit (unit = BET ÷ number of lines) |
| Low symbols, 2-of-a-kind on a line | small payout (1–2 units) |
| 🔄 ×3 (any row) | Replay: bet refunded (A/RJ types), then an instant free spin — chains up to 12×. RJ types refund **double** |
| 🎰 ×3 (any row) | Bonus game (~1 in 200). BB machines: BIG BONUS card pick (3 of 12 cards, 0–40× BET). AT machines: ASSIST TIME, 10 boosted free spins |
| MEGA JACK | random, ~1 in 1500 spins, pays 40× BET |

- Out of medals? Claim **+300 medals** every 60 seconds (offered on the home screen or when you spin)
- Measured RTP (return-to-player): **92.6%–99.1%** across all 14 machines (verified with a 100,000-spin simulation per machine)

### Machines (14)

Types: **A** = replay type / **BB** = BIG BONUS (card game) / **AT** = ASSIST TIME (free spins) / **RJ** = double-refund replays

| Machine | Type | Lines | Bet | Unlock | TOP symbol (per unit) |
|---|---|---|---|---|---|
| CLASSIC 777 | A | 1 | 1–10 | free | 7️⃣ ×750 |
| FRUIT PARADISE | A | 3 | 1–10 | free | 🍍 ×600 |
| SAKURA FESTIVAL | BB | 3 | 1–10 | free | 🌸 ×1000 |
| NEON DRIVE | AT | 5 | 1–10 | 200 | 🏎️ ×900 |
| DRAGON'S HOARD | RJ | 5 | 1–10 | 300 | 🐉 ×825 |
| OCEAN TREASURE | AT | 9 | 1–5 | 400 | 🐬 ×950 |
| LUCKY CAT | BB | 5 | 1–10 | 500 | 🐱 ×1000 |
| SPACE ODYSSEY | AT | 9 | 1–5 | 700 | 🚀 ×1000 |
| PIRATE GOLD | BB | 9 | 1–5 | 900 | 🏴‍☠️ ×1050 |
| CYBER NINJA | RJ | 9 | 1–5 | 1100 | 🥷 ×750 |
| ICE FORTRESS | AT | 9 | 1–5 | 1300 | ❄️ ×950 |
| JUNGLE BEAT | BB | 9 | 1–5 | 1600 | 🦁 ×1000 |
| WIZARD CASTLE | RJ | 9 | 1–5 | 1900 | 🧙 ×825 |
| MEGA VOLCANO | BB | 9 | 1–10 | 2400 | 🌋 ×1400 |

### Save data

- Stored in the browser's localStorage (key `neon777cruise_v1`)
- Saved: medals, unlocked machines, per-machine bet / spins / biggest win / bonus count, language, sound, turbo, last machine
- Wipe everything with the **DELETE SAVE** button on the home screen
- Clearing browser data also removes the save

### Requirements

Any recent browser with JavaScript, localStorage and Web Audio (Chrome / Edge / Firefox / Safari, iOS and Android included). No internet connection needed.

### Tech

Plain HTML + CSS + JavaScript with zero dependencies. All sounds are synthesized live via the Web Audio API — no image or audio files, no external libraries.

---

## 中文

### 概述

只在浏览器中运行的竖屏老虎机游戏 —— 无需安装、无外部库、可离线运行。

- **文件**: 只有 `index.html` 一个文件(约 46KB)
- **界面**: 手机为竖屏全屏,电脑为居中竖屏布局
- **语言**: 日本語 / English / 中文 —— 顶部按钮切换,首次打开自动检测系统语言
- **音效**: 全部由 Web Audio API 实时合成。顶部 🔊 / 🔇 开关(设置会保存)
- **存档**: 自动保存到本机 localStorage(无需账号、无需联网)
- **机器**: 共 14 台(1/3/5/9 条赔付线,4 种机型)
- 纯娱乐游戏,不涉及任何真实货币

### 玩法

1. 在浏览器中打开 `index.html`(双击即可,也可传到手机)
2. 初始赠送 **500 代币**,已解锁 3 台机器
3. 点击机器 → 用 −/+ 调整**投注** → 点**旋转**(键盘:`空格` / `S`)
4. 转轮左右两侧的编号圆点代表赔付线。线上 3 个相同即中奖
5. **AUTO** = 最多连转 100 次 / **TURBO** = 高速旋转 / **赔率表** = 本机赔率与规则

### 赔付与特殊规则

| 符号 | 规则 |
|---|---|
| 线上 3 个相同 | 按赔率表赔付 × 单位注(单位注 = 投注 ÷ 线数) |
| 低等级符号 2 个相同 | 小额赔付(1〜2 单位注) |
| 🔄 ×3(任意一行) | 重转:返还投注(A/RJ 机型),随后立即免费再转,最多连锁 12 次。RJ 机型**双倍**返还 |
| 🎰 ×3(任意一行) | 奖励游戏(约 1/200)。BB 机型 = 大奖励:12 张牌选 3 张(0〜40 倍投注);AT 机型 = 助攻时间:10 次高赔率免费旋转 |
| 超级大奖 | 每次旋转约 1/1500 概率随机触发,赔付 40 倍投注 |

- 代币用完?每 60 秒可领取 **+300 代币**(首页或点旋转时会提示)
- 实测 RTP(返奖率):全部 14 台为 **92.6%〜99.1%**(每台 10 万次旋转模拟验证)

### 机器一览(14 台)

机型:**A** = 重转型 / **BB** = 大奖励(选牌)/ **AT** = 助攻时间(免费旋转)/ **RJ** = 双倍返还重转

| 机器 | 机型 | 线数 | 投注 | 解锁 | 顶级符号(每单位注) |
|---|---|---|---|---|---|
| CLASSIC 777 | A | 1 | 1〜10 | 免费 | 7️⃣ ×750 |
| FRUIT PARADISE | A | 3 | 1〜10 | 免费 | 🍍 ×600 |
| SAKURA FESTIVAL | BB | 3 | 1〜10 | 免费 | 🌸 ×1000 |
| NEON DRIVE | AT | 5 | 1〜10 | 200 | 🏎️ ×900 |
| DRAGON'S HOARD | RJ | 5 | 1〜10 | 300 | 🐉 ×825 |
| OCEAN TREASURE | AT | 9 | 1〜5 | 400 | 🐬 ×950 |
| LUCKY CAT | BB | 5 | 1〜10 | 500 | 🐱 ×1000 |
| SPACE ODYSSEY | AT | 9 | 1〜5 | 700 | 🚀 ×1000 |
| PIRATE GOLD | BB | 9 | 1〜5 | 900 | 🏴‍☠️ ×1050 |
| CYBER NINJA | RJ | 9 | 1〜5 | 1100 | 🥷 ×750 |
| ICE FORTRESS | AT | 9 | 1〜5 | 1300 | ❄️ ×950 |
| JUNGLE BEAT | BB | 9 | 1〜5 | 1600 | 🦁 ×1000 |
| WIZARD CASTLE | RJ | 9 | 1〜5 | 1900 | 🧙 ×825 |
| MEGA VOLCANO | BB | 9 | 1〜10 | 2400 | 🌋 ×1400 |

### 存档

- 保存位置:浏览器 localStorage(键名 `neon777cruise_v1`)
- 保存内容:代币、已解锁机器、各机器的投注/旋转数/最大赢取/奖励次数、语言、音效、TURBO、上次游玩的机器
- 首页的「删除存档」按钮可清空全部数据
- 清除浏览器数据也会一并删除存档

### 运行环境

支持 JavaScript、localStorage 和 Web Audio API 的较新浏览器(Chrome / Edge / Firefox / Safari,含 iOS 与 Android)。无需联网。

### 技术

零依赖的原生 HTML + CSS + JavaScript。所有音效均由 Web Audio API 实时合成,不使用任何图片、音频文件或外部库。

---

*For entertainment purposes only. No real-money gambling. / ギャンブルは依存性を助長する可能性がありますが、本ゲームは仮想メダルのみを使用します。 / 本游戏仅使用虚拟代币,仅供娱乐。*
