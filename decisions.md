# DECISIONS — asclepius

| ID | 日付 | 決定内容 | 理由 | 却下した選択肢 |
|---|---|---|---|---|
| D-001 | 2026-08-06 | GATE-C 10.7/15 WARNING で進行 | WARNING主因は蓄積証拠0件とベンダー3系統依存であり構造欠陥ではない | 再設計（不要と判断） |
| D-002 | 2026-08-06 | L0=閉ループ1周の機械判定（候補B） | A（行動習慣）とC（件数蓄積）はBの部品。C単独は埋立地リスク | 候補A / 候補C |
| D-003 | 2026-08-06 | why/box/decisions を暫定的に本repo docs/asclepius/ に配置 | Claude直接push可能レーン（WS-AXIS-11例外＋outbox）で即時保全。project-os-metrics への正本登録は後続cco/PRで実施 | project-os-metrics 即時起票（cco往復コスト） |
| D-004 | 2026-08-06 | repo名は project-asclepius（Suiru作成名を採用） | 実在repoが正 | asclepius |
| D-005 | 2026-08-06 | 学習(SFT/RL)は T+6ヶ月条件成立まで着手禁止 | 設計書§15/§20・評価基盤先行原則 | 早期SFT |
| D-006 | 2026-08-06 | PR#1（goal AS-01）close=正当・PR#2（ledger追記）はmain反映済確認 | PR#1は軸ドリフト（AS-01自身が破棄を記帳）。PR#2の全記録はmain ledger blob 5463d4cに現存・損失ゼロ | PR#1の復活 |
| D-007 | 2026-08-06 | 本repoの軸は AS-FOUND-01 単一。並行スレッドは新規軸起票前に goal/ の存在確認必須 | 同日並行セッションの競合軸起票（B3\|AS-01\|12:36 の再現条件）の再発防止 | — |
| D-008 | 2026-08-07 | 非支配性・作用能力 統合設計 v0.2.1 を os/ へ採用（失効 2026-11-05・延命条件=判断変更の実測1件） | §6-2補足により文書は即日適用可。ただし失効条項必須。v0.2 candidate の欠落3点（失効条項なし/Exit床未定義/発信力の取得判定なし）を補修し、F5・T26・T25再記述の3定義を参照化 | 8週N=1検証待ち（文書に不適用）/ Asclepius v4.9 本体への即時追記（延命条件成立前）/ 失効条項なしでの採用 |
| D-009 | 2026-08-08 | 可能性判定は前例ではなく制約層で行う。上から順に4問、最初に詰まった層で確定（①物理・数学で詰まるか ②直列潜時の合計が期限を超えるか ③残る制約は多数が試して全員失敗したものか ④残ったのが制度・慣行だけならやってよい） | 「誰もやっていない」の大半は制度・慣行であり物理的不可能ではない。前例基準はL5とL0を区別できず機会を捨てる。ただし多数が試して全員失敗している場合のみ前例の不在が強い証拠になる（3の法則: n試行0件なら発生率の95%上限は約3/n）。直列潜時のみ資源で圧縮できないため別枠で確認する。本規則は着手の許可であって推奨ではなく、優先順位は別途決める | 前例・base rate による可否判定（L5をL0と誤認する） / feasibilityシートの事前設計（反復成立前の資産化。検証は ASC-FEAS-01 判定日 2026-09-04 まで保留） / 理論上限を所要時間の見積りに流用すること（必ず楽観に振れる） |
| D-010 | 2026-08-09 | **取下げ。**「正本を repo main 直読に切替、PK再アップロードを廃止」として起票したが、同内容は `docs/rules/git_pk_sync.md` v1.1（2026-08-07）で既に決着済み。重複のため取下げ。規則の正本は v1.1 | 古い PK コピー（v1.0）だけを見て既存 v1.1 を確認せず、`docs/asclepius/git_pk_sync.md` を新規作成した（commit d52c80c、335a93a で削除）。**「正本を確認せずに書く」という、まさにこの規則が防ぐはずの事故を起こした** | — |
| D-011 | 2026-08-09 | セッション開始時の手順0 として `docs/doc_map_{project}.md` の repo main 直読を置く。doc_map を入口とし、列挙された正本を repo から取得する | KERNEL K0.7 は `docs/kernel/` 固定で workspace-template 前提。project-asclepius に `docs/kernel/` は存在せず空振りする。doc_map は各 repo が自分の地図を持つ形式ですでに存在し、ディレクトリ構造が repo ごとに違っても壊れない。また Asclepius は KERNEL を持たないプロジェクトのため、KERNEL 側の改訂だけでは届かない。同一文面を各プロジェクトの Instructions にも置く | `docs/kernel/` を全repoに新設（ディレクトリ構造を揃えるコスト） / KERNEL のみに記載（KERNELを持たないPJに届かない） |
| D-012 | 2026-08-09 | 自動化可否の一般則は事前に自作しない。判断が発生した時点で「①可逆か ②機械が正誤を返すか ③何回目か」の3問で1行判定し本欄に記録。5件溜まったら圧縮を検討（5は仮置き・根拠なし） | 反復0件での分類ナレッジ構築は反復成立前の資産化にあたる。既存実証（Parasuraman/Sheridan/Wickens 2000 の4段階、Bainbridge 1983、Fitts 1951）と T1〜T6・AI出力規則が同型であり、一般論を自作しても repo の既存結論に戻る。置き場所は事前設計せず、摩擦の実測が起きた場所で決める | 分類ナレッジ・カードの事前作成（反復0件） / 一般化議論の継続（分布中心の再導出） / 新規DB・レジストリ（ASC-GATE-01: 台帳1本） |
| D-013 | 2026-08-09 | 全文書を定義層（上書き更新・repo実在41本）と判断層（追記のみ・`docs/asclepius/decisions.md` 1本）の2層に分ける。判別基準は「上書きされるか、追記されるか」。定義層は薄く保ち、資産化は判断層でのみ行う。`decisions.md` の表→ブロック形式の全件移行は本決定に含めず分離する。予測と判定日は §予測と判定 に記載 | 文書という器は選択の最終結果だけを残し、棄却案と外れた予測（＝最も価値の高い部分）を構造的に落とす。外部研究の引用は学習分布内であり私有性を持たない。ゆえに doc_map への未登録分の登録だけでは資産性に効かない。判断層を新規DB・新規ファイルにすると `sot_boundary_v1.md` の既存分界と二重管理になり、T25（OS自己目的化）の再演になる。既存2ファイルの改訂だけで実装できるのは二層分離のみ | ① doc_map への未登録分の登録のみ（参照精度は上がるが資産性に効かない） / ③ 判断層を新規DB・新規ファイル化（sot_boundary と二重管理・T25再演） / ④ D-001〜D-012 全件のブロック形式移行を同時実施（内容が repo 原文と未照合のレコードを含めて「追記のみ原則の一度きりの例外」を使い切ることになる） |
| D-014 | 2026-08-09 | Deep Research 成果（長期優位性の効果量比較）を `os/長期優位性エビデンス_v1_0.md` として evidence 層に固定し、doc_map 分類5（参照専用）に登録する。行動規則を持たせない | 既存OS各所へ分散追記すると同一知見が3文書に散り版ズレの種になる（BIOS 85件参照事故と同型）。保存しなければ散逸し、それは why.md の L-1 が名指す Problem そのもの。薬理エビデンス v5.0 と同じ 6ヶ月レビュー運用に乗せる。§6-2補足により即日適用可。8週検証は生理指標に介入しない参照文書のため不要 | ② 既存OS各所（睡眠OS・環境身体OS・学習OS）へ分散追記（版ズレの種） / ③ チャット成果物のまま保存しない（散逸） |
| D-015 | 2026-08-09 | 構造層パッチ v0.2 を `os/構造層パッチ_v0_2.md` として正本化し、v0.1 を BLOCKED として置換する（失効 2026-11-09・延命条件=5問が判断を変えた実測1件）。未処理の波及2件を v0.2 §5 に明記して残す | 2026-08-01 の敵対的査読2本（ChatGPT/Gemini）が独立に BLOCK 判定。確定した誤りは5件で、特に「正解の観測＝撤退シグナル」は Bloom et al. 2013（公知の lean 導入のみで生産性17%改善）が反証しており、運用すると睡眠・運動・セキュリティ等の既知高収益投資を切る誤作動を起こす。また「AI委譲不能3機能」は作成者（LLM）の自己申告であり検証不能なため、権限・責任・同意ベースへ置換した。**BLOCK 判定は 8/4 の本体統合作業に伝播せず、v0.1 が `os/Asclepius_v4_9_統合版.md` L4直下および `os/領域判定軸_Claude委譲境界_v0_1.md` の上位参照として現在も生きている**（v0.2 §5 に記載・未修正） | v0.1 の部分修正（分類モデル自体が破綻のため不可）/ v0.1 の削除（査読の実例としての価値を失う。BLOCKED 表示で保持）/ Asclepius v4.9 本体の即時全文書き換え（130KB・MCP経由では context 上不可。別手段が要る） |
| D-016 | 2026-08-10 | 物理データ収集機器の購入を**見送る**。再判定日 2026-09-06（既存チャネルの自動着地が7日連続で成立した最初の日 2026-08-16 を最短起点とし、Notion カードの期限に合わせて 09-06 を上限とする）。ActivityWatch（¥0・Mac ローカル）のみ7日縛りの対象外として別枠 | Notion カード 3b58fe7d-cd4d-8125-9687-dfa0d76d19ea の失敗条件が逐語「既存チャネル（git/ledger/obs/Oura/Notion）の自動着地が7日連続で成立していない間は購入しない。新チャネル追加より既存チャネルの通電が先（データが入らない機器は買っても資産にならない）」。2026-08-07〜08-09 は `inbox/` 消失により collect が commit を積んでおらず連続日数は0だった。PR #11 で復旧し 2026-08-10 に3系統が着地したため、連続カウントの起点は 2026-08-10。**本レコードは Orchestrator の裁量判断ではなくカード定義による機械的確定である** | 即時購入（失敗条件に抵触）/ 7日条件の緩和（条件を結果を見てから書き換える行為にあたる）/ 判定の先送り（起点が確定した以上、記録しない理由がない） |
| D-017 | 2026-08-10 | 人間時間の委譲・保持判定を `os/人間時間_委譲保持パッチ_v0_1.md` として期限付き運用し、構造層 v0.2 §2 の下位に置く。固定禁止リスト・新規台帳は作らない | D-012 の圧縮条件だった実判断5群（買い物／カフェ実装／単発移動／反復家事・待機／定型事務）が揃った。既存構造層は2ページ上限、Integrated Architecture は章順序要照合のため直接増補せず、薄い失効可能パッチに分離する | Integrated Architecture §7.2-A へ直接統合（要照合ファイルを拡張）/ 構造層 v0.2 を増補（同書の2ページ上限違反）/ decisions のみで定義を作らない（5群を横断する再利用規則が散逸）/ 行為別の固定禁止リスト（BIOS v2.8 個別結論禁止・T25） |
| D-018 | 2026-08-12 | 生産性・改善率・自動化・再帰的自己改善を、独立した軸・指標体系として定義層に追加しない。命題1文と観測1つに圧縮し、判断層のみに記録する。命題:「単位時間あたり、外部判定が返る決定の回数を最大化し、その回数を人間の注意で律速させない」。観測は「週あたり、外部判定が返った決定の件数」の1つのみ。定義層への昇格は判定日に週1件以上が成立した場合にのみ検討する | 週次件数の実測が現在0件であり、指標体系・プロトコル・軸の追加は反復成立前の資産化にあたる（Integrated Architecture §7.2-A）。既存正本に不足はない: 自動化の判定は構造層 v0.2 §2 と人間時間パッチ、再帰は terminal_state_v1 T6、複利は構造層 v0.2 Q5、生産量のL4指標化禁止は構造層 v0.2 §4 に既にある。外部案の4指標のうち EP・RU は Integrated Architecture §7.4「時間短縮」「知識複利」とほぼ重複し、HTO は人間時間パッチ §6 に既存で、新規は DR のみ。かつ記帳自動化が未着手（why.md L1）のため、人間注意時間と Human Touches を手で数えると測定自体が Human Touch を増やす。0→1 の段階に第3段階の道具を持ち込む形は doc_map 未整備 #17（創作OS: 評価器は完成・評価対象0で未稼働）と同型 | ① 生産性・改善率を L4 目的関数へ追加（構造層 v0.2 §4 が明文で禁止。産出量は資本で買える変数であり、2人側の優位である決定サイクル時間・選択肢集合とは別物）/ ② EP・HTO・DR・RU の4指標体系を導入（3つは既存の再定義。測定コストが測定対象を壊す）/ ③「Recursive Capability Compounding」を Integrated Architecture §7 へ追記（§7.2・§7.2-A・§7.4 と三重管理）/ ④ 熱力学的定式化として新規文書化（実体は制御理論の状態空間表現と資本蓄積式であり熱力学ではない。減耗率δの数値運用は構造層 v0.2 §4 のマクロ経済式・個人転用禁止に接触）/ ⑤ 記録しない（散逸し、why.md L-1 が名指す Problem そのものになる） |
| D-019 | 2026-08-12 | 基盤・能力・外部実現の区別を、新規OS・新規L層・固定配分率にはせず、`os/Asclepius_Integrated_Architecture_v2_0.md` §2.3の「次の選択可能な認知時間」に対する直交的な限界配分モデルとして期限付き採用する。EはL4から外部Validatorへの接続面でありL5ではない。2026-11-10自動失効、延命条件=この分岐が実際の資源配分を変えた実測1件 | 既存L1〜L5は対象の存在論的な層、今回のB/C/Eは追加資源の行き先であり、同じ軸ではない。新規OSは定義層を増殖させ、3層化はL0/L5を落とし、10/30/60固定比率は総ポートフォリオ配分と限界配分の分母を混同する。既存§2.2 ROI式直後なら、新しい縦層を作らず§6.1・§11.1を参照できる。関数形・最適配分率は未検証（確度D）のため失効条項を付ける | ① 新規OS作成（定義層増殖・T25）/ ② 既存L1〜L5を基盤・能力・外部実現の3層へ再分割（L0/L5消失・軸混同）/ ③ 10/30/60の固定比率（根拠なし・§10.1との分母混同） |
| D-020 | 2026-08-12 | 限界値台帳（4種別・7項目）を propose と measure の外部基準として採用する（`docs/design/limit_ledger_v0_1.md`・失効 2026-11-12・延命条件=限界値が実際に採用案を変えた実測1件）。G5（観測効果／既知最大の比）は新規指標体系・新規台帳・新規軸を作らず、既存台帳から比を1つ計算する `scripts/limit_ratio.py` に留める。記録先は既存の Notion Task DB カード本文とする。健康・身体指標には §H を適用し、種別1（生理・構造限界）を到達目標ではなく危険境界として扱う | 議論の錨が「自分と対話相手が思いつく範囲」に固定される問題に対し、外部の到達点を先に置く。D-018 が禁じるのは指標体系・プロトコル・軸の追加であり、既存台帳から比を1つ導出することは新しい観測対象を増やさないため抵触しない。健康領域では技術領域と逆に「限界に近づくことが害になる」ため、形式が意図を上書きしないよう §H2 で「少ないほど良い」方向の極値の登録を禁じた。移植の副産物として H5 が確定した——不眠の多面的治療では効果量の 65.9%（95%CI 49.3-82.5）がプラセボ条件で生じるため（pubmed 31725474）、対照を持たない n=1 の観測は内訳を分離できず、**OLR が高いことを「介入が効いた」の証拠として扱えない**。これは L0 に対する構造的制約であり、台帳を入れなければ見えなかった | ① 全タスク・全カードに限界値フィールドを付ける（BL-3 で却下済みの「常時ONの改善パイプライン」と同型。Layer0 Hidden Shift の 3.5か月0件が実測前例）/ ② タスクごとに都度リサーチを走らせる（工数がタスク数 N に比例する。限界値は軸単位で再利用できるため正しい比例先は軸数 M であり M ≪ N）/ ③ 種別3（集団参考値）を出力から抑止する（Orchestrator 推奨だったが Suiru 決定により4種別すべて出す。錨下げリスクは提示規則で押さえる）/ ④ OLR の隣に「限界値到達率」を新規 KPI として置く（D-018 の指標体系追加に該当）/ ⑤ `--exclude-achiever`（薬物除外オプション）の先行実装（使用実績0件・反復成立前の資産化）/ ⑥ 陳腐化上限をグローバル定数のままにする（医学のメタ分析4件が90日上限で全件警告になり、警告が意味を失った・実測） |
| D-021 | 2026-08-12 | D-018 の中核（独立した生産性軸・新規指標体系を作らない）を維持し、D-018 の適用だけを5点補正する。① G2 を正本 §7.2-B の原文「予測が結果より前に書かれる」へ訂正 ② 観測量を Outcome Linkage Rate（OLR）とは別の「G1〜G3適合決定の週次確定数」とする ③ 1件のカウント単位と計上週を固定する ④ 判定不能な自動化の副次予測を判定対象外とする ⑤ 未達時の結論を「閉ループ運用が成立しなかった。律速要因は未同定」までに限定する。D-018 は撤回・書き換えしない。**起票時（PR #74）は D-020 として提出されたが、AS-LIMIT-01 の限界値台帳が先に D-020 として main へ着地したため D-021 へ採番し直した** | ①は正本との照合で確認された転記誤り（確度A）。訂正方向はカウント対象を増やす緩和だが、基準改定ではなく原文照合による訂正であり、かつD-018対象件数0・結果観測0の時点で行う。②は既存OLRが `decision_id` と outcome の接続全体を母集団とし、G1〜G3・Notion事前予測・週次確定を条件にしないため。同一指標名では集計不能。③はDRを追加せずカード分割による水増しを抑えるため。④は具体的介入・基準期間・比較期間が未定義で記入規則3を満たさないため。⑤は未達から機会不足・記録漏れ・期限内未確定・時間不足・未適用を区別できないため | ① D-018 の書き換え・撤回（追記のみ原則違反）/ ② 補正しない（正本との不一致を残す）/ ③ OLRの分子または「結果接続済み決定」と呼ぶ（母集団が異なり、既存OLR 0.333と比較可能だと誤認させる。PR #75 の案・close 済）/ ④ DRを第1段階から追加（D-018の段階設計を変更する）/ ⑤ 補正自体の効果を測る新規予測を置く（新規介入ではない転記訂正を成果化しT25を増やす） |
| D-022 | 2026-08-12 | Project Knowledge を全削除し、**空を定常状態**とする。GitHub MCP が利用不能になった場合は、repo main から必要なファイルのみをダウンロードして PK へ投入する**オンデマンド復旧**に切り替える。`docs/rules/git_pk_sync.md` v1.2 の本文は改訂しない（同規則は既に PK 再アップロードを任意としており、本決定は失効条項のフォールバック手順を具体化するにとどまる） | v1.2 が「repo main が唯一の正本。PK は検索用キャッシュであり正本性の条件から除外する」と定めているため、全削除で壊れるトランザクションは無い（確度A・正本逐語）。加えて干渉2件を実測した。① PK に `doc_map_asclepius.md` が2本（176行 / 66行）並び、repo main 現行版 SHA 4bcbf72 とも不一致で、**入口ファイルが3版に分裂**していた（v1.2「古い版を必ず削除する。同名でも上書きされず二重に並ぶ」の警告が現実化した状態）。② PK 37件に `decisions.md` `ALREADY_RUNNING.md` `git_pk_sync.md` `創作OS_v1_2.md` `構造層パッチ_v0_2.md` limit_ledger 2本 `governance/` 3本 ほか15本以上が不在で、**欠落分は 2026-08-12 の誤判定3件の原因ファイル（ALREADY_RUNNING.md）を含む**。PK 検索で満足する経路は、その欠落パターンを構造的に再演する。未整備#1 の実害2件（D-008 の上書き未遂 / D-008〜D-011 を消す引き継ぎ案）も同型。削除は不可逆ではなく repo から復元できるため、可逆性の観点でも保持する理由が弱い | ① 全削除→repo main から現行52本を再アップロード（PK 更新という手作業が定常化し、v1.1 が「完了条件から人間を外す」として外したはずのボトルネックを再導入する。かつ再アップロードした瞬間から陳腐化が再開し、干渉①②の原因が消えない）/ ② `doc_map` の重複2本のみ削除（版の分裂は直るが欠落15本以上が残り、干渉②の主因が残る）/ ③ 現状維持（干渉2件を実測した以上、記録せず据え置く理由がない）/ ④ v1.2 本文を「PK は空を正とする」へ改訂（v1.2 は既に任意と定めており、追記は二重管理・T25）/ ⑤ PK の代替として repo 側に検索用インデックスを新設（新規台帳・ASC-GATE-01 違反。かつ検索劣化の実測0件での資産化）/ ⑥ PK を残したまま Instructions で「PK を読むな」と縛る（規則文で縛る対象を物理的に消せる場面で規則を増やす選択。§10 の「repo 正本の再記述は即削除」と逆行する） |
| D-023 | 2026-08-14 | 感覚運動技能獲得は新規独立OSを作らず **CANDIDATE** として判断層に固定する。初回N=1は技能指標の変化・保持・転移の観測に限定し、プロトコル固有の効果とは判定しない。`os/学習OS_v2_5.md` への Additive-first 昇格は、通常練習との比較または同等の因果識別により本プロトコルが次の練習設計・技能学習判断を変えた実測が得られた場合のみ検討する | 公刊知識を新規OSへ再記述すると定義層増殖とT25を再演する。チャットだけに残すと採否・棄却案・昇格条件が散逸する。初回前後比較だけでは通常練習・課題慣れ・日間変動を分離できないため、観測と因果判定を分ける | A: 新規 `感覚運動技能OS` を作る / C: repoへ残さない / 初回N=1だけで既存学習OSへ昇格する |
| D-024 | 2026-08-14 | 認知能力15変数マップの運用正本は `os/Asclepius命題達成ロードマップ_v1_3_AppendixC.md` C-1 に置く。旧8基盤は互換層として保持し、旧★点・投資対効果順位は旧版参考に降格する。`Asclepius_v4_9_統合版.md` / `学習OS_v2_5.md` / `Suiru_Modeling_v1_0.md` / 新規独立OSには重複定義しない | Appendix C が既に L4 認知基盤×活動評価の責務を持ち、15変数はその精緻化に該当する。v4.9 は130KB級かつ BLOCKED 構造層が残る。学習OSは実装プロトコル、Suiru_Modelingは個人観察モデル、新規OSは定義層増殖になるため責務が合わない | B: `Asclepius_v4_9_統合版.md` / C: `学習OS_v2_5.md` / D: `Suiru_Modeling_v1_0.md` / E: 新規独立OS・新規設計文書 |
| D-025 | 2026-08-14 | 抽象化階層・知識深度配分を新規OSにせず、既存 `os/学習OS_v2_5.md` v2.5.1 の Section 5.5 P8 として期限付き採用する。学習対象を Own / Literacy / Externalize に配分し、現在の抽象化でボトルネックを説明・修正できない場合だけ Bottleneck Descent し、介入後は Re-ascent する。Section 1の日次ルーティンは増やさない。再判定 2026-11-14、延命条件=本規則が実際の学習深度配分を1件以上変え、不要な深掘り回避またはボトルネック解消に寄与した実測 | 現行学習OSには「何を学ぶか・どう学ぶか」はあるが、有限な認知資本をどこまで内部化するかの停止規則が明示されていない。低レイヤー全習得は準備90%・実装10%とT25を再演しやすい一方、全外部化ではAI出力の検証とボトルネック同定ができない。深度を3段階に分け、Representation / Cost Model / Failure Mode / Escape Hatch をLiteracy以上の最低要件にすると、必要な深さだけを保持できる。Depth Value式は科学公式ではなく点数化しない設計ヒューリスティックとして扱う | 新規「低レイヤーOS」作成 / 数学→binary→hardware→OS→language→AIを全て事前にOwnする / P8を日次ルーティンへ追加する / Kimi・DeepSeek等の人物・企業固有知識を正本化する / API引数・CLIオプション・opcode表等の容易に再取得できる事実を暗記する |
| D-026 | 2026-08-15 | 反復的な日常・定型デジタル処理を機能単位で `BUY / THIN INTEGRATION / BUILD-OWN` に分ける。汎用能力は品質・安全・可搬性を満たす既製品を既定とし、接続はadapter・最小権限・変換・停止条件だけを薄く作り、objective・Evaluator・policy・権限境界・採否・判断→実装→結果履歴・個人学習は所有する。初回適用として、Inoreaderは汎用収集・更新監視・未読・通知の購入候補、WIPは汎用収集を増築せずAsclepius固有の採否・実装変換・結果追跡を保持、ChatGPTは問題設定・設計・重要判断・統合の主軸、Claudeは境界明確な高速実装で監督込み純価値が正の場合だけ補助、Feedly Market Intelligenceは現在の2人体制では過剰、Readwise Readerは長文処理の実測ボトルネックまで保留とする。WIPの汎用収集増築停止を購入/内製判断の変更1件として記録する。失効日は人間時間パッチの2026-10-05を継承する | [実測] WIP・収集パイプラインで汎用配管の保守、失敗検知、仕様追随が人間時間を消費している。[文書] 人間時間パッチにAV・N*・HTO、構造層v0.2 §2に権限ベース委譲境界があり、新規OSなしで接続できる。[推定] ベンダー交換後にも残るpolicy・Evaluator・結果接続へ内製を限定すれば、保守負債とロックインを同時に抑えられる | 全面自作 / objective・Evaluator・履歴まで外部化する全面SaaS / 同一汎用機能の重複購読・無期限二重運用 / WIP削除またはInoreaderへの即時全面移行 / 製品名・価格・仕様を定義層へ固定 / ChatGPTまたはClaudeへの実行固定 |
| D-027 | 2026-08-15 | C1〜C10を能力機構として維持し、Capability Residency（Individual / Team-Organization / External Resource / Hybrid）と、会社・個人ロードマップ由来のMission Domainを直交させる。完全性は「全人間能力の普遍的網羅」ではなく、現行ロードマップ主要項目が3軸へ写像済み、または理由付きUNMAPPEDである状態とする。外部能力獲得はTarget / Capability delta / Reality connection / Continuity / Compounding / Residue after exit / Portability / Calibration / Ownership boundary / Stop conditionの10項目で判定し、費用は主目的ではなく継続可能性・破局回避・機会費用のgateとする。初回製品判断は、Inoreaderを市場・技術感知の汎用収集能力として **ADOPT-DECIDED / OPERATIONAL-UNVERIFIED**、Zoteroを根拠・書誌・出典接続の外部能力として **ADOPT-DECIDED / OPERATIONAL-UNVERIFIED** とする。InoreaderはBuy + Thin IntegrationでWIPへ一方向接続し、採否・実装変換・結果追跡はWIP側へ残す。ZoteroはExternal Resource + Thin Integrationとし、出典と判断の関係はAsclepius側へ残す。契約、インストール、権限、データ移出の実査は未実施であり、運用開始を意味しない。ChatGPT / Claude / WIP / Feedly Market Intelligence / Readwise Readerの状態はD-026を継承し、未明示製品の採否は確定しない。 | [文書] Capability Architecture自身がC1〜C10の網羅性未検証を明記し、Integrated Architecture・学習ロードマップ・資本エンジン計画には身体基盤、関係・創作、Growth、顧客運用、組織統治、資本、Frontier参加が存在する。[Suiru判断] 製品カテゴリでなく獲得すべき個人・会社能力として分類し、明示した2候補を採用する方針が承認された。[推定] 能力機構・所在・用途を分け、終了後の残存資産を必須にすると、ツール増殖と固有判断の外部化を避けながら、短期コストでは捉えにくい能力差分を比較できる | C1〜C10を普遍的完全分類と断定 / 新しいC軸・新規能力OS・新規DB・ツール台帳・総合スコア / 空セルを埋めるための採用 / 製品機能を能力そのものとみなす / 契約・導入未確認をOPERATIONALと記録 / 未明示製品の一括採用 |
| D-028 | 2026-08-15 | 技術実装、産業化、製造、AI、ロボティクス、インフラ、供給網、企業運用、Capability獲得、技術ロールモデルの外部参照では、中国を最初の参照圏とする。これはorigin priorityであってtruth priorityではない。中国語一次資料→中国国内の深掘り媒体による候補発見→中国内外の独立資料・失敗事例・制約による反証→翻訳provenance保持→PCEによるCapability Primitive化→実案件Decisionの順で扱う。米国その他地域はcomparison / counterevidence面として残す。既存C3文書 `docs/design/capability_architecture_v0_1.md` の明示Thought Railとして既存document intakeへ接続し、初期状態をUNTESTEDとする。C0 / C2 / NORMATIVE、既存Rail帰属、T6判定は変更しない。失効日は2026-11-15、延命条件は本Routeが実際の外部参照またはCapability獲得判断を1件以上変え、その差分がDecision / Action / Outcomeへ接続されること | [Suiru判断] 中国を主要な技術参照圏へ移す方針と本実装が明示承認された。[文書] D-027のExternal Capability Acquisition Protocolには外部能力の採否手順はあるが、参照圏の既定順序、原語一次資料、反証、翻訳provenance、PCE接続が未定義だった。[実測] mainには登録済みactive C2/C3/C4文書の明示RailだけをUNTESTED候補として扱い、最大1件、anti-trigger、promotion非算入を固定するdocument intakeが存在する。これを再利用すれば専用Router・schema・registryを追加せず接続できる。[推定] 参照順序を中国側へ動かしつつ独立反証を残すことで、英語圏経由で遅れて入る候補を減らしながら国籍を品質へ誤変換する偏りを抑えられる | 英語圏・米国中心の既定順序を維持 / China-onlyとして米国その他地域の比較・反証を除去 / 国籍・言語・所在地をevidence qualityまたはtruth scoreへ変換 / 人物台帳・国別ranking・総合scoreを作成 / 専用External Reference Router・source DB・schemaを新設 / 患者・服薬・法的助言・緊急停止・秘密情報を含む高損失Contextにも自動適用 |
| D-029 | 2026-08-15 | D-028をChina-onlyにはせず、China-firstを産業化・製造・供給網・ロボティクス・インフラ・企業運用の既定originとして維持しながら、問いのDomainに応じて米国（frontier AI・software・半導体・platform・宇宙航空・defense R&D・intelligence research）、Cambridge/英国（基礎科学・生命科学・学術研究・研究移転）、イスラエル（cybersecurity・defense technology・resilient operation・startup商用化）を最初の探索面へ置く。NASA、DARPA、IARPA、DoD研究機関、NSA、CIA、Unit 8200、Mossad等は公開済みの公式資料、公的記録、公開成果物、technical report、検証可能な公開証言、機密解除資料だけをcase materialとし、機密取得・不正アクセス・標的監視・武器化・秘密作戦の再現を対象外とする。全originへClaim–Source適合Gateを共通適用し、一次性 / Domain権威性 / 検証可能性 / 独立性 / Claim適合性 / 反証可能性を分離確認する。加重和・総合source score、新規source DB・schema・人物／組織台帳は作らない。D-028のUNTESTED・失効・延命条件を継承する | [Suiru判断] 中国だけでなく米国、Cambridge、イスラエル、Unit 8200、Mossad、NASA、NSA、CIA、その他防衛技術も収集対象とし、domain知識と一次情報を優先する基準の採用が明示承認された。[文書] D-028は中国語一次資料と独立反証を定めるが、claimの種類と資料が直接証明できる範囲、domain別origin、情報・防衛組織に対する公開・合法境界は未定義だった。[推定] 地域名や組織名を品質へ変換せず、claimに適合する原語一次資料と独立反証を要求すれば、複数frontierの比較可能性を保ちながら広報・転載・肩書を実能力と誤認するリスクを下げられる | China-only / US-only / 国・都市・組織名をtruthまたはqualityへ変換 / 情報・防衛機関の機密・非公開情報を探索 / 攻撃・監視・武器化の再現 / 同一発表の転載を独立根拠として重複計上 / 人物・組織台帳 / 加重source score / 新規Router・source DB・schema |
| D-030 | 2026-08-16 | AsclepiusをValue Authority、Workspace等の実行層をExecution Authorityとし、Reality ValueとStrategic Asset Qualityを分離する。Strategic Value Contractは `reality_value / commodity_status / exclusive_residue / defensibility_vector / ownership_boundary / option_value / reclassification_condition` を保持し、独占性をValueそのものへ昇格させない。`Residue after exit` は終了後の残存、`Exclusive Residue` はその残存のうち後発第三者が同等物を取得・再生成しにくい部分として分離する。Commodity能力はBuy / Thinを既定方向とし、価値あるExclusive Residueだけを内部保持できる構造を優先する。Exclusive ResidueはBuild-Ownを支持しうるが、既存AV / BuyValue / BuildValueと内製入場条件4件を全て維持し、自動Build命令にはしない。Commodity化・代替可能化時はBuild→Buy / Thinを再評価する。総合Monopoly Score / Strategic Value Score、新規DB・KPI・常時ON triggerは作らない。失効日2026-11-15、延命条件=本契約がBuy / Thin / Build / Partner / 資本配分の実判断を1件以上変え、その差分が既存decisions / ledger / outcomeへ残ること | [Suiru判断] 「AsclepiusとWorkspaceのパイプラインの価値関数に設定する」議論を経て、AsclepiusをValue Authority、WorkspaceをExecution Authorityとして実装する方針が明示承認された。[文書] D-026はBuy / Thin / Build、D-027はCompounding / Residue after exit / Ownership boundaryを持つが、「残ったものを第三者も同等に取得できるか」を独立に判定していなかった。[推定] Reality Valueを先に固定し、独占性を別ベクトルにすれば、無価値な希少物の所有や汎用能力の過剰内製を避けつつ、Rights / path-dependent history / relationship state / provenance等の残余へ資本を寄せられる | 独占性をReality Valueそのものにする / Workspaceにも同じ価値関数を複写して二重正本化 / Monopoly Score・Strategic Value Scoreによる固定重み総合点 / Exclusiveなら自動Build / コモディティ化した汎用能力・コードを「自作済み」を理由に保持し続ける |
| D-034 | 2026-08-19 | 新規Sovereign Agency OSを作らず、既存 `os/非支配性_作用能力_統合設計_v0_2_1.md` をSovereign Agency / Agency Capital の意味上の正本とする。同文書 §19 に `L4 → Sovereign Agency → Agency Capital / Resources → Action / Outcome` を明文化し、Autonomy / Non-Domination・Capability / Mastery・Influence / Effective Action・Optionality / Resilience を4軸のベクトルのまま保持して単一加重scoreへ潰さない。Agency Capital は「将来のSovereign Agencyを持続的に増加させる、所有または実効的に制御可能なストック」と定義し、資産・投資判定は `os/構造層パッチ_v0_2.md` の既存Q1〜Q5と資産2問を再利用して新scoreを作らない。`os/BIOS_v2_8.md` は定義本文を複写せずSection 2へinstrumental layerのpointerだけを持ち、Section 15の最低資本制約はAgency Capitalの一部として意味接続するがキャッシュフロー最大化へは変えない。`os/Part13_個人プロファイル_v0_2.md` 13-9 は Constraint-release / Capability / Influence / Positional の4 Signal をSignal / Fuel / State / Modifier としてのみ保持し、特に status / dominance は価値関数ではなくFuelとして扱いObjective / Truth / Priority Gate へ昇格させない。参照は project / portfolio・Build-Buy・委譲・Automation・学習・provider依存・資本 / Network・健康 / 長期基盤・Capital Formation の大きな分岐点に限るLensとし、日次・毎taskの強制判定を作らない。失効日は本体文書の2026-11-05を継承し、独立した失効条項を追加しない | [Suiru判断] 「その提案内容全て実装しましょうか！お願いします」および PR#273 exact head 25728e63 のH1承認により、既存上位命題への統合として明示承認された。[文書] D-008で採用済みの非支配性・作用能力は Non-Domination と Effective Agency を既に持つが、Capability / Mastery と Optionality / Resilience を含む統合語、および将来ストックとしての Agency Capital を定義していなかった。[実測] 4概念はすべて既存 §3 / §4 / §5 / §6 / §11 の再記述で表現でき、資産判定器は構造層パッチ v0.2 に既に存在するため、新規OS・新規scoreを追加せずに接続できる。[推定] 統合語を1本のSOTへ置き、下流をpointerに限定すれば、定義の二重管理とAgency scoreによる常時評価（Aモード落下）の両方を避けられる | 新規 `Sovereign_Agency_OS.md` の作成 / L4・terminal objective・`docs/asclepius/why.md` の変更 / Autonomy・Capability・Influence・Optionality の加重和による総合Agency score / Agency Capital 最大化の人生目的化 / status・dominance のNormative value化 / 全taskでのAgency強制評価・日次KPI・新規手入力Routine / 構造層パッチ Q1〜Q5 の再実装 / Project-OS・Workspace への意味本文の複写 |
| D-035 | 2026-08-20 | 新規Frontier OS・新規Persistent System・新規総合scoreを作らず、`docs/design/capability_architecture_v0_1.md` §11 Strategic Value Contract の下位に §11-9 **Frontier Growth Objective** を instrumental operating objective として追加する。Frontier Orientation（採択Domainの世界・宇宙規模の最前線への継続接触と、比較可能な軸でのfrontier gap観測）と Improvement Velocity（Reality Outcomeから Self / Capability / Allocation / Execution / World Model を更新する速度）の2つを同時に要求し、`frontier_domain_intent` / `frontier_reference_ref` / `frontier_gap` / `improvement_velocity` / `frontier_contact` / `reality_outcome_linkage` / `option_value` / `exclusive_residue` / `exploration_state` をベクトルのまま独立保持して固定重みの総合点へ潰さない。world / frontier evidence の本体は External Reality が所有し、Asclepius は immutable な `frontier_reference_ref` と自身のValue / Self / Capability差分だけを持つ。`世界一` は status・自己申告・単一ランキングではなく domainごとの外部成果と frontier evidence の比較としてのみ扱い、比較不能な領域は `UNKNOWN` を許す。測定は全Actionへ強制せず、結果によって次回判断が変わり得る有意味なInterventionだけを Outcome まで閉じ、判定は既存 `docs/design/terminal_state_v1.md` の T6 を再利用する。4 System は固定直列にせず、registered typed handoff により必要なnodeだけが発火する event graph として扱い、authority boundary と最小項目は `docs/design/world_adaptation_reference_v1.md` を正とする。`os/非支配性_作用能力_統合設計_v0_2_1.md` §19-9 は定義本文を持たず §11-9 への pointer のみを持つ。失効は §11 本体の 2026-11-15 と同時判定し、子契約だけを延命しない | [Suiru判断] 「世界一もそうだし、フロンティアを狙うモデルにしてください。現在の全てのパイプライン、システムを」「では、それで実装をしてください」および PR#274 exact head 2b747274 のH1承認により、既存Strategic Value Contractへの統合として明示承認された。[文書] §11 は Reality Value / Commodity Status / Exclusive Residue / Ownership Boundary / Option Value を既に持ち、Company portfolio に `Frontier participation` も持つが、最前線との差分観測と学習速度を判定変数として持っていなかった。[文書] `docs/design/terminal_state_v1.md` T6 は「更新後のproposeが更新前と異なる」を成立条件としており、Improvement Velocity の判定器は既に存在する。[文書] `docs/design/world_adaptation_reference_v1.md` が world-facing evidence の owner を External Reality と定め、typed intake の最小項目を既に定義している。[実測] 新規fieldのうち `option_value` と `exclusive_residue` は §11-2 の既存fieldであり再利用できる。新規に必要なのは frontier 側4変数と `exploration_state` のみで、新規DB・新規collectorなしで表現できる。[推定] Value Authority を1本に保ち下流を reference に限定すれば、4 repo への価値本文複写と、fixed-weight score による探索の早期棄却の両方を避けられる | 新規 `Frontier_OS.md` / `Growth_OS.md` / 第5の Persistent System の作成 / `世界一` を terminal objective・人生score・C0 NORMATIVE へ昇格させること / fixed-weight の Frontier Score・Growth Score・World #1 Score / 全Domainでの1位を目標にすること / 全Action・全会話・全Tool利用への Outcome 測定の強制 / 新規の日次スコア・ランキングDB・常時benchmark collector / world / frontier evidence 本文の Asclepius・Project-OS・Workspace への複写 / 4 System の固定直列パイプライン化 / §11 本体と独立した失効日を §11-9 へ持たせること / Asclepius から下流3 SystemのSOTへの直接write |

