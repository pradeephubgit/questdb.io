# Screenshot tests

The purpose of the code in this folder is to provide a simple screenshot
regression test.

It is meant to be run only during development locally on a contributors machine.
For this reason, the code is more hands-on than something fully automated would
be.

## Why

It is difficult to implement changes when codebase is not covered by tests. To
make matters easier, this tool provides some assurance and allows to avoid
regressions.

## How it works

> `pwd` should point to the root of the repository

1. execute `npm start` to initiate local dev server
1. execute `ts-node test/screenshot/index.ts` (get `ts-node` with
   `npm install -g ts-node` if you don't have it)
1. headless browser (puppeteer) will visit all internal links found on
   `localhost:3000`
1. links are cached to `test/screenshot/links` file.
1. headless browser visits all links found in `test/screenshot/links` file and
   saves screenshots to `test/screenshot/checkpoints`
1. screenshots in `test/screenshot/checkpoints` are then compared against
   `test/screenshot/baselines`
1. if checkpoint screenshot is different than baseline, then a new screenshot is
   saved to `test/screenshot/diffs` with different areas marked in red.

Once the process is done, contributor can inspect the contents of
`test/screenshot/diffs` and see if their changes have negative impact.
