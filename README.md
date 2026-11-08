# math

## 📖 [Read the documentation → tauto-lang.github.io/math-by-ai](https://tauto-lang.github.io/math-by-ai/)

The source of every module, with each name linked to its definition:
[core](https://tauto-lang.github.io/math-by-ai/core/) ·
[algebra](https://tauto-lang.github.io/math-by-ai/algebra/) ·
[nat](https://tauto-lang.github.io/math-by-ai/nat/) ·
[geometry](https://tauto-lang.github.io/math-by-ai/geometry/)

A mathematics library for Tauto. It connects abstract theorems about monoids, commutative monoids, groups and semirings
to the arithmetic, order and divisibility of the natural numbers, and goes as far as Euclid's algorithm,
Bézout's identity with integer coefficients, primality testing, the existence and uniqueness of prime factorization,
and the infinitude of the primes.
It constructs the real numbers as Dedekind cuts of the rationals and proves by a diagonal argument that they are uncountable.
It has commutative rings and integral domains, `ring_norm!`, which proves ring equations by normalizing polynomials,
and a proof without axioms that the opposite sides of a parallelogram are equal, in the coordinate plane over an integral domain.

## Contents

| tote | Module | Contents |
| --- | --- | --- |
| `core` | `notation`, `highlight` | `logic!`, the grammar of equations and logical connectives, shared token highlighting |
| `core` | `equality` | `congr2`, congruence of equations for two-argument functions |
| `core` | `order` | Partial orders as Prop-valued relations; reflexivity, transitivity, antisymmetry; uniqueness of the least element |
| `core` | `functions`, `diagonal` | Injections and surjections; the diagonal of binary sequences and their uncountability |
| `core` | `rational_order` | The strict order of the rationals, and a rational between any two rationals |
| `core` | `real`, `real_nat` | Dedekind cuts, extensional equality of cuts, the supremum of a bounded non-empty family, the injective embedding of the naturals |
| `core` | `interval`, `interval_cut`, `real_diagonal` | A cut built from nested rational intervals, a diagonal argument avoiding every row, the uncountability of the reals |
| `core` | `classical`, `classical_decision` | Deciding a proposition with evidence, and a separate classical decision axiom |
| `algebra` | `monoid` | `Monoid` taking the operation and the unit as arguments; associativity and unit laws; uniqueness of the unit; finite products and concatenation; exponent laws for powers; homomorphisms preserve finite products |
| `algebra` | `commutative` | Commutative monoids, the four-term interchange law, invariance of finite products under permutation, powers of products |
| `algebra` | `group` | Non-commutative groups; left and right cancellation; uniqueness of inverses, double inverse, inverse of a product; solutions of equations and their uniqueness |
| `algebra` | `semiring` | Semirings with commutative addition, distribution over finite sums on both sides, expanding products of binomials |
| `algebra` | `notation` | `alg!`, monoid and group expressions with explicit operations, `⋆` and `ε` |
| `algebra` | `semiring_notation` | `semiring!`, expressions with explicit addition, multiplication, 0 and 1 |
| `algebra` | `ring` | Commutative rings `CommRing` and integral domains `IntegralDomain`; laws of multiplication by zero and negation; the additive group and the multiplicative monoid of a ring |
| `algebra` | `ring_norm`, `ring_tactic` | Normal forms of ring expressions and their soundness `ring_norm_eq`; `ring_norm!`, which proves equations in a commutative ring |
| `algebra` | `ring_notation` | `ring!`, expressions with explicit addition, zero, negation, multiplication and one; `+`, `-`, `*`, unary minus |
| `nat` | `arithmetic` | The natural numbers as commutative monoids under addition and multiplication and as a semiring; concatenation and permutation invariance of `sum` and `prod`; scalar multiples of finite sums |
| `nat` | `order` | The partial order of the naturals, 0 is least, order with successors |
| `nat` | `divisibility` | Divisibility with the quotient as evidence; transitivity; closure under sums and products; divisibility of 0 |
| `nat` | `number_theory` | Divisibility of finite sums, linear combinations with natural coefficients, and positive powers |
| `nat` | `subtraction` | Truncated subtraction of naturals and multiplication; divisibility and subtraction |
| `nat` | `euclid` | Euclid's algorithm for the greatest common divisor; termination and correctness on every input; symmetry, uniqueness, the Euclid step |
| `nat` | `bezout` | Coefficients from the extended Euclidean algorithm, a balance equation split into positive and negative parts, Bézout's identity with integer coefficients |
| `nat` | `coprime` | Cancellation in products of coprime numbers |
| `nat` | `primes` | The definition of primes; Euclid's lemma when a prime divides a product |
| `nat` | `primality`, `prime_decision` | Soundness and completeness of primality testing by trial division |
| `nat` | `factor_search` | Finding a proper factor of a composite number, with both factors smaller |
| `nat` | `factorization`, `unique_factorization` | Computing the prime factorization of every positive natural; its correctness; uniqueness up to reordering |
| `nat` | `infinite_primes` | The factorial, and a prime above any given bound |
| `nat` | `relations` | `nat_rel!`, divisibility, equations and comparisons between arithmetic expressions |
| `nat` | `notation` | `nat!`, expressions, equations and comparisons of naturals; `+`, `-`, `*` |
| `nat` | `integer_notation` | `int!`, integer expressions, negation, the embedding of naturals, signed differences |
| `geometry` | `point` | Points `Point(K)` of the coordinate plane over a ring K |
| `geometry` | `notation` | `geo!`, parallel segments `∥`, equal squared lengths `≅`, `¬` and `∧` |
| `geometry` | `parallelogram` | Over an integral domain, the opposite sides of a parallelogram have equal (squared) lengths |

The dependencies are `nat → algebra → core` and `nat → core` (for order), and `geometry → algebra → core` and `geometry → core`.
The library reuses the standard library's `Nat` and its arithmetic theorems.
`Monoid(A, op, unit)` is evidence of the laws, so addition and multiplication can both be given for the same `Nat`.
`map_product` needs only that the operation and the unit are preserved, not the monoid laws.

The root `Tauto.eure` is the entry point for development; it collects the four totes as explicit path dependencies.
The current Totebag has no declaration for workspace members, so the library does not assume one.
Each tote resolves its dependencies from its own manifest and depends on no package outside math.

## Notation and highlighting

Definitions and notations are imported separately. Every grammar is registered with `syntax!(..., with(tokens: ...))`.
A notation applies only inside the arguments of its own macro, so notations from several areas can be used in the same file.

| import | Macro | What it writes |
| --- | --- | --- |
| `core::notation` | `logic!` | Equations of any type, `¬`, `∧`, `∨`, `→` |
| `algebra::notation` | `alg!` | `operation, unit; expression`, `⋆` and `ε`, equations of any type |
| `algebra::semiring_notation` | `semiring!` | `add, zero, mul, one; expression`, `+`, `*`, `0`, `1` and equations |
| `nat::notation` | `nat!` | Natural-number expressions, `+`, truncated subtraction `-`, `*`, `=`, `≤`, `<` |
| `nat::integer_notation` | `int!` | Integer expressions, `+`, `-`, `*`, unary minus, `↑` and `diff`, equations and comparisons |
| `nat::relations` | `nat_rel!` | Divisibility, equations and comparisons between natural-number expressions |
| `algebra::ring_notation` | `ring!` | `add, zero, neg, mul, one; expression`, `+`, `-`, `*`, `0`, `1` and equations |
| `geometry::notation` | `geo!` | `add, zero, neg, mul, one; relation`, `AB ∥ CD`, `AB ≅ CD`, `¬`, `∧` |

```taut
import std::Base
import std::NatNorm
import std::Tactic
import nat::notation

theorem distribute(a: Nat, b: Nat, c: Nat): nat!(`a * (b + c) = a * b + a * c`) {
  by nat_norm!(): nat!(`a * (b + c) = a * b + a * c`) {}
}
```

The notations also work inside a larger expression. For example, the nested calls
`Nat::mul(Nat::add(g, Nat::add(Nat::mul(a, na), Nat::mul(b, nb))), c)` are written as follows.

```taut
nat!(`(g + (a * na + b * nb)) * c`)
alg!(`op, unit; inv(a) ⋆ (a ⋆ b) = b`)
semiring!(`add, zero, mul, one; (a + b) * c = a * c + b * c`)
int!(`↑a * coefficient_a(c) + ↑b * coefficient_b(c) = ↑g`)
nat_rel!(`d | a * x + b * y`)
logic!(`d = 1 ∨ d = p`)
```

Variables and functions are written with the caller's names. Unicode identifiers and qualified names such as `Nat::...` work.
Function application such as `f(a + b)` works too, and so do `$name` and `${ ... }`, which passes any Tauto expression.
A variable with the same name as one of the macro's helper functions still refers to the caller's variable.

`*` binds tighter than `+` and `-`, and binary operators are left-associative. Parentheses set the grouping and are expanded as written.
In `logic!`, `¬`, `=`, `∧`, `∨` and `→` bind in that order from tightest, and implication is right-associative.
For naturals, `a - b` is truncated subtraction; for integers, `a - b` is ordinary integer subtraction.
Inside `int!`, numerals are integers, `↑a` is the embedding of the natural a into the integers,
and `diff(p, n)`, the signed difference of the naturals p and n, expands exactly to `Int::sub_nat(p, n)`.
`diff(a * p, a * n)` and `↑gcd(a, b)` can also be written.
When an integer expression calls a function of another type and an argument such as a numeral must be passed as a natural, write it with `${ ... }`.

`ε` in `alg!` and `0` and `1` in `semiring!` are the values given in the header; they bring no numeric operations to the type A.
The header of `semiring!` takes names or `${ ... }`. The notations themselves assume no laws such as commutativity and do not reorder operations.
A notation expands to a term or a proposition; it does not build proofs.
`nat_eq!` and `monoid_eq!` remain as compatibility names for existing code.

Token highlighting reports variables as `variable`, called functions as `function`, numerals as `number`, operators as `operator`,
and `ε` and the abstract zero and one as `enumMember`. It skips whitespace and keeps the UTF-8 byte offsets the scanner passes.
It does not paint the inside of `${ ... }` as a single DSL token.

```sh
tauto highlight --tokens examples/notation.taut
tauto run --backend javascript tests/highlight.taut
```

Run these from the repository root.

The actual definitions, theorems, intermediate propositions in inductions and congruence lambdas are written in these notations too.
The macro expanders, and the comparison terms in [examples/notation.taut](examples/notation.taut) that check a notation is definitionally equal to the original term,
spell out the original function calls.

Runnable proof examples:

- [examples/basic.taut](examples/basic.taut): a first monoid and the naturals, compatibility notation.
- [examples/advanced.taut](examples/advanced.taut): groups, semirings, divisibility, order.
- [examples/number_theory.taut](examples/number_theory.taut): Euclid, Bézout, prime factorization, infinitely many primes.
- [examples/uncountability.taut](examples/uncountability.taut): uncountability of binary sequences and of the reals, `|ℕ| < |ℝ|`.
- [examples/notation.taut](examples/notation.taut): expansion of every grammar, grouping, Unicode, name contexts.
- [examples/geometry.taut](examples/geometry.taut): a ring equation by `ring_norm!`, the opposite sides of a parallelogram.

## Assumptions and scope of the theorems

- Cancellation in groups, the inverse of a product `inv(a ⋆ b) = inv(b) ⋆ inv(a)` and the uniqueness of solutions of equations do not assume commutativity.
- Multiplication in a semiring need not be commutative. Expanding binomials keeps the order of multiplication.
- `CommRing` is a ring whose multiplication is also commutative. `ring_norm!` takes the evidence of a commutative ring and checks that the normal form of the difference of the two sides is 0. Fields are not defined yet.
- Plane geometry uses coordinates over an integral domain. There are no square roots, so lengths are compared squared, and parallelism means the cross product is 0. `parallelogram_opposite_sides` assumes that A, B and D are not on one line.
- `Permutation` is evidence generated by adjacent swaps, keeping the head, and transitivity. Finite products in a commutative monoid are proved invariant along such evidence.
- `Divides(a, b)` is a proposition holding a natural `k` with evidence that `a * k = b`. `Prime(p)` requires `1 < p` and that every divisor is 1 or p.
- `IsLeast` states the lower-bound property, and `least_unique` also requires explicitly that each candidate belongs to the set.

## Computation and proofs in number theory

`gcd_correct(a, b)` proves that `gcd(a, b)` divides both inputs and is divided by every common factor.
It has no hypotheses on the inputs, `gcd(0, 0) = 0` included.
Internally, Euclid's algorithm uses b steps of structural recursion, and the proof shows that this many always suffice because the remainder decreases.
It is not a theorem that assumes success for some fixed fuel.

`bezout_coefficients(a, b)` computes four naturals `(pa, na, pb, nb)`.
`bezout_balance` proves `gcd(a,b) + a*na + b*nb = a*pa + b*pb`,
and `bezout_identity` proves `a*(pa-na) + b*(pb-nb) = gcd(a,b)` through the embedding into the integers.
The integer coefficients are available from `coefficient_a` and `coefficient_b`.

`is_prime_sound` and `is_prime_complete` connect `is_prime(n) = true` and `Prime(n)` in both directions.
`factorize(n)` computes a list of primes for positive n. `factorize_correct` proves that every element is prime and that the product matches,
and `factorization_unique` gives a `Permutation` to any other prime factorization. Repeated prime factors are kept.
The factorization of 1 is the empty list. Nothing is claimed about factorizing 0.
The internal recursion of factorization also uses a count based on n, and its sufficiency is proved from both the proper factor and the quotient being smaller.

`prime_above_correct(n)` proves that the computed `prime_above(n)` is prime and greater than n.
The construction is Euclid's argument, taking a prime factor of `factorial(n) + 1`, and uses neither classical logic nor the axiom of choice.

These are trial-division implementations that put proofs first; they use no search up to the square root, no sieve and no fast integer representation.
In particular, `prime_above` builds a factorial, so it is not meant for finding primes for large inputs.

## Uncountability of the reals

The entry point is `reals_more_than_naturals` in [examples/uncountability.taut](examples/uncountability.taut).
It combines the injectivity of the embedding of the naturals with the fact that no `Nat → Real` enumerates every real.

`Real` is a Dedekind cut of the rationals. It holds evidence that its lower set is non-empty, not everything, closed downward,
and has no greatest element. Two cuts representing the same real is defined by `SameReal`.
`CoversReals` judges whether an enumeration is exhaustive up to this equality, so the proof never concludes "not enumerable"
merely because evidence or functions are represented differently. Different representations of a rational, such as `1/2` and `2/4`,
also do not affect membership in a cut, by `real_respects_rationals`.

If a non-empty family of cuts is bounded above, its union is the supremum.
`supremum` satisfies the four conditions of a cut, and `supremum_upper` and `supremum_least` prove
that it is an upper bound and the least one. The existence, completeness and uncountability of the reals are not taken as axioms.
The library covers the construction and order of the reals needed for this proof; arithmetic on the reals is not implemented yet.

The diagonal argument for the reals uses rational intervals instead of decimal expansions.
Taking the candidate enumeration to be `rows`, it builds a cut `d` as follows.

1. Start from `I₀ = [0, 1]`. Choose a rational `m` inside `Iₙ = [a, b]`.
2. If `m` belongs to the lower set of `rows(n)`, let `Iₙ₊₁ = [a, m]`.
   Otherwise, choose a rational `r` with `m < r < b` and let `Iₙ₊₁ = [r, b]`.
3. Let `d = {q ∈ ℚ | q < left(Iₙ) for some n}`.
   Because the intervals are nested, this is a non-empty lower set that is not everything and has no greatest element.
4. In the first case, `m` belongs to `rows(n)` and not to `d`.
   In the second case, `m` belongs to `d` and not to `rows(n)`.
   So `d` differs from every row.

The interval lengths need not tend to 0, and the intersection need not be unique.
The mediant `(a+c)/(b+d)` gives a value between two rationals.
`chain_cross` guarantees the order of any left end and any right end, and `branch_excludes` packages the argument that avoids one row.
The final `reals_not_enumerable` then only assumes exhaustiveness and extracts the membership of the diagonal.

**Logical assumptions**: `cantor_binary` for binary sequences, the construction of cuts, the supremum and the injectivity of the naturals use no axioms.
`cantor_reals` and `reals_more_than_naturals`, about the reals, use the classical decision principle
`classical_decision : (P : Prop) → Decision(P)`, which chooses the truth of a proposition with evidence.
It is a single explicit logical axiom in [classical_decision.taut](totes/core/src/classical_decision.taut),
and the constructive proof for binary sequences does not import it. The general `reals_not_enumerable` takes the decision principle as an argument
and does not depend on the axiom itself. Note the difference between `axioms: none` in the check results and taking the decision principle as an argument.

```sh
tauto check examples/uncountability.taut --fresh --summary
tauto assumptions examples/uncountability.taut --json
```

The axiom list of `cantor_binary` is empty, and the axiom lists of the two theorems about the reals contain only
`classical_decision`.

## Verification

```sh
tauto check --fresh --summary
tauto assumptions examples/uncountability.taut --json
tauto run --backend javascript tests/highlight.taut
tauto syntax gen --check totes/core/src
tauto syntax gen --check totes/algebra/src
tauto syntax gen --check totes/nat/src
tauto syntax gen --check totes/geometry/src
```

Run these from the repository root.
`tauto check` with no arguments fresh-checks the root package, the four totes it depends on, and `examples/` and `tests/` together.
This includes the concrete values in `tests/stress.taut`. `tauto assumptions` shows the axioms each theorem uses.
`tests/highlight.taut` checks the token callbacks of six grammars and their UTF-8 ranges at run time.
The generated tables of the grammars are included in each `src/.tauto-syntax/`.
The totes are in `totes/{core,algebra,nat,geometry}`.

## Load check with concrete values

`tests/stress.taut` checks that 100003 is prime, that `gcd(1071, 462) = 21`, and the prime factorization of 360.
These concrete checks are a load check, separate from the proofs of correctness for every input, and do not guarantee any maximum input size.

## License

Licensed under either of MIT or Apache-2.0, at your option.
See [LICENSE-MIT](LICENSE-MIT) and [LICENSE-APACHE](LICENSE-APACHE).
