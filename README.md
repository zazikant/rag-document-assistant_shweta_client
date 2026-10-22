
<!-- Updated: 2026-09-18 -->

## AX DSPy Pipeline — Provenance

Ported **word-to-word** from the "Bible" repo
[`atomic-graph-opencode`](https://github.com/zazikant/atomic-graph-opencode)
(same port already applied to tradingview-notes-app, ax-opencode-translator,
ax-translator, gsap-animation-pipeline, Dspy-app, google-ads-subagent-vercel).

- `src/lib/brain/ax-pipeline.ts` — the Bible's VALIDATE → REFINE quality gate
  wrapped around the REDUCE stage: weighted-axes rubric (coverage > fidelity >
  coherence > conflict surfacing > citation accuracy), exact JSON format,
  scoring bands, "Be FAIR"; `compileRefinePrompt()` (DSPy `Module.compile()`
  analog); `callWithRetryAwareness()` + `ErrorEntry` history;
  `parseLLMJson()` + `recoverTruncatedJSON()` robust JSON chain;
  `VALIDATION_THRESHOLD = 0.75`, `MAX_ITERATIONS = 3`, 20s time budget.
- `/api/brain/chat` — REDUCE synthesis now runs through the gate
  (new `ax-validate` stage events); the streamed answer retries are
  error-history aware.
- SSE event contract and all RAG prompts unchanged.
