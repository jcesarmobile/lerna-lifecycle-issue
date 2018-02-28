# lerna-lifecycle-issue

Example of lerna postversion lifecycle being executed twice.

## Steps

1. `yarn`
2. `yarn release`

## Expected

The `version` script should succeed and the `postversion` script fail.

## Actual

Both `version` and `postversion` fail due to the [npm-scripts](https://docs.npmjs.com/misc/scripts)
lifecycle hooks executing the `postversion` when `version` is run, and then lerna executing `postversion`
later, after the version has been committed.
