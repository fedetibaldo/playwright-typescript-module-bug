# Playwright Typescript + Module bug

Minimal reproduction of [issue 15862](https://github.com/microsoft/playwright/issues/15862). Using `@playwright/test` version `1.42.0`.

## Working example

Branch `main` is the working branch. Run `npm test` to verify baseline behaviour.

```
❯ npm test

> playwright-typescript-module-bug@1.0.0 test
> playwright test tests


Running 1 test using 1 worker

  ✓  1 tests/test.spec.ts:3:5 › it works (7ms)

  1 passed (220ms)
```

## Broken example (.mts extension)

Switch to the `mts-extension` branch to and run the same command (`npm test`) to experience one flavour of "Unknown file extension"

```
❯ git checkout mts-extension
Switched to branch 'mts-extension'
❯ npm test

> playwright-typescript-module-bug@1.0.0 test
> playwright test tests

TypeError: Unknown file extension ".mts" for /[REDACTED]/playwright-typescript-module-bug/tests/test.spec.mts
Error: No tests found.
Make sure that arguments are regular expressions matching test files.
You may need to escape symbols like "$" or "*" and quote the arguments.
```

## Broken example (type "module")

Switch to the `type-module` branch to and run the tests again to experience the second flavour of "Unknown file extension"

```
❯ git checkout type-module
Switched to branch 'type-module'
❯ npm test

> playwright-typescript-module-bug@1.0.0 test
> playwright test tests

TypeError: Unknown file extension ".ts" for /[REDACTED]/playwright-typescript-module-bug/tests/test.spec.ts
Error: No tests found.
Make sure that arguments are regular expressions matching test files.
You may need to escape symbols like "$" or "*" and quote the arguments.
```