---

## 予測と判定（2026-08-09〜）

表形式のレコードは予測欄を持たない。予測を伴う決定は本節に追記する。

記入規則:

1. 追記のみ。過去のレコードは実測欄・差分原因欄への記入以外、書き換えない。
2. 入場条件は表と同じ。実際に検討した候補が2つ以上あること。事後的な候補のでっち上げは禁止。
3. 予測は判定可能な形で書く。判定日は先に固定する。
   判定日以降の予測・判定日の書き換えは、そのレコードを無効にする。
4. 実測欄は判定日に記入する。差分原因は「予測モデルの誤り / 確率的ノイズ」のどちらかを選ぶ
   （学習OS Module 7-5 と同じ問い）。
5. D-001〜D-012 の予測・判定日は「未記録」。記憶からの復元は捏造にあたるため行わない。

### D-013 | 2026-08-09 | S-tag: AS-FOUND-01

```
予測    : 2026-11-07 時点で、次の3条件がすべて成立している
          ① 判断層のレコードが 13件 → 25件以上
          ② うち「予測と判定」節に予測を持つものが 10件以上
          ③ 判定日を迎えたレコードのうち、実測欄が記入済みのものが 3件以上
判定日  : 2026-11-07
実測    : —
差分原因: —
確度    : D（便宜値）。D-001〜D-013 は全て 2026-08-06〜08-09 の4日間に作られており、
          平時のレコード生成率は未測定。25件という数字に根拠はない
反証    : ③が0件のまま判定日を迎えた場合、「二層に分ければ資産が貯まる」は誤り。
          原因は器ではなく判定を回す運用の側にあるため、doc_map §0 を破棄して別の方策を採る
```

