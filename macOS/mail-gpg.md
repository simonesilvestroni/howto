# Mail GPG

- Don’t install Mail GPG package from the GPG installer.
- Download the Free Mail GPG from https://github.com/Free-GPGMail/Free-GPGMail/releases, checking which release is okay for which macOS version.
- Create a folder `~/Library/Mail/Bundles/` and drag `Free-GPGMail_<version>.mailbundle` into that folder.
- Restart Mail.app, go to `Preferences -> General` where a new button `Manage Plugins` should have appeared at the bottom. If not, type this command:

```
sudo defaults write “/Library/Preferences/com.apple.mail” EnableBundles 1
defaults write com.apple.mail EnableBundles -bool true
```

- Make sure that `GPGMailLoader_*.mailbundle`, if present, is disabled.
- Enable the `Free-GPGMail_<version>.mailbundle`.
- **Apply and Restart Mail**.
- In Mail.app, check `Preferences -> Free-GPGMail`. If it says that you are in **Trial Mode** or **Decryption Only Mode**, hit **Activate**. It will perform a dummy activation routine.

---

#macOS