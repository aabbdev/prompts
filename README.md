# Repository minimalism

The repository is the product, not a transcript of the work. Keep only the
smallest coherent tree that implements, tests and explains the current system.

- Modify the canonical existing file by default. Create a new file only when it
  has an independent consumer, lifecycle, owner, or required file format.
- Before creating a file, name its consumer and explain why the closest existing
  module cannot own it. If there is no concrete answer, do not create the file.
- Organize by subsystem, not by implementation detail. Closely coupled helpers,
  state classes, losses and adapters belong with the component that owns them.
- Do not create one-file abstractions. A module containing one private helper
  used by one other module should normally be merged into its caller.
- One concept, one canonical representation. Never keep parallel templates,
  configs, schemas, CLIs, reports or implementations for the same job.
- Version control is the archive. Delete superseded variants instead of keeping
  `old`, `legacy`, `final`, `v2`, comparison or migration copies in the tree.
- Compatibility code requires a real supported consumer or an explicit user
  requirement. Do not preserve dead branches “just in case”.
- Do not turn the investigation process into repository artifacts. Scratch
  analyses, intermediate reports, experiment matrices and generated summaries
  stay outside the deliverable unless a command or CI check consumes them.
- Generated artifacts do not belong beside source code. Do not include wheels,
  ZIPs, caches, build directories, logs or checksums unless distribution
  explicitly requires them.
- Prefer one public command per real workflow. Merge wrappers that differ only
  by flags; delete scripts that merely forward to another implementation.
- Group tests by subsystem. Do not create a new test file for every bug, helper
  or implementation file.
- Keep documentation canonical: one README for usage, one design document when
  the mathematics needs it, and one current limitations section. Delete
  historical audits after their conclusions are integrated.
- File count is a design signal. A growing tree requires justification even when
  every individual file appears reasonable.
- Do not optimize file count blindly. Split a file only when the resulting
  modules can be understood, tested and changed independently. Never create a
  giant miscellaneous module merely to report a smaller number.
- At the end of every task, audit the complete tree:
  1. identify every new file and its consumer;
  2. find duplicate responsibilities and representations;
  3. merge single-consumer micro-modules;
  4. delete dead code, stale docs and generated debris;
  5. run the real tests after deletion.
- Report both the functional result and the structural delta: files added,
  files removed, canonical entry points and remaining intentional boundaries.
- If two implementations pass the same tests, the smaller coherent tree wins.

# Verification discipline
A check must EXECUTE something and FAIL on a real condition. Never sign,
hash, notarise or "attest" a value that a human or another tool supplied.
- If nothing consumes an artifact and fails when it is wrong, do not create it.
  No evidence bundles, no signed reports, no sha256 rituals, no key custody.
- Never write a gate whose only input is a boolean map.
- Do not build tooling for a deferred phase. Build what the next milestone
  needs and delete the rest.
- One implementation per job. Two tools doing the same job = delete one.
- Every file must have a consumer: a script, CI, or an import. Otherwise it does
  not exist. Delete dead code on sight instead of leaving scaffolding behind.
- Never let a document describe a capability that is not implemented.
- A check that can pass without running its work is worse than no check.
- Prefer the boring path: plan -> review -> apply, with CI on the branch.
  Rigour comes from tests that bite, not from process that looks rigorous.
- Deleting code is a deliverable. A smaller tree doing the same job wins.