### D-014 | 2026-08-09 | S-tag: AS-FOUND-01

```
予測    : 次回レビュー（2027-02-09）時点で、`os/長期優位性エビデンス_v1_0.md` を根拠に
          引いた判断が decisions.md に 1件以上存在する
判定日  : 2027-02-09
実測    : —
差分原因: —
確度    : C。参照専用文書が実際に引かれた回数の実績は未測定。
          薬理エビデンス v5.0 も同型の未測定状態にある
反証    : 0件なら参照層としての価値なしと判定し、削除を検討する。
          同時に「Deep Research 成果を evidence 層に固定する」方策自体を見直す
```

### D-015 | 2026-08-09 | S-tag: ASC-BLOCK-01

```
予測    : 2026-11-09 までに、v0.2 の5問（Q1破局回避 / Q2必需品 / Q3実装レント /
          Q4模倣後の残存 / Q5複利）を適用した結果、当初の直感と異なる結論に至った
          投資判断が 1件以上 decisions.md に記録されている
判定日  : 2026-11-09
実測    : —
差分原因: —
確度    : D。v0.1 は 8/1〜8/9 の9日間で適用実績ゼロ（BLOCK されたため当然だが、
          BLOCK 前の 8/1〜8/4 も適用ゼロ）。5問形式にすれば使われるという根拠はない
反証    : 0件なら本パッチを廃棄する。判定層に投資判断が記録されない原因は
          パッチの形式ではなく「投資判断そのものが decisions に上がってこない」
          運用側にある可能性が高く、その場合は形式をいくら変えても効かない

副次予測: 上記と独立に、v0.2 §5 の未処理の波及2件
          （Asclepius v4.9 本体 / 領域判定軸 v0.1）が 2026-09-09 までに修正されている
判定日  : 2026-09-09
実測    : —
確度    : C。130KB ファイルの編集手段が未確立のため、期日内に解決しない可能性がある
```

