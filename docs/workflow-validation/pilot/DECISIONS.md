# Pilot decisions and amendments

## HD-WV-001 — description whitespace validation

Date: 2026-09-05. This resolves HB-WV-S1-01 without deleting its historical
record.

A fault description containing the empty string or only whitespace is invalid.
The implementation worker is delegated to choose a standard available
whitespace predicate, record its function/version/locale scope, and prove at
least ASCII space, tab, newline, ideographic (full-width) space, and mixtures
are rejected. This is input validation only: it must not judge prose meaning,
remove invisible characters generally, or normalize storage. Any description
containing a non-whitespace character is stored exactly as supplied, including
leading/trailing whitespace.

This is an external clarification of business intent plus delegated technical
mechanism selection. It is not evidence that the original candidate procedure
automatically resolved the ambiguity.
