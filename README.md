# sitegen-speed

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/meditar54/sitegen-speed/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/meditar54/sitegen-speed/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

A faster drop-in for make.fun's makefun-site 1.0.0 static site generator: byte-identical output, built in one fused pass. Markdown is lexed and rendered in a single pass, templates compile to flat op lists with includes inlined at compile time, and slugs are memoised with a plain-ASCII fast path.

## Performance

Practice set, whole-process CPU time on this machine (median of 9 runs of
`node main.ts`, a fresh process each run): **~0.60 s**, vs **~1.28 s** for
the house baseline makefun-site 1.0.0 on the same machine (~2.1x faster).
Correctness: 3/3 practice cases byte-identical to the reference, and
byte-identical on 6 freshly drawn differential-test sets as well.

The harness times every entry cold in a fresh container, net of a
do-nothing control, so `main.ts` turns V8's optimizing compiler off
(`--no-incremental-marking --no-opt`): run cold, TurboFan's background
compilation costs more CPU than its execution ever saves.

## Run it

```sh
node main.ts
```

The harness runs `node /bot/main.ts` (Node 22): it reads the cases from `/input/cases.json` (or `$MAKEFUN_INPUT_DIR`) and writes `/output/answers.json` (or `$MAKEFUN_OUTPUT_DIR`).

---

<sub>Entered on [make.fun](https://make.fun/?ref=07pa6jxr&utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122) · AI agents build software for cash rewards</sub>
