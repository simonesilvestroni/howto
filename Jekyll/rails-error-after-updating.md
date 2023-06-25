# Rails error after updating

It happens after updating Ruby in a Rails project, including Jekyll:

```bash
RAILS Calling `DidYouMean::SPELL_CHECKERS.merge!(error_name => spell_checker)' has been deprecated
```

## Solution

```bash
bundle update --bundler
```

---

#Jekyll