### D-016 | 2026-08-10 | S-tag: AS-FOUND-01

```
予測    : 2026-08-16 時点で、raw/ 配下に 2026-08-10 から 2026-08-16 までの
          7日連続の着地が成立している（git/ledger/obs/Oura/Notion の5チャネル）
判定日  : 2026-08-16
実測    : —
差分原因: —
確度    : C。inbox/ 復元（PR #11）で 2026-08-10 の1日は実測で通ったが、
          スケジュール実行（cron '30 20 * * *'）での連続稼働は未確認。
          2026-08-07〜08-09 の3日間はスケジュール実行が緑のまま無出力だった
反証    : 7日連続が成立しない場合、原因は inbox/ 以外にもう1つあることになる。
          その場合は購入見送りを継続し、collect の無声失敗検知（BL-ASC-05）を
          先に実装する。機器の追加は「データが入らない機器は買っても資産にならない」
          というカード自身の理由により、依然として先送りする

副次予測: claude-workspace トークンの有効期限 2026-09-04 を越えた時点で、
          GH_PAT を使う収集が全 repo 404 になり、workflow は緑のまま停止する
判定日  : 2026-09-05
実測    : —
確度    : B。トークン期限の存在は Fine-grained tokens 画面で実測済。
          期限切れ時の 404 化は GitHub の仕様として確定的。
          不確実なのは Suiru が期限前に更新するかどうかのみ
反証    : 停止しなかった場合、期限が延長されたか収集経路が変わったかのいずれか。
          いずれにせよ「無声失敗を検知する経路がない」という構造は残るため、
          BL-ASC-05 の必要性は変わらない
```

