# s69-mc-codex promotion manifest gate - 2026-06-20

Owner/prefix: s69-mc-codex-

Batch 112 in G:\codex-project\s69-mc-codex hardened the 40-to-80 promotion proof path. stage_promotion.write_promotion_manifest() now writes with runner_json.write_json_report(). True disk write failure remains fail-closed with ok=false, reason=promotion_manifest_write_failed, and source_reason preserved.

Important rule: promotion manifest serialization sanitization is not a clean proof. If non-JSON fields require sanitization, evidence is written but the proof becomes ok=false/reason=promotion_manifest_serialization_sanitized. evaluate_previous_stage_proof() rejects persisted promotion manifests unless ok is True, reason is ok, write_result.ok is True, and no serialization_sanitized marker exists. This prevents sanitized or noncanonical promotion manifests from satisfying the 80 previous-stage S gate.

Verification: stage_promotion 16 passed; promotion/launch/run_config 97 passed; writer 379 passed / 2 skipped; determ 61 passed; review 9 passed; py_compile stage_promotion.py passed. Franklin requested changes on sanitized proof acceptance; Wegener and Carver approved after fix. preflight_40.py still rc=1 / blocked_missing_real_brief; no provider writing started.

Commits: code f0d333f00, project log 42fd393de, paperclip 5fe45e2e.
