# math

## 📖 [ドキュメントを読む → tauto-lang.github.io/math-by-ai](https://tauto-lang.github.io/math-by-ai/)

全モジュールのソースを、名前から定義へ飛べる形で読める:
[core](https://tauto-lang.github.io/math-by-ai/core/) ·
[algebra](https://tauto-lang.github.io/math-by-ai/algebra/) ·
[nat](https://tauto-lang.github.io/math-by-ai/nat/) ·
[geometry](https://tauto-lang.github.io/math-by-ai/geometry/)

Tauto の数学ライブラリ。モノイド・可換モノイド・群・半環の抽象的な定理を、
自然数の算術・順序・整除と結び付ける。Euclid の互除法、整数係数の Bézout 等式、
素数判定、素因数分解の存在と一意性、素数が無限に存在することまで証明する。
有理数の Dedekind 切断から実数を構成し、対角線論法によって実数の非可算性も証明する。
可換環と整域、多項式の正規化による環の等式の自動証明 `ring_norm!` を備え、
整域上の座標平面で平行四辺形の対辺が等しいことを公理なしで証明する。

## 構成

| tote | モジュール | 内容 |
| --- | --- | --- |
| `core` | `notation`・`highlight` | `logic!`、等式・論理結合子の文法、共有のトークン色付け |
| `core` | `equality` | 二変数関数の等式の合同性 `congr2` |
| `core` | `order` | 命題を値にする関係の半順序、反射律・推移律・反対称律、最小元の一意性 |
| `core` | `functions`・`diagonal` | 単射・全射、二値列の対角線と非可算性 |
| `core` | `rational_order` | 有理数の狭義順序と、二つの有理数の間にある有理数の構成 |
| `core` | `real`・`real_nat` | Dedekind 切断、切断の外延的同値、有界な非空族の上限、自然数の単射的な埋め込み |
| `core` | `interval`・`interval_cut`・`real_diagonal` | 入れ子の有理区間からの切断の構成、各行を避ける対角線論法、実数の非可算性 |
| `core` | `classical`・`classical_decision` | 証拠付きの命題の判定と、独立した古典的判定公理 |
| `algebra` | `monoid` | 演算と単位元を引数に取る `Monoid`、結合律・単位律、単位元の一意性、有限積と連結、冪の指数法則、準同型による有限積の保存 |
| `algebra` | `commutative` | 可換モノイド、四項の交換則、置換による有限積の不変性、積の冪 |
| `algebra` | `group` | 非可換群、左右消去律、逆元の一意性・二重逆元・積の逆元、方程式の解と一意性 |
| `algebra` | `semiring` | 加法が可換な半環、左右の有限和への分配、二項式どうしの積の展開 |
| `algebra` | `notation` | `alg!`、演算を明示するモノイド・群の式、`⋆` と `ε` |
| `algebra` | `semiring_notation` | `semiring!`、加法・乗法と 0・1 を明示する式 |
| `algebra` | `ring` | 可換環 `CommRing` と整域 `IntegralDomain`、零との積・負号の法則、加法群・乗法モノイドの取り出し |
| `algebra` | `ring_norm`・`ring_tactic` | 環の式の正規形と健全性 `ring_norm_eq`、可換環の等式を証明する `ring_norm!` |
| `algebra` | `ring_notation` | `ring!`、加法・零・負号・乗法・一を明示する式、`+`・`-`・`*`・単項負号 |
| `nat` | `arithmetic` | 自然数の加法／乗法の可換モノイドと半環、`sum`・`prod` の連結・置換不変性、有限和のスカラー倍 |
| `nat` | `order` | 自然数の半順序、0 が最小、後者との順序 |
| `nat` | `divisibility` | 証拠の商を持つ整除関係、推移性、和・積による閉性、0 の整除 |
| `nat` | `number_theory` | 有限和・自然数係数の線形結合・正の冪の整除 |
| `nat` | `subtraction` | 自然数の切り捨て減算と乗法、整除と減算 |
| `nat` | `euclid` | 最大公約数を計算する互除法、任意の入力での停止と正しさ、対称性・一意性・Euclid ステップ |
| `nat` | `bezout` | 拡張 Euclid の係数計算、正負に分けた平衡等式、整数係数の Bézout 等式 |
| `nat` | `coprime` | 互いに素な数についての積の消去則 |
| `nat` | `primes` | 素数の定義、素数が積を割るときの Euclid の補題 |
| `nat` | `primality`・`prime_decision` | 試し割りによる素数判定の健全性と完全性 |
| `nat` | `factor_search` | 合成数の真の因子の探索、両因子が小さくなること |
| `nat` | `factorization`・`unique_factorization` | 任意の正の自然数の素因数分解の計算・正しさ・並べ替えを除く一意性 |
| `nat` | `infinite_primes` | 階乗と、任意の上限を超える素数の構成 |
| `nat` | `relations` | `nat_rel!`、算術式を含む整除・等式・比較 |
| `nat` | `notation` | `nat!`、自然数の式・等式・比較、`+`・`-`・`*` |
| `nat` | `integer_notation` | `int!`、整数の式・負号・自然数の埋め込み・符号付き差 |
| `geometry` | `point` | 環 K 上の座標平面の点 `Point(K)` |
| `geometry` | `notation` | `geo!`、線分の平行 `∥`・長さの二乗の一致 `≅`、`¬`・`∧` |
| `geometry` | `parallelogram` | 整域上で、平行四辺形の対辺の長さ（の二乗）が等しいこと |

依存は `nat → algebra → core` に加え、`nat → core`（順序）、`geometry → algebra → core` と `geometry → core`。標準ライブラリの `Nat` と既存の算術定理を再利用する。
`Monoid(A, op, unit)` は法則の証拠で、加法と乗法を同じ `Nat` に同時に与えられる。
`map_product` は演算と単位元の保存だけを必要とし、モノイドの法則を余分に要求しない。

ルートの `Tauto.eure` は四つの tote を明示的な path 依存としてまとめた開発用の入口。
現行の Totebag に専用の workspace member 宣言はないため、その機能を仮定していない。
各 tote は自身の manifest から依存を解決でき、math の外の package に依存しない。

## 表記と色付け

定義と表記はそれぞれ import する。すべての文法を `syntax!(..., with(tokens: ...))` で登録している。
専用マクロの引数内だけに適用されるため、複数分野の表記を同じファイルで使える。

| import | マクロ | 表すもの |
| --- | --- | --- |
| `core::notation` | `logic!` | 型を限定しない等式、`¬`・`∧`・`∨`・`→` |
| `algebra::notation` | `alg!` | `演算, 単位元; 式`、`⋆`・`ε`、任意の型の等式 |
| `algebra::semiring_notation` | `semiring!` | `加法, 零, 乗法, 一; 式`、`+`・`*`・`0`・`1` と等式 |
| `nat::notation` | `nat!` | 自然数の式、`+`・切り捨て減算 `-`・`*`、`=`・`≤`・`<` |
| `nat::integer_notation` | `int!` | 整数の式、`+`・`-`・`*`・単項負号、`↑`・`diff`、等式・比較 |
| `nat::relations` | `nat_rel!` | 自然数の算術式どうしの整除・等式・比較 |
| `algebra::ring_notation` | `ring!` | `加法, 零, 負号, 乗法, 一; 式`、`+`・`-`・`*`・`0`・`1` と等式 |
| `geometry::notation` | `geo!` | `加法, 零, 負号, 乗法, 一; 関係`、`AB ∥ CD`・`AB ≅ CD`・`¬`・`∧` |

```taut
import std::Base
import std::NatNorm
import std::Tactic
import nat::notation

theorem distribute(a: Nat, b: Nat, c: Nat): nat!(`a * (b + c) = a * b + a * c`) {
  by nat_norm!(): nat!(`a * (b + c) = a * b + a * c`) {}
}
```

式の途中にも使える。たとえば関数呼び出しが重なった
`Nat::mul(Nat::add(g, Nat::add(Nat::mul(a, na), Nat::mul(b, nb))), c)` は次の形になる。

```taut
nat!(`(g + (a * na + b * nb)) * c`)
alg!(`op, unit; inv(a) ⋆ (a ⋆ b) = b`)
semiring!(`add, zero, mul, one; (a + b) * c = a * c + b * c`)
int!(`↑a * coefficient_a(c) + ↑b * coefficient_b(c) = ↑g`)
nat_rel!(`d | a * x + b * y`)
logic!(`d = 1 ∨ d = p`)
```

変数や関数は呼び出し側の名前をそのまま書ける。Unicode の識別子と `Nat::...` のような修飾名も使える。
`f(a + b)` のような関数適用も可能。既存の `$name` と、任意の Tauto 式を渡す `${ ... }` も使える。
マクロの補助関数と同じ名前の変数でも、呼び出し側の文脈を保持する。

`*` は `+`・`-` より強く、二項演算は左結合。括弧は式の結合順序を指定し、そのまま展開される。
`logic!` は `¬`、`=`、`∧`、`∨`、`→` の順に強く、含意は右結合。
自然数の `a - b` は切り捨て減算、整数の `a - b` は通常の整数減算。
`int!` 内の数値は整数、`↑a` は自然数 a の整数への埋め込み、`diff(p, n)` は自然数 p と n の符号付き差（`Int::sub_nat(p, n)`）に正確に展開する。
`diff(a * p, a * n)` や `↑gcd(a, b)` も書ける。
整数の式から別の型の関数を呼ぶとき、引数の数値などを自然数として渡す必要があれば `${ ... }` で明示する。

`alg!` の `ε` と、`semiring!` の `0`・`1` はヘッダで指定した値であり、型 A に数値の演算を勝手に導入しない。
`semiring!` のヘッダは名前または `${ ... }` で渡す。これらの表記自体は可換性などの法則を仮定せず、演算の順序を変更しない。
表記は項や命題へ展開するもので、証明を自動的に作るものではない。
`nat_eq!`・`monoid_eq!` は既存コード向けの互換名として残している。

トークンの色付けは変数を `variable`、呼び出す関数を `function`、数値を `number`、演算子を `operator`、
`ε` や抽象的な零・一を `enumMember` として返す。空白を除外し、scanner が渡す UTF-8 のバイト位置を保持する。
`${ ... }` の内部を一つの DSL トークンとして塗りつぶすことはしない。

```sh
tauto highlight --tokens examples/notation.taut
tauto run --backend javascript tests/highlight.taut
```

リポジトリのルートで実行する。

実際の定義・定理・帰納法の途中の命題・合同性のラムダも、この表記で書いている。
マクロの展開器と、表記と元の項が定義的に一致することを確かめる [examples/notation.taut](examples/notation.taut) の比較先では、元の関数呼び出しを明示している。

実行できる証明例:

- [examples/basic.taut](examples/basic.taut): 最初のモノイドと自然数、互換表記。
- [examples/advanced.taut](examples/advanced.taut): 群・半環・整除・順序。
- [examples/number_theory.taut](examples/number_theory.taut): Euclid、Bézout、素因数分解、素数の無限性。
- [examples/uncountability.taut](examples/uncountability.taut): 二値列と実数の非可算性、`|ℕ| < |ℝ|`。
- [examples/notation.taut](examples/notation.taut): 全文法の展開・結合順序・Unicode・名前の文脈。
- [examples/geometry.taut](examples/geometry.taut): `ring_norm!` による環の等式、平行四辺形の対辺。

## 定理の仮定と範囲

- 群の消去律・積の逆元 `inv(a ⋆ b) = inv(b) ⋆ inv(a)`・方程式の解の一意性は、可換性を仮定しない。
- 半環の乗法は可換でなくてよい。二項式の展開も乗算の順序を保持する。
- `CommRing` は乗法も可換な環。`ring_norm!` は可換環の証拠を受け取り、両辺の差の正規形が 0 になることを検査する。体はまだ定義していない。
- 平面幾何は整域上の座標で扱う。平方根がないので長さは二乗で比べ、平行は外積が 0 であることで表す。`parallelogram_opposite_sides` は A・B・D が一直線上にないことを仮定する。
- `Permutation` は隣接交換・先頭の維持・推移性で生成する証拠。可換モノイドの有限積がその証拠に沿って不変であることを証明する。
- `Divides(a, b)` は `a * k = b` となる自然数 `k` と等式の証拠を持つ命題。`Prime(p)` は `1 < p` と、すべての約数が 1 または p であることを要求する。
- `IsLeast` は下界の性質を表し、`least_unique` は候補それぞれの集合への所属も明示的に要求する。

## 数論の計算と証明

`gcd_correct(a, b)` は、`gcd(a, b)` が両方を割り、すべての共通因子に割られることを証明する。
`gcd(0, 0) = 0` も含め、入力についての前提はない。
互除法は内部で b 回分の構造的再帰を用い、剰余が小さくなることからその回数で必ず足りると証明する。
任意の固定 fuel に成功を仮定する定理ではない。

`bezout_coefficients(a, b)` は四つの自然数 `(pa, na, pb, nb)` を計算する。
`bezout_balance` は `gcd(a,b) + a*na + b*nb = a*pa + b*pb`、
`bezout_identity` は整数への埋め込みを用いた `a*(pa-na) + b*(pb-nb) = gcd(a,b)` を証明する。
整数係数を `coefficient_a`・`coefficient_b` から取得できる。

`is_prime_sound` と `is_prime_complete` により、`is_prime(n) = true` と `Prime(n)` が両方向に結び付く。
`factorize(n)` は正の n に対し素数のリストを計算する。`factorize_correct` が全要素の素数性と積の一致を証明し、
`factorization_unique` が任意の別の素因数分解との `Permutation` を与える。重複した素因子も保持する。
1 の分解は空リスト。0 については分解の正しさを主張しない。
分解の内部再帰も n に基づく回数を使い、真の因子と商の両方が小さくなることから十分性を証明する。

`prime_above_correct(n)` は、計算した `prime_above(n)` が素数で n より大きいことを証明する。
構成は `factorial(n) + 1` の素因子を取り出す Euclid の議論で、古典論理や選択公理を使わない。

これらは証明を優先した試し割り実装で、平方根までの探索・篩・高速な整数表現は使っていない。
特に `prime_above` は階乗を作るため、大きな入力の素数探索に向く実装ではない。

## 実数の非可算性

入口は [examples/uncountability.taut](examples/uncountability.taut) の
`reals_more_than_naturals`。自然数の埋め込みの単射性と、どの `Nat → Real` も
すべての実数を列挙できないことを組み合わせている。

`Real` は有理数の Dedekind 切断。下側集合が非空で、全体ではなく、下に閉じ、
最大元を持たないことを証拠として保持する。同じ切断を表すことは `SameReal` で定義する。
`CoversReals` はこの同値で列挙の網羅性を判定するので、証拠や関数の表現が異なるだけで
「列挙できない」と結論していない。有理数の `1/2` と `2/4` のような表現の違いも
`real_respects_rationals` によって切断の所属に影響しない。

切断の非空族が上に有界なら、その和集合が上限になる。
`supremum` が切断の四条件を満たし、`supremum_upper` と `supremum_least` が
上界であることと最小性を証明する。実数の存在・完備性・非可算性を公理として置いていない。
この証明に必要な実数の構成と順序を扱い、実数の加減乗除はまだ実装していない。

実数側の対角線論法は、小数表示の代わりに有理区間を使う。
列挙の候補を `rows` として、次のように切断 `d` を作る。

1. `I₀ = [0, 1]` から始める。`Iₙ = [a, b]` の内部に有理数 `m` を選ぶ。
2. `m` が `rows(n)` の下側集合に属するなら、`Iₙ₊₁ = [a, m]` とする。
   属さないなら、`m < r < b` となる有理数 `r` を選び、`Iₙ₊₁ = [r, b]` とする。
3. `d = {q ∈ ℚ | ある n について q < left(Iₙ)}` とする。
   入れ子性により、これは非空で全体ではない、最大元のない下側集合になる。
4. 前者の場合 `m` は `rows(n)` に属し `d` に属さない。
   後者の場合 `m` は `d` に属し `rows(n)` に属さない。
   よって `d` はすべての行と異なる。

区間の長さが 0 に収束することや、交点の一意性は不要。
二つの有理数の間の値には媒介数 `(a+c)/(b+d)` を使う。
`chain_cross` が任意の左端と右端の順序を保証し、`branch_excludes` が一行を避ける議論をまとめる。
最後の `reals_not_enumerable` は、網羅性を仮定して対角線の所属を取り出すだけになる。

**論理的な前提**: 二値列の `cantor_binary`、切断の構成、上限、自然数の単射性は公理を使わない。
実数についての `cantor_reals` と `reals_more_than_naturals` は、命題の真偽を証拠付きで選ぶ
古典的判定原理 `classical_decision : (P : Prop) → Decision(P)` を使う。
これは [classical_decision.taut](totes/core/src/classical_decision.taut) の一つの明示的な論理公理であり、
構成的な二値列の証明からは import しない。一般形の `reals_not_enumerable` は判定原理を引数に取り、
この公理自体には依存しない。検査結果の `axioms: none` と、判定原理を引数に持つことは区別する。

```sh
tauto check examples/uncountability.taut --fresh --summary
tauto assumptions examples/uncountability.taut --json
```

`cantor_binary` の公理一覧は空、実数についての二つの定理の公理一覧は
`classical_decision` だけになる。

## 検証

```sh
tauto check --fresh --summary
tauto assumptions examples/uncountability.taut --json
tauto run --backend javascript tests/highlight.taut
tauto syntax gen --check totes/core/src
tauto syntax gen --check totes/algebra/src
tauto syntax gen --check totes/nat/src
tauto syntax gen --check totes/geometry/src
```

リポジトリのルートで実行する。
引数なしの `tauto check` は、ルートの package と依存する4つの tote、`examples/`・`tests/` をまとめて fresh check する。
`tests/stress.taut` の具体値の確認もここに含まれる。`tauto assumptions` で、各定理が使う公理を確認できる。
`tests/highlight.taut` は6文法のトークン callback と UTF-8 の範囲を実行時に検査する。
文法の生成表は各 `src/.tauto-syntax/` に含める。
tote は `totes/{core,algebra,nat,geometry}` に置く。

## 具体値の負荷確認

`tests/stress.taut` では 100003 の素数性、`gcd(1071, 462) = 21`、360 の素因数分解を検証する。
これらの具体値の確認は、任意入力についての正しさの証明とは別の負荷確認であり、最大入力の保証ではない。

## ライセンス

MIT または Apache-2.0 の、いずれかを選択できる。
[LICENSE-MIT](LICENSE-MIT)・[LICENSE-APACHE](LICENSE-APACHE) を参照。