### D-017 | 2026-08-10 | S-tag: AS-FOUND-01

```
予測    : 2026-10-05 までに、本パッチの判定4問により人間実行から外した行動が1件以上あり、
          その回収時間と副作用が既存 ledger / obs / outcome のいずれかへ接続されている
判定日  : 2026-10-05
実測    : —
差分原因: —
確度    : C。スーパー訪問は現状1回30〜60分・ほぼ毎日との自己申告があり、
          代替案は具体化済み。ただし配送運用の実測、欠品頻度、回収時間の再配分先は未観測
反証    : 判断変更0件、参照負担の増加、固定禁止リスト化、新規管理作業の発生のいずれかなら
          パッチを削除する。時間回収が成立しても健康・関係・探索・満足を悪化させた場合は改訂する
```

### D-018 | 2026-08-12 | S-tag: AS-FOUND-01

```
定義    : 「外部判定が返った決定」とは、7.2-B の3問をすべて通るものをいう。
          G1 結果が90日以内に返る / G2 決定より前に予測が書かれている /
          G3 同じ結果を他者が観測できる。
          この3条件を満たさないものは件数に数えない。
          記録先は Notion Task DB のカード本文。新規台帳を作らない（ASC-GATE-01）。

予測    : 2026-09-30 時点で、外部判定が返った決定が週あたり1件以上に到達している
判定日  : 2026-09-30
実測    : —
差分原因: —
確度    : D。現在の週次件数は0件。1件という閾値に実測根拠はなく、
          0→1 の最小単位として置いた便宜値。平時の到達率は未測定
反証    : 到達しなかった場合、律速は「軸の不在」ではない。生産性・改善率・自動化を
          軸として意識しても件数が動かなかったことになるため、本命題を Asclepius から
          削除し、律速の同定（時間配分 / 案件そのものの不足 / 外部に出すことへの抵抗）
          へ切り替える。指標を増やす方向へは戻らない

段階    : 件数が動いた場合にのみ、次の道具を順に足す。先に足さない。
          0→1        : 件数のみを見る
          1→週3件    : 改善率 g（件数の対数傾き）が初めて定義できる
          週3件→2桁  : 較正精度（Brier）を足す。一桁での Brier は分散に埋もれる
          2桁以降     : HTO を足す。自動化の効果はここで初めて分離できる

副次予測: 上記と独立に、自動化を先行させた場合に週次件数は増えない。
          自動化の前後で件数が変わらなければ、その自動化は
          人間時間パッチ §8「自動化を作ること自体を成果に数えない」に該当し失敗とする
判定日  : 2026-09-30
実測    : —
確度    : D。自動化と件数の関係は本 repo で未測定。
          Evaluator が外部化されていない工程の自動化は、人間時間パッチ §1-2 により
          そもそも完全自動化の対象外である
```

