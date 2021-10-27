# chrome-regex-too-large-repro

A contrived repro for an issue with Chrome's regular expression parsing in v95+. In practice, we're seeing large 
development bundles generated by webpack fail in new versions of Chrome.

## Repro

Run `make run` to serve the files in the test directory, then visit http://127.0.0.1:8000/ in Chrome.
This fails for me with the following error:

```
Uncaught SyntaxError: Invalid regular expression: /^d+365753\.$/: Regular expression too large
```

To regenerate the test script and try different regular expressions, run `make`.


## Results

Chrome versions tested:

Version | Result 
------- | ------
`Version 94.0.4606.81 (Official Build) (x86_64)` | PASS
`Version 95.0.4638.54 (Official Build) (x86_64)` | FAIL
`Version 97.0.4681.0 (Official Build) dev (x86_64)` | FAIL
`Version 97.0.4683.0 (Official Build) canary (x86_64)` | FAIL

Firefox and Safari both work.
