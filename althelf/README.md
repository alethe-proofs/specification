# Alethe Classic in AletheLF

Alethe proofs can be expressed as restricted AletheLF proofs.  These proofs must
fulfill some restrictions (For example, all conclusions must be printed),
and use a specific signature.  The signature collects the Alethe proof rules.
To avoid confusion, this document refers to Alethe as "Alethe Classic".

An Althe Classic consumer should be able to use the AltheLF proofs, by only
changing its parser.

## Changes

* We assume that AletheLF is extended with a `:match-conclusion` feature
  that captures the conclusion of the step.  This is very useful for Alethe
  Classic proofs, since they allow us to avoid extra arguments.
* `cl` is not unary, instead `(cl)` is the term `false`.  Hence, a the simple
	`false` term should be parsed as the empty clause, and `cl false` is the
	 clause containing the literal `false`.
* Sharing doesn't use `!named`, but instead uses `define` statements.