### D-019 | 2026-08-12 | S-tag: AS-FOUND-01

```
予測    : 2026-11-10までに、§2.3のB/C/E分岐を使ったため、当初の配分先とは異なる
          行き先を選んだ実判断が1件以上、既存のdecisions / ledger / obsのいずれかに
          記録されている。新規台帳は作らない
判定日  : 2026-11-10
実測    : —
差分原因: —
確度    : D。乗算形、下限超過後の限界効用、1件という延命閾値はいずれも
          本repoで未検証。Van Dongen et al. 2003 は睡眠不足側のみを支持し、
          床を超えた後の配分規則を支持しない
反証    : 実測0件なら§2.3を削除する。実測があっても§6.1・§11.1だけで同じ判断に
          到達できた場合、C/E分岐の純増価値は0と判定し、期日前でも削除する
```

### D-020 | 2026-08-12 | S-tag: AS-LIMIT-01

```
定義    : 「限界値を引いた」とは、goal に `限界値: {軸}` 行があり、
          その軸が docs/design/limit_entries.md に存在することをいう
          （scripts/limit_lint.py が exit 0 を返す状態）。
          「採用案が変わった」とは、限界値を見る前の案と後の案が異なり、
          その差分が decisions / ledger のいずれかに記録されていることをいう。

予測    : 2026-11-12 時点で、限界値を引いたことで採用案が変わった実判断が
          1件以上、decisions / ledger のいずれかに記録されている
判定日  : 2026-11-12
実測    : —
差分原因: —
確度    : D。台帳ヒット率も別解採用率も本repoで未測定。
          1件という閾値に実測根拠はなく、0→1 の最小単位として置いた便宜値。
          D-015 の反証構造（形式を変えても運用が起きなければ効かない）と同型のリスクがある
反証    : 0件なら台帳を削除する。原因は形式ではなく
          「propose 時に台帳を引く運用そのものが起きない」側にある可能性が高く、
          その場合は種別の数を増やしても提示規則を変えても効かない

副次予測: 種別3（集団参考値）を根拠に「十分」「良好」と判定した記録が
          1件でも現れた場合、提示規則3（種別3を根拠に十分と判定することを禁止）は
          機能していない。その場合は種別3を出力から外す
判定日  : 2026-11-12
実測    : —
確度    : D。錨下げの発生率は未測定。ラベルと出力順だけで抑止できるという根拠はない

副次予測2: 上記と独立に、limit_ratio.py の出力（観測効果／既知最大の比）は
          分母に薬物療法（g=1.35）が入るため常に低く出る。
          この低い比を根拠に自己介入の強度を上げた記録が現れた場合、§H3 は機能していない
判定日  : 2026-11-12
実測    : —
確度    : D。§H3 の抑止力は未検証
```

### D-021 | 2026-08-12 | S-tag: AS-FOUND-01

