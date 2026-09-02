# WSJT-X Improved JP1LRT Edition

🌐 **言語:** [English](README.md) | 日本語

[![Status](https://img.shields.io/badge/status-Public%20Release%20Candidate-orange)](https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6)
[![Current release](https://img.shields.io/badge/release-20260901A--REB522--P6-blue)](https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6)
![User Guide](https://img.shields.io/badge/User%20Guide-Edition%201.8%20%7C%2016%20languages-brightgreen)

**WSJT-X Improved本来の機能を維持しながら、より賢いCQ RUN、Wanted/Hunting、安全なQSO遷移、そして実運用を重視したFT8/FT4ワークフローを追加する、JTDXの運用思想に着想を得た追加運用レイヤーです。**

> **現在のPublic Release Candidate:** `20260901A-REB522-P6 / P6-AL`  
> **ベース:** WSJT-X Improved `3.1.0 / 260522`（2026年5月22日版）  
> **WSJT-X Improved 3.2.0ベースのリリースではありません。**

**最新リリース:**  
https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6

---

## なぜJP1LRT Editionを作ったのか

私は **津久浦慶治 / JP1LRT** です。

**JTDXのauthorized beta tester（公認ベータテスター）**であり、**日本語ローカライズ担当**でもあります。

普段FT8/FT4を運用する中で、私はJTDXの運用思想に非常に慣れ親しんできました。特に、CQ RUNでの運用フロー、優先順位に基づく呼出局の選択、Wanted局の扱い、そして自動化を利用しながらも運用者が主導権を保てる点です。

その後、WSJT-X 3.0が登場し、続いてWSJT-X Improved 3.1が登場しました。

私はそのソースコードを読み、解析し始めました。そして、新しいデコーダー構成と、WSJT-X Improvedに加えられた実用的なデコード機能に非常に強く惹かれました。

そこで、非常に単純なアイデアが浮かびました。

> **「WSJT-X Improvedのデコーダーとプラットフォームを使いながら、JTDXに近い感覚で運用できたらどうだろう？」**

これが、**WSJT-X Improved JP1LRT Edition**の始まりです。

### 実際の始まりはAvg/Lagでした

このプロジェクトは、最初から大規模な運用ロジックの再設計を目指して始まったわけではありません。

**最初のJP1LRT modificationはAvg/Lag**でした。受信デコードの`DT`値を観測し、status areaにrobust averageとcycle-boundary lag indicationを表示する、実運用向けの小さなタイミング補助機能です。

その小さな実験が出発点でした。

そこから、internal logical-time Sync、CQ RUNとAutoSeqのownership logic、Wanted/Hunting、安全なmanual takeover、Terminal Hold、DF handling、directed-CQ safeguards、拡張callsign data、diagnostics、そして現在P6 / P6-ALに含まれる各種運用機能へと発展していきました。

つまり、現在のJP1LRT Editionは、次のような単純な問いから自然に育ってきたものです。

> **「普段FT8/FT4を運用するとき、自分が欲しい情報と運用フローをWSJT-X Improvedの中に直接持ち込めないだろうか？」**

目的は、WSJT-X ImprovedをJTDXそのものに変えることではありません。また、WSJT-X / WSJT-X Improvedに元々存在する機能を削除したり、置き換えたりすることでもありません。

JP1LRT Editionが目指しているのは、

- **すでにうまく動いているものは、そのまま残す**
- **WSJT-X Improved本来の能力を維持する**
- その上に、**JTDXの運用思想を参考にした運用レイヤーを追加する**

というものです。

JP1LRTによる変更では、**FT8デコーダー本体を置き換えたり、再チューニングしたりしていません。**

主な変更対象はデコーダーの周囲にある運用ロジックです。CQ RUNでの選局、Wanted/Hunting、QSOの所有権と安全な引き継ぎ、終端メッセージの保護、手動介入、DF制御、診断情報、その他の運用ワークフロー改善が中心です。

### このプロジェクトのきっかけとなったデコーダー解析

WSJT-X Improved 3.1のデコーダーについて、なぜ私が強く興味を持ったのかを解説したソースコードベースの記事も書いています。

**WSJT-X 3.1 improved の FT8 デコーダー設定を理解する**

デコーダー解析記事は現在、**16言語**で公開しています。

[🇬🇧 English](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_en.html) | [🇯🇵 日本語](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ja.html) | [🇫🇷 Français](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_fr.html) | [🇩🇪 Deutsch](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_de.html) | [🇪🇸 Español](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_es.html) | [🇨🇳 简体中文](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_zh-cn.html) | [🇹🇼 繁體中文](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_zh-tw.html) | [🇰🇷 한국어](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ko.html) | [🇵🇹 Português](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_pt.html) | [🇮🇹 Italiano](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_it.html) | [🇳🇱 Nederlands](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_nl.html) | [🇷🇺 Русский](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ru.html) | [🇵🇱 Polski](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_pl.html) | [🇹🇷 Türkçe](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_tr.html) | [🇸🇪 Svenska](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_sv.html) | [🇮🇩 Bahasa Indonesia](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_id.html)

この記事では、Decode Start、段階的デコード、STD / MTDの関係、FT8サイクル内でのCPUリソース配分、実運用でのデコーダー設定などを扱っています。

---

## JP1LRT Editionは何が違うのか？

JP1LRT Editionは、**実際の運用フロー**を中心に設計しています。

目的は単純にボタンを増やすことでも、自動化を増やすことでもありません。

重要なのは、**自動運用を予測可能なものにすること**、そして**運用者の意図と進行中QSOの状態を守ること**です。

### 主な運用思想

- **Avg/Lagとoptional internal Sync — このプロジェクトの出発点**  
  Avg/Lagは受信デコードの`DT`値からタイミング情報を得ます。`Avg=`は利用可能なDT値のrobust averageを表示し、`Lag=`はcycle boundaryに対する符号付きタイミング表示を行います。これはstatus/timing aidであり、**FT8 decoder coreは変更しません**。後に追加されたoptional internal Syncも、このタイミング処理から発展したものです。

- **AutoSeq 2 / AutoSeq 3**  
  JTDXユーザーに馴染みのある運用思想を参考にした、優先順位ベースのCQ RUN呼出局選択です。

- **Wanted / Hunting**  
  Wantedとして設定したcallsign、prefix、gridなどを待ち受け、安全な条件が成立した場合に自動取得します。

- **Wanted-Pounce無応答時のHunting復帰（P6）**  
  Huntingから開始されたQSOで、相手から続きの応答がなく、こちらがレポートを正確に3回送信した場合、4回目のレポートを送信せず、自動CQへ移行せず、Wanted Pounceを有効なまま安全にHunting待機へ戻ります。

- **Terminal Hold**  
  RR73 / 73処理と終端フェーズの間、現在のQSO相手のownershipを維持します。これにより、早すぎるQSO state clearや不適切な次局への切り替えを防止します。

- **Safe manual takeover**  
  運用者による手動操作は優先します。ただし、保護対象となっている送信が進行中の場合は、その送信を安全に完了させてから新しい相手へ切り替えます。

- **Active-QSO protection**  
  進行中QSOがあるとき、第三者局のdecodeによって現在のQSO相手が勝手に上書きされないよう保護します。

- **Best S&Pの言語非依存化**  
  `New Call on Band`や`New DXCC`の判定に、翻訳された表示文字列ではなく、安定した内部カテゴリ識別子を使用します。

- **LoTW tie-break**  
  候補局が他の条件で同等だった場合、LoTW statusをtie-breakとして利用できます。

- **Directed-CQ safety**  
  `CQ DX`および標準的な地域指定CQについて、自動取得時に明確な安全条件を設けています。

- **Orange WantedとBlue display-onlyの分離**  
  OrangeはWanted / 自動優先選択の対象になり得ます。一方、Blueは表示上のハイライトだけに使用でき、自動Wanted targetにはなりません。

- **Quick Call OFFにも意味がある**  
  Quick CallがOFFの場合、Best S&Pがtarget、DX Call、DX Grid、送信メッセージを準備しても、自動的に送信開始はしません。

- **JTDXライクなBand Activity / Activity Window表示**  
  CQ行だけでなく、report、`RRR`、`RR73`、`73`など通常QSO中のdecodeでも、局属性を表示し続けられるよう拡張しています。JTDXで慣れ親しんだ情報量の多い運用表示に近づけています。

- **LoTWユーザーの明示表示**  
  最新のLoTW-user dataが利用できる場合、LoTW usersをactivity display上で明示的に表示します。country/entity、worked/B4、Wanted/highlight、その他の局属性も、CQ行であるかどうかに依存せず表示できます。

- **見やすくしたWide Graph**  
  Wide Graph / waterfall表示を実運用向けに調整しています。contrastにはJTDX由来のmedian-noise normalizationを使い、**Gain -11 / Zero 7**を実用的な開始値としています。また、Wide Graphの時計文字が欠けていたレイアウトも調整し、時計を完全に読めるようにしています。

- **高精度の自局Grid Locator**  
  レポーティングなど、高精度Locatorを利用できるサービス向けに、最大10文字の自局Grid Locatorを入力できます。

- **拡張`ALLCALL7.TXT` support**  
  元のALLCALL7 handlingを**250,000-entry-class capacity**へ拡張しました。P6 / P6-AL packageには現在、**218,100 unique callsigns**を含む`ALLCALL7.TXT` datasetを収録しています。これによりlocal callsign lookupと、それに依存するdisplay/classification機能のカバー範囲が大きく広がります。FT8 decoderやover-the-air message自体は変更しません。

- **詳細なdiagnostics**  
  必要に応じてJP1LRT独自の診断情報を`ALL.TXT`へ記録できます。複雑なstate transition問題の再現・解析に利用できます。

JP1LRT Editionは、意図的に**additive（追加型）**として設計しています。

元のWSJT-X Improvedの通常機能を失わせるのではなく、**日常のFT8/FT4運用を、その上からより使いやすくする**ことを目的としています。

---

## このプロジェクトはどのように育ったか

Release historyを見ると、JP1LRT Editionが**最初から完成形として設計されたわけではない**ことが分かります。ひとつの実用的なtiming aidから始まり、非常に短い期間でJTDXの運用思想を取り込んだ総合的な運用環境へ発展していきました。

### 2026年4月 — プロジェクトの骨格ができる

1. **4月6日 — Avg/Lagが出発点（`v20260406`）**  
   最初に公開したJP1LRT buildは**Avg/Lag display patch**でした。

2. **4月7日 — Avg/Lag/Sync（`v20260407`）**  
   タイミング実験がAvg/Lagとinternal logical-time Syncへ発展しました。

3. **4月8日 — Wide Graph / waterfallがプロジェクトの一部になる（`v20260408`）**  
   JTDXの`scale_by_median()` normalizationを移植し、waterfall contrastを改善。gain calculationもJTDX寄りに変更し、Gain/Zeroの数値tooltipも追加しました。

4. **4月9日 — AutoSeq 2/3とpriority-based CQ operation（`v20260409`）**  
   AutoSeq 2とAutoSeq 3を追加し、priority-based station selectionを実装。non-CQ messageのcoloringもJTDX的な方向へ拡張しました。

5. **4月9日夜 — JTDX-style displayとlarge `ALLCALL7.TXT` support（`v20260409b`）**  
   これはかなり早い時期の重要な拡張でした。  
   - non-CQ lineのattribute-oriented highlighting  
   - 明示的な**LoTW `●` marker**  
   - Fox/Hound / MSHV composite message表示の改善  
   - current DX Call rowの強調  
   - Wide Graph identification  
   - **larger `ALLCALL7.TXT` array/read support**  
   を追加しました。続く`v20260409c`では、前のpackageに含まれていたALLCALL7 datasetが不完全だったため、full datasetを復元しました。

6. **4月11日 — standalone packageとproject identification（`v20260411b`）**  
   Windows packageをself-contained化し、PSK Reporter / title bar上でもmodified buildだと明確に識別できるようにしました。

7. **4月13日 — CQ RUNが本格的な運用システムになる（`v20260413`）**  
   automatic next-station CQ RUN handoffを実装し、ADIF snapshot protectionとmanual / AutoSeq ownership safeguardsを強化しました。`ALLCALL7.TXT`もさらに拡張し、内部capacityを**250,000-entry class**へ。この時点のrelease notesでは**210,981 entries**のdatasetが記録されています。

8. **4月17〜28日 — terminal messageとtarget selectionの安全性強化**  
   RR73/73 duplicate transmission、stale candidate、manual-target ownership、double-click corner caseなどを調査・修正しました。  
   **4月27日（`v20260427B`）**には、Wanted callsign / prefix / grid priorityをAutoSeq / CQ RUNへ追加しました。

### 2026年5月 — Wanted/Huntingが主要テーマになる

9. **5月25〜27日 — Wanted Pounce / Huntingとcolor-action分離**  
   `v20260525A–G` lineでWanted pounce、stale timeout、return-to-Hunting behaviorを発展させました。  
   `v20260527C`では役割を明確に分離しました。  
   - **Orange** = display + Wanted / AutoSeq / pounce action  
   - **Blue** = display-only highlight

10. **5月29日 — FT4 late-pickとtarget DF following（`v20260529D`）**  
    AutoSeq 2 late-pick supportをFT4へ拡張し、targetを呼んでいる間、Tx DFを動かさずにRx DFだけを相手のdecoded DFへfollowできるようにしました。

### 2026年6月 — QSO ownershipとterminal safetyを徹底的に強化

11. **6月 — Terminal Hold、terminal arbitration、manual takeover safety**  
    RR73/73までactive QSOを確実に保護すること、stale ownershipやunsafe next-target handoffを防ぐこと、そしてoperatorが手動介入した場合の安全な動作定義に開発の重点が移りました。

12. **6月末 — Rx DFとTerminal Holdの連携**  
    RXDF1/RXDF2 lineで、Rx DFをいつTx DFへ戻すべきかを精査し、Terminal Holdがactiveの間にRx markerが早く戻ってしまうことを明示的に防止しました。

### 2026年7月 — StandardとALを並行buildとして整理

13. **7月 — active-QSO、stale-target、manual-takeover protectionをさらに強化**  
    tester feedbackを基に、運用ロジックの堅牢性を高めました。

14. **7月22日系 — Standard / AL GUI builds**  
    同じcore logicを、  
    - **Standard GUI** — WSJT-X Improved PLUS-style  
    - **AL GUI** — AL_PLUS / JTDX-like layout  
    の2系統で正式に配布する形を明確化しました。最初のmultilingual User Guide seriesもEnglish / Japanese / German / Spanishの4言語で公開しました。

### 2026年8〜9月 — Public RCへ成熟

15. **8月 — higher-precision Grid、directed-CQ safety、release-line consolidation**  
    GL10 / RCQ workで高精度自局Grid supportを追加しつつ、mode-safeなtransmitted locator lengthを維持しました。また、自動取得に`CQ DX` / regional CQ safety gateを追加しました。

16. **8月 — REB522 / P3→P5 Public-RC line**  
    それまでの開発成果をJP1LRT Editionのrelease lineへrebase・統合。Best S&Pのlanguage-independent selectionやReturn-to-Hunting behaviorなども後期の重要な改良です。

17. **9月1日 — P6 / P6-AL**  
    P6ではWanted-Pounce no-reply ruleを追加。レポートを正確に3回送っても応答がなければ、4回目を送らず、自動CQにも移行せず、安全にHuntingへ戻ります。User Guide Edition 1.8はその後**16言語**に到達しました。

このように、最初はひとつの**Avg/Lag display experiment**だったものが、少しずつ、**WSJT-X Improvedで気に入ったdecoder/platform**と、**JTDXで慣れ親しんだoperating flowとinformation density**を組み合わせる試みへ成長しました。

---

## 実運用のための表示改善

JP1LRT Editionの変更は、automationやQSO state machineだけではありません。

**実際の運用中に画面から必要な情報を読み取りやすくすること**も、プロジェクトの大きなテーマです。

### Band Activity / Activity Window

私はactivity displayをJTDXに近い感覚で使いたいと考えました。

JP1LRT Editionでは、局属性をCQ lineだけに限定しません。report exchange、`RRR`、`RR73`、`73`など、通常QSO中のtrafficでも有用なstation attributeを表示し続けることができます。

利用可能なdata fileとsettingsに応じて、例えば以下を表示・強調できます。

- **LoTW-user status**
- country / DXCC entity
- worked / B4 status
- Wanted / highlight status
- current-target emphasis
- その他JP1LRT display/classification logicで使用するstation attributes

つまり、decode lineがCQではなく進行中QSOの一部になっただけで、局に関する有用なcontextを失わないようにしています。

特に**LoTW-user marker**は、JP1LRTのcandidate-selection logicの一部でLoTW statusをtie-breakにも利用しているため、実運用上も分かりやすい表示です。

### Wide Graph / waterfall

Wide Graphも見やすさを重視して調整しています。

Waterfall contrastには**JTDX-derived median-noise normalization**を使用し、JP1LRT Editionでは**Gain -11 / Zero 7**を実用的な開始値としています。

Wide Graph layout自体も調整しました。upstream layoutでは時計文字の一部が欠けて見えることがありましたが、JP1LRT layoutでは時計が完全に表示され、通常運用中でも読みやすくなるよう修正しています。

AutoSeqやTerminal Holdと比べれば小さなUI変更ですが、根底にある設計思想は同じです。

> **運用者が実際に必要とする情報を、運用中にもっと見やすくする。**

---

## 拡張ALLCALL7.TXT callsign database

JP1LRT Editionでは、local `ALLCALL7.TXT` callsign databaseの扱える規模も拡張しています。

これは実は**かなり初期のJP1LRT modification**です。large-ALLCALL7 supportは**2026年4月9日の`v20260409b`**で登場し、array sizeとread limitを拡張して、より大きなdatasetを扱えるようにしました。その直後のpackage updateでは、不完全なdatasetが見つかったためcomplete datasetを復元しています。

`v20260413`の時点では、内部callsign arrayと`MAXC`を**250,000-entry class**へ拡張し、当時のreleaseでは**210,981 entries**を記録しています。

現在のP6 / P6-AL distributionには、**218,100 unique callsigns**が含まれています。

この大きなdatasetにより、local callsign lookupと、それに依存するdisplay/classification functionのcoverageが大幅に広がります。

`ALLCALL7.TXT`はsupporting local data fileです。これを拡張しても、**FT8 decoder、送信されるFT8/FT4 message、AutoSeqのQSO ownership protection、PSK Reporter behaviorは変更されません。**

P6 / P6-AL packaged dataset:

`SHA-256: 676f1a402ead5944fccd88656427ae9f016dfdfa58b7fdc3c8e0b7ac88033b18`

`ALLCALL7.TXT`は`wsjtx.exe`と同じfolderに置いてください。

---

## 現在のリリース：P6 / P6-AL

| 項目 | 現在の内容 |
|---|---|
| Release | `20260901A-REB522-P6 / P6-AL` |
| Status | **Public Release Candidate** |
| Base | WSJT-X Improved `3.1.0 / 260522` |
| Base date | 2026年5月22日 |
| User Guide | Edition 1.8 |
| Guide languages | **16** |
| Windows builds | Standard GUI / AL GUI |
| Source | complete source bundle提供 |

### Standard版とAL版

両方とも、QSO logic、AutoSeq、Wanted/Hunting、Terminal Hold、manual-takeover safety、Best S&P、directed-CQ safetyについては同じ現行logicを搭載しています。

主な違いは**GUI layout**です。

**Standard版とAL版を同じdirectoryへ展開しないでください。**

---

## P6の重要変更 — Wanted-Pounce無応答処理

P6ではHuntingに関する重要なboundary conditionを改善しました。

Wanted Pounce / Huntingから開始したQSOで、相手から続きの応答が得られず、こちらがレポートを正確に3回送信した場合、

- 4回目のレポートは送信しない
- CQを自動送信しない
- Auto Txを停止する
- DX Callをclearする
- Tx6 / CALLINGへ戻る
- Wanted Pounceは有効なまま
- Orange Hunting standbyへ復帰
- 蓄積されたAutoSeq candidateを保持
- 同じWanted局を後から再びnew QSOとして取得可能

となります。

ただし、3回目のレポート送信直後に**RR73などのvalid response**が届いた場合は、QSO completionが優先されます。

**final 73 → Terminal Hold → normal return to Hunting**

となります。

通常の`CQ: First`や、通常CQ RUNでのAutoSeq 2 no-progress処理は、今回のP6 Hunting復帰処理とは別であり、従来どおりです。

---

## ダウンロードとSHA-256

### Windows GUI packages

| Build | File | SHA-256 |
|---|---|---|
| Standard GUI | `WSJT-X_20260901A-REB522-P6_win64.zip` | `d69ef54fb7d10feb3a7bc9620497eda8ec40c700f08f4d5302e8e016a02e992b` |
| AL GUI | `WSJT-X_20260901A-REB522-P6-AL_win64.zip` | `658db59666b89ae4884365e5ba55087b234b29aaa0cf7950fee80fcb2ab800e7` |

### Source bundles

| Build | File | SHA-256 |
|---|---|---|
| Standard source | `WSJT-X_20260901A-REB522-P6_source_bundle.zip` | `86e53df77bacaa93fc16bed15aec8e8ae1529231df16873486dacdb619803e2c` |
| AL source | `WSJT-X_20260901A-REB522-P6-AL_source_bundle.zip` | `8ecb9f4d6ec4763a2eb03f7d33a1971466263b7435a7efc491e56b8365a1c1f4` |

各fileに対応する`.sha256` sidecarも用意しています。

**Download:**  
https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6

---

## User Guide Edition 1.8 — 16言語

P6 / P6-ALのUser Guideは以下の16言語で用意しています。

- 🇯🇵 日本語
- 🇬🇧 英語
- 🇫🇷 フランス語
- 🇪🇸 スペイン語
- 🇩🇪 ドイツ語
- 🇨🇳 中国語（簡体字）
- 🇹🇼 中国語（繁体字）
- 🇰🇷 韓国語
- 🇵🇹 ポルトガル語
- 🇮🇹 イタリア語
- 🇳🇱 オランダ語
- 🇷🇺 ロシア語
- 🇵🇱 ポーランド語
- 🇹🇷 トルコ語
- 🇸🇪 スウェーデン語
- 🇮🇩 インドネシア語

**English Edition 1.8を、多言語版の意味上のmaster**としています。

User Guideでは、installation、Standard / ALの違い、AutoSeq 2/3、Wanted/Hunting、Terminal Hold、manual takeover、Best S&P、DF behavior、diagnostics、known limitations、Public RC precautionsなどを解説しています。

すべてのcurrent guide fileはP6 release pageから入手できます。

https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6

---

## Public RCとしての注意

P6 / P6-ALは**Public Release Candidate**であり、GA / stable releaseではありません。

初回試用時には、

1. 現在正常に動いているinstallationを残す
2. 新しい別folderへ展開
3. Standard / ALを混在させない
4. 別の`--rig-name` profileを使用
5. settingsとlogsをbackup
6. callsign、grid、rig、PTT、audio、reporting、loggingを確認
7. 生成されるTx message、DX Call、Auto Tx状態を監視
8. 無人・無監視運用をしない
9. 異常があれば直ちに送信停止

を推奨します。

自動選択機能を使用していても、送信内容と法令遵守についての責任は運用者にあります。

---

## 既知の制限・現在調査中の項目

P6ですべての既存問題が解決したとは考えていません。

現在のknown itemsには、

- `F/DB6LL`のようなprefix-form slash callのRR73処理は、まだ完全ではない
- `jt9.exe`のintermittent SIGSEGVは別件として未解決
- **“Highlight also messages with 73 or RR73”**に関する報告は引き続き調査中
- `--language=es`では、新規未翻訳UI stringの一部が英語ではなく日本語で表示される場合がある
  - QSO logic / transmitted messageには影響しない
- Fox/Houndは主要なmodification/test scopeではない
- FT8/FT4向けprotectionやscore-mode ruleがMSK144などでも完全に同一とは限らない

などがあります。

Public RC validationに合格していることは、**すべてのmode、setting combination、boundary conditionを完全に試験済みである**という意味ではありません。

---

## 不具合報告について

想定外の動作を見つけた場合は、可能な範囲で以下を添えてください。

- Standard / AL
- title barに表示される完全なversion identifier
- Windows version
- modeと関連settings
- Wanted Pounce / Huntingがarmedだったか
- Quick Call ON/OFF
- 発生UTC時刻
- 期待した動作
- 実際の動作
- 関連する`ALL.TXT`
- 必要ならscreenshot
- 必要に応じて`wsjtx_log.adi`

再現調査を行う場合は、User Guideに記載されているJP1LRT diagnostic recording optionを有効にしてください。

Logにはcallsign、locator、frequency、timestamp、内部operating stateなどが含まれる可能性があります。公開前に必ず内容を確認してください。

---

## 開発背景・関連記事

### Decoder解析 — 16言語

**WSJT-X 3.1 improved の FT8 デコーダー設定を理解する**

[🇬🇧 English](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_en.html) | [🇯🇵 日本語](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ja.html) | [🇫🇷 Français](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_fr.html) | [🇩🇪 Deutsch](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_de.html) | [🇪🇸 Español](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_es.html) | [🇨🇳 简体中文](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_zh-cn.html) | [🇹🇼 繁體中文](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_zh-tw.html) | [🇰🇷 한국어](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ko.html) | [🇵🇹 Português](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_pt.html) | [🇮🇹 Italiano](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_it.html) | [🇳🇱 Nederlands](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_nl.html) | [🇷🇺 Русский](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ru.html) | [🇵🇱 Polski](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_pl.html) | [🇹🇷 Türkçe](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_tr.html) | [🇸🇪 Svenska](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_sv.html) | [🇮🇩 Bahasa Indonesia](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_id.html)

---

## Upstream projectsへの謝辞

JP1LRT Editionは、アマチュア無線softwareのupstream communityが積み上げてきた成果があるからこそ存在しています。

- **WSJT-X**  
  https://wsjtx.sourceforge.io/

- **WSJT-X Improved by Uwe Risse / DG2YCB**  
  https://sourceforge.net/projects/wsjt-x-improved/

- **JTDX**  
  https://sourceforge.net/projects/jtdx/

JP1LRT Editionは**独立したmodified edition**です。

WSJT-X、WSJT-X Improved、JTDXいずれのofficial releaseでもありません。

本projectはGPL licenseのWSJT-X / WSJT-X Improved系codeをベースとしています。binaryとともにcomplete source bundleを公開しており、適用されるlicense termsについてはsource bundle内のlicense / copyright noticeを参照してください。

WSJT-Xのoriginal authors / contributors、Uwe / DG2YCBとWSJT-X Improved community、そしてJTDX developers / testersに心から感謝します。

彼らの成果と運用思想がなければ、このprojectは存在しません。

---

## JP1LRTについて

**津久浦慶治(つくうら　よしはる) / JP1LRT**

- 1983年開局
- JTDX authorized beta tester
- JTDX日本語ローカライズ担当
- WSJT-X Improved JP1LRT Edition developer / maintainer

私が重視しているのは、**自動化そのものではありません。**

FT8/FT4運用を、**より予測可能で、より実用的にすること**です。

> 進行中QSOを守る。  
> Terminal handlingを守る。  
> 運用者による意図的な手動操作を尊重する。  
> 次の相手を賢く選ぶ。  
> そして運用者がWanted局を待つと決めたなら、その状態へ正しく戻る。

73,  
**[津久浦慶治 / JP1LRT](https://www.qrz.com/db/JP1LRT)**
