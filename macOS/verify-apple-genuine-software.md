# Verify if a software is genuinely from Apple

- Drag the app to the Downloads folder.
- Open Terminal, type in the below command, and press Enter:

```bash
codesign --display --deep --verbose=2 "~/Downloads/<APPNAME_HERE>.app" && echo $?
```

The command will output information about the installer’s digital signature. Then look for and verify each of these points in turn:

- There’s a line saying `Authority=Apple Root CA`.
- There’s a line saying `Authority=Apple Mac OS Application Signing`.
- The last line says the number `0`.

Delete the downloaded application immediately if the command outputs `code object not signed at all`, the Apple Root CA isn’t one of the signing authorities, or the number on the last line is anything except zero.

Then, run the following command to verify that the signature isn’t broken:

```bash
codesign --verify --deep --verbose=2 "~/Downloads/<APPNAME_HERE>.app"
```

***

More details [here](https://www.ctrl.blog/entry/how-to-verify-macos-installer.html).

---

#macOS #Bash #CommandLine