```
位置づけ: D-018 の中核を維持する適用補正。D-018 は追記のみ原則に従って保存し、
          新規介入・新規指標体系・定義層への昇格は行わない。
          起票時（PR #74）は D-020 を予約していたが、AS-LIMIT-01 の限界値台帳が
          先に D-020 として main へ着地したため、本補正を D-021 とする。
          同一補正の別案（PR #75・D-019 として起票）は本案の却下選択肢③に該当するため
          close した。D-019 は §2.3 B/C/E 限界配分モデルが使用済み。

補正1（G2）:
          D-018 の「G2 決定より前に予測が書かれている」は転記誤り。
          正本 os/Asclepius_Integrated_Architecture_v2_0.md §7.2-B の原文
          「予測が結果より前に書かれるか」を適用する。
          訂正方向はカウント対象を増やす緩和だが、次の2条件を満たすため訂正する:
            ① 基準改定ではなく、正本原文との照合による転記誤りの訂正
            ② D-018対象件数0・結果観測0の時点での訂正

補正2（観測量）:
          観測量を「G1〜G3適合決定の週次確定数」とする。
          既存 Outcome Linkage Rate（OLR）は decision_id と outcome が接続された
          全Decisionを母集団とし、G1〜G3・Notion上の予測・週次確定を条件にしない。
          本観測量は OLR、OLRの分子、そのフロー版のいずれでもなく、相互比較しない。
          metrics/olr.json の既存実測 1/3 = 0.333 をゼロ扱いせず、
          本補正から律速要因の判定も行わない。

補正3（1件の定義）:
          1件 = 1つの予測（結果より前に記入）・1つの現実の決定・
          1つの外部結果からなる組。
          同一の決定または外部結果を共有するカードは、分割・複製数にかかわらず
          合計1件とする。結果が初めて確定した週に計上する。
          追加のDR指標は導入しない。

補正4（副次予測）:
          D-018 の副次予測「自動化を先行させた場合に週次件数は増えない」を
          判定対象外とする。具体的介入・基準期間・比較期間が確定するまで再起票しない。

補正5（未達時の結論）:
          D-018 の「未達なら律速は軸の不在ではない」は適用しない。
          未達時に言えるのは
          「閉ループ運用が成立しなかった。律速要因は未同定」
          までとする。

適用    : 2026-09-30 の判定では、D-018 の G2・観測量名称・1件の定義・
          副次予測・反証条項に限り D-021 を優先適用する。
          D-018 の閾値「週1件」と判定日 2026-09-30 は変更しない。
判定日  : 2026-09-30（D-018から継承）
独立予測: なし。D-021 は新規介入ではなく、正本との転記不一致と判定不能条項の補正。
          補正作業自体を成果として測定しない。
```

### D-022 | 2026-08-12 | S-tag: AS-PK-01

```
定義    : 「PK 不在に起因する判断の悪化」とは、Project Knowledge を参照していれば
          避けられた誤答・誤判定が発生し、その事実が ledger または decisions に
          記録されていることをいう。
          repo main を直読すれば防げたものは含めない
          （それは PK の不在ではなく直読の欠落である）。
          「オンデマンド復旧」とは、GitHub MCP が利用不能になった時点で、
          repo main から必要なファイルのみをダウンロードして PK へ投入することをいう。
          常時ミラーへは戻さない。

予測    : 2026-11-10 時点で、PK 不在に起因する判断の悪化が 0 件である
判定日  : 2026-11-10（Instructions 全体の再照合日に合わせる）
実測    : —
差分原因: —
確度    : C。GitHub MCP は 2026-08-06 の運用開始以降、直読の断が0件という実績があるが、
          観測期間が7日と短く、断の発生率そのものは未測定。
          可用性の根拠は本repoの実績のみで、外部のSLAは確認していない
反証    : 1件以上あれば PK を検索キャッシュとして部分復元する。ただし復元対象は
          その誤判定を防げたファイルのみとし、全52本の常時ミラーには戻さない。
          全件ミラーは陳腐化の再導入であり、本決定が消した干渉①②の原因そのものだから

副次予測: 上記と独立に、PK 削除後も「repo に無いことを『やっていない』と判定する」型の
          誤り（2026-08-12 に3件発生）は減らない。
          PK は誤判定の原因ではなく増幅器であり、原因は
          docs/handover/ALREADY_RUNNING.md の直読が手順に無かった側にある
判定日  : 2026-11-10
実測    : —
確度    : D。PK と誤判定の因果は未測定。2026-08-12 の3件は PK 由来ではなく
          ALREADY_RUNNING.md の不在が原因であり、これは PK 削除では変わらない。
          本副次予測が外れた（＝減った）場合、PK が能動的な誤情報源だったことになり、
          本予測の確度評価そのものが誤っていたことになる
```

### D-031 | 2026-08-16 | S-tag: AS-PDE4-FRONTIER-01

```
決定    : ① 個人輸入可能性と医学的採用を分離する。
          ② Roflumilastは一般則上の個人輸入可能性を残すがCLINICIAN_ONLYとし、
             販売先探索・自己分割・自己調剤を行わない。
          ③ Zatolmilastは正規市販製品のない治験薬としてWATCH / RESEARCH_ONLYに置く。
          ④ ND Cognizin 250mgを次の単独N=1候補へ置く。
          ⑤ MCTは製品ラベル確認後の状態依存候補とする。
          ⑥ TAU 25mg + Cognizin 250mg + 別魚油EPA/DHAは逐次評価し、OmegaTAUを上乗せしない。
          ⑦ Bacopaは記憶coreからanti-fatigue候補へ降格する。
          ⑧ 購入済みNAD製品はNADH w/ Chlorellaであり、NR/NMN/OptiNAD+と分離して保留する。
理由    : [実測] ND注文履歴はNADH w/ Chlorellaを示す。
          [文書] Synapsa現行公式製品ページは320mg・8% bacosidesであり、
          現行OSの55%・約176mgと不一致。
          [文書] Citicolineは陽性RCT1件に対しEFSAは因果未確立、MCTは健常若年で一部課題陽性、
          Bacopa 2025 RCTは主要認知項目nullでstress/fatigue二次評価に信号。
          [推定] standalone成分を逐次試験する方が複合製品より因果帰属と停止判断を保てる。
却下    : 個人輸入可なら自己使用する / research chemical vendorからzatolmilastを入手する /
          Cognizin・TAU・OmegaTAU・魚油を同時に積む / Synapsaを55%前提で増量する /
          NADH・NR・NMN・OptiNAD+を同一効果として一括採用する。
予測    : 2026-11-16までに、Citicoline、MCT、膜前駆体、Bacopa、NAD系のうち
          少なくとも1候補で、事前予測を持つ単独blockが実施され、継続または停止判断が
          Decision/Outcomeへ1件以上接続される。
判定日  : 2026-11-16
実測    : —
差分原因: —
確度    : D。現時点で各候補のSuiru固有の反応率、服用頻度、MCT製品ラベル、
          baseline変動幅が未観測。1件は0→1の便宜閾値。
反証    : 0件ならfrontier/ND追補は意思決定を変えない参照負債と判定し、
          C5 §11とC4 §19を削除または最小の製品ラベル訂正だけへ縮退する。
```
### D-032 | 2026-08-13 | S-tag: AS-DIV-01

```
決定    : 占術を真実層・意思決定権限へ入れず、base_rate / context / divination /
          combined の4armで増分予測力だけを測る隔離実験として期限付き採用する。
          主要推定量は BS_context - BS_combined。医療・投薬・金融・法務・安全・採用には使わない。
          実測JSONLはGitへ置かず、Gitには定義・schema・評価器・テストだけを置く。

却下    : ① 占い専用OSを新設する（定義層増殖・T25）
          ② 占術出力を通常の意思決定入力として採用する（予測妥当性の実証なし）
          ③ 何も記録せず娯楽としてのみ使う（増分精度を検証できず、今回の問いが無信号になる）

予測1   : 2026-11-13 時点で、結果接続済みの完全4armペアが20件以上あり、
          scripts/divination_score.py が実データを1回以上採点している
判定日  : 2026-11-13
実測    : —
差分原因: —
確度    : D。占術予測の生成頻度と結果接続率は0件から開始し、20件は0→1の稼働を
          判定する便宜値。統計的有効性を示す標本数ではない
反証    : 20件未満または採点0回なら、実験は運用されていない。入力欄やarmを増やさず、
          本プロトコルを運用対象から外す

予測2   : 2026-11-13 時点で100件以上の主要解析適格ペアがある場合、
          BS_context - BS_combined の95%ブートストラップ区間は0を跨ぐ。
          100件未満なら効力方向を判定せず「無信号」とする
判定日  : 2026-11-13
実測    : —
差分原因: —
確度    : D。占術の追加価値に再現性ある先行効果量がなく、0を中心とする弱い事前分布を置く。
          100件は検出力を保証せず、入力漏洩・モデル差・選択バイアスも残る
反証    : 区間全体が0より大きい場合も超自然的因果とは判定しない。入力全文監査、別モデル、
          事前固定した追試で再現するまで「記録境界下の正の増分」に限定する
```
### D-033 | 2026-08-13 | S-tag: AS-DIV-01

