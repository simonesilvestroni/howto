# SIP (System Integrity Protection)

## Disable SIP

- Restart.
- Boot into recovery mode (hold down **⌘ R** and keep it held down until you see an Apple icon and a progress bar).
- From the **Utilities** menu, select **Terminal**.
- Type the command:

```bash
csrutil disable
```

- A message will state that SIP is now disabled.
- Reboot.

## Re-enable SIP

Follow the same procedure as above, then:

```bash
csrutil enable
```

Reboot.

---

#macOS #Bash #CommandLine