# Alethe Classic in AletheLF

Alethe proofs can be expressed as restricted AletheLF proofs.  These proofs must
fulfill some restrictions (For example, all conclusions must be printed),
and use a specific signature.  The signature collects the Alethe proof rules.
To avoid confusion, this document refers to Alethe as "Alethe Classic".

An Alethe Classic consumer should be able to use the AltheLF proofs, by only
changing its parser.

## Changes

* We assume that AletheLF is extended with a `:match-conclusion` feature
  that captures the conclusion of the step.  This is very useful for Alethe
  Classic proofs, since they allow us to avoid extra arguments.
* `cl` cannot be used without arguments.  To write `(cl)` AletheLF uses the term
  `false`.  Hence, a the simple `false` term should be parsed as the empty
  clause, and `cl false` is the clause containing the literal `false`.
* Sharing doesn't use `! .. :named`, but instead uses `define` statements.

## Contexts

Alethe Classic has a notion of contexts used to reason about binders.  Contexts
are lists of variable assignments and shadowings (self assignments). In AletheLF
a context is represented as a conjunction of equalities `= x t` where `x` is a
variable and `t` a term.

Since context are scoped, we use AletheLF's context mechanism.  The extended
context become assumptions of the scope and premises of steps that use contexts.
Hence, the equivalent to an `anchor` is an `assume-push`.  The
context-manipulating rules are rules with `:assumption` that check that the
assumption is the appropriately extended context.

TODO: should the context have its own type?