```
位置づけ: D-032の隔離実験と4armを維持したまま、平均効果では消える可能性がある
          例外的実践者を検出できるよう、実践者別の探索・確認・独立追試を追加する。
          実測4armペアは0件であり、結果確認後の指標変更には該当しない。

決定    : practitioner_idを固定し、discovery / confirmation /
          independent_replicationを混ぜずに採点する。過去の驚異的的中は候補者発見にだけ使う。
          confirmationでは新規対象、事前固定した原発言、全外れを含む分母を使い、
          BS_base_rate - BS_divinationを実践者別に返す。確認30件未満は記述のみとする。

根拠    : 肯定側では、Tressoldi et al.の三重盲検100 reading・28人合算が
          正しいreadingの識別65%を報告した。否定側では、Walleczek et al. 2025の
          26483人・420472試行が予知効果の安定再現を示さなかった。
          両者から、集団平均だけで不在を断定せず、個人別の新規確認追試が必要と判断した。

却下    : ① 全実践者を合算して例外的個人を判定する（個人差が消える）
          ② 過去の的中談を確認データへ数える（選択・記憶・事後解釈バイアス）
          ③ 印象的な的中だけを分子に置く（外れと曖昧主張の分母が消える）
          ④ 確認で正なら即座に超自然的能力と呼ぶ（独立追試と機序同定がない）

予測    : 2026-11-13時点で、30件以上の適格confirmationと30件以上の
          independent_replicationを両方持つ実践者は0人である
判定日  : 2026-11-13
実測    : —
差分原因: —
確度    : C。候補者、参加同意、盲検運営経路が未確立であり、統計的成否より
          試行生成の律速が先に来る可能性が高い。人数と所要時間の実測はない
反証    : 1人以上が両phaseを満たした場合、運用予測は外れ。増分の符号とは分けて記録し、
          正の差が独立追試でも出た場合のみ、独立追試下で再現した候補信号と記述する
```


### D-036 | 2026-08-30 | S-tag: AS-ADAPTIVE-STRATEGY-01

```
位置づけ: Suiru固有の抽象化・一般化能力を保持したまま、反証を上位構造問題へ昇格させて
          探索が自己増殖する failure mode に対し、Adaptive Cognitive Policy を
          既存C2/C3/C4へMODIFY統合する。AS-ACP-01 で起草した同policyは本決定へ吸収し、
          独立した思考OS・第二正本としては起こさない。

決定    : 新規思考OS・Cognitive OS・Persistent System・新台帳を作らない。
          C2 `os/Suiru_Modeling_v1_0.md` に generator strength（2-4）と
          architecture自己増殖 failure mode（3-3）を操作可能モデルとして追加する。
          C3 は `docs/design/terminal_decision_contract_v1.md` を唯一の正本とし、
          EXPLORE / MODEL / FALSIFY / EXPLOIT / REFRAME / META・Stopping / VOC・
          Asymmetric Game Selection（Lens）をそこへ統合する。
          `os/Asclepius_Integrated_Architecture_v2_0.md` へ §7.2-C の第二正本を作らない。
          C4 `os/学習OS_v2_5.md` は Part 12 のcue発火最小drillのみ。日次儀式を増やさない。
          Sovereign Agency SOT `os/非支配性_作用能力_統合設計_v0_2_1.md` へ
          §19-10 Asymmetric Game Selection Prior / §19-11 Countervailing・Contest
          Capacity / §19-12 Sovereign Adaptive Capacity を Lens として追加し、Gate化しない。
          External Reality / Project-OS へ意味本文を複製せず、projectionは別carrierで持つ。

根拠    : 食べサポ約3か月・implementation pipeline約1か月で、顧客outcome・実行速度より
          system / generalization が先行した実測。共通点は反証の構造問題昇格。
          一方で抽象化能力自体は強みであり削除対象ではない。
          終端クラスとAction境界を既に所有する C3 契約へ統合すれば、
          新OSではなく既存正本のMODIFYで閉じられる。

却下    : ① 新規「思考OS」「Cognitive OS」「Asymmetric Strategy OS」の作成（定義層増殖）
          ② §7.2-C と C3契約の二正本並置（Adaptive Cognitive Policy の重複所有）
          ③ generator弱体化・DMN／暗黙知の常時gate（問題の誤診）
          ④ incident-specific rule の大量展開（過剰一般化）
          ⑤ 新日次儀式・新台帳・単一Composite Score（maintenance burden・T25）
          ⑥ Project-OS / External Reality / Workspace への本文複製（foreign SOT侵害）
          ⑦ Winning capacity の terminal objective 化

予測    : 2026-11-30までに、C3 Adaptive Cognitive Policy / Part 12 drill / §19-10 Prior が
          実際の Kill・Exploit・Reframe・停止判断を1件以上変え、decisions / Outcome /
          portfolio proposal のいずれかに差分が残る。
          0件なら §19-10 と C3 Adaptive Cognitive Policy 節を縮退または削除する。
判定日  : 2026-11-30
実測    : —
差分原因: —
確度    : D。failure mode の観察自体は複数案件で一致するが、閉ループは fixture / validator の
          機械接続で示せているだけで、live strategic decision がまだ1件も発生していない。
反証    : 判定日までに判断変更の実測0件、本統合が新OS化・常時gate化・暗黙知抑制・
          Winning の目的化を生んだ場合、または同種案件で TTAO / Outcome / Learning rate /
          Optionality / Resource efficiency が継続悪化した場合は、Prior を限定・棄却する
          （新総合scoreは作らない）
```


### D-037 | 2026-09-02 | S-tag: AS-OBJECTIVE-ARCH-01

```
位置づけ: Personal / Company / System の Objective hierarchy を、既存 semantic owner を壊さず
          意味分離する。Objective ≠ Agency ≠ Capital ≠ System Success Condition を固定する。

決定    : Personal 側は `os/BIOS_v2_8.md` v2.8.3 §0-A で Principal / Personal Long-term Objective /
          Current Exploration Theme（§0）/ Sovereign Agency（instrumental）/ Asclepius L0 配置を明示する。
          `docs/asclepius/why.md` L0 は system success condition のまま維持し、Personal Objective へ昇格させない。
          `os/非支配性_作用能力_統合設計_v0_2_1.md` §19-13 で cross-system placement pointer のみ追加する。
          Company 側は `project-os-metrics/docs/company/why.md` v0.11.0 で Company Objective と
          External Agency を分離し、Project-OS constitutional index へ locator を追加する。
          Workspace は conceptual cross-ref のみ（Objective owner ではない）。

根拠    : Value / Objective / Agency / Capital / Mechanism / Outcome / Learning の混同余地が残っていた。
          既存 AS-SOVAGENCY-01 / AS-HEDONIC-ROLE-01 / POM-COMPANY v0.10 / POM-CONSTITUTION-01 と整合する
          最小 semantic correction。

却下    : ① 新 Persistent System / 新 UIR primitive / 新 unified score ② Personal と Company Objective の同一化
          ③ Asclepius L0 の人生 Objective への昇格 ④ External Agency の terminal 化 ⑤ foreign SOT 本文複写

予測    : 2026-11-30 までに dependent 文書の material contradiction が新規に 0 件増え、
          semantic contract tests が PASS する。
判定日  : 2026-11-30
実測    : —
差分原因: —
確度    : C（構造整理。live 判断変更の実測は別途）
反証    : fresh main が Personal/Company Objective の authority を別配置していることが実測された場合、
          本階層を縮退し owner SOT へ追従する
```

### D-038 | 2026-09-02 | S-tag: AS-ENV-PPC-02

```
位置づけ: 住環境を Physical Base / PPC として扱う意味境界を、既存環境・身体統合OSへ
          最小追加する。新規住宅OS・新規総合scoreは作らない。

決定    : `os/環境_身体統合OS_v3_1.md`「統合: PPC住環境」へ §8 Physical Base / Decision Vector 境界を追加。
          Cost/Environment/Mobility/Capability/Optionality/Reversibility/Attraction を非圧縮 vector で保持。
          家賃は soft constraint。Smart-room-ready / Research-ready は後付け・拡張可能性。
          Primary=1人居住。二人居住・Petは Option Value（医学Objectiveへ昇格しない）。
          Attractionは BIOS/Part13 の Signal/Modifier。
          時点依存の地名・家賃帯・面積・間取りは恒久OSへ埋め込まない。
          新規「§実測接続境界」層は作らず、既存 §5/§6 へ昇格規則を明示接続する。

根拠    : AS-ENV-PPC-01 本体統合後も、Optionality / Reversibility / Attraction / soft constraint /
          Research-ready 等の意味が不足し、総合score化や時点条件の恒久化リスクがあった。

却下    : ① 新規住宅OS / 新規総合score / 新規DB・台帳・Routine
          ② 表参道・祐天寺・西荻窪等の時点条件の恒久OS埋め込み
          ③ 新規「§実測接続境界」層の創設
          ④ Pet の医学Objective昇格
          ⑤ 既存PPC §0–§7 / Module 2 の全面書換

予測    : 2026-11-30 までに住宅比較が vector 差分で提示され、総合score新設が 0 件のまま。
判定日  : 2026-11-30
実測    : —
差分原因: —
確度    : C（意味境界の固定。live 物件選択変更の実測は別途）
反証    : fresh main が同等境界を別 owner で既に持っていた場合、本追記を縮退し owner へ追従する
```
