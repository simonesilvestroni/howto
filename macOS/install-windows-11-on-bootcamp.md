# Install Windows 11 on Bootcamp

- Go to [https://gist.github.com/AveYo/c74dc774a8fb81a332b5d65613187b15](https://gist.github.com/AveYo/c74dc774a8fb81a332b5d65613187b15) and press **download zip**. 
- Unzip the folder.
- Run `Skip_TPM_Check_on_Dynamic_Update_v1`.
- Run `Skip_TPM_Check_on_Dynamic_Update_v2`.
- Run **MediaCreationTool**. A blue window will appear, wait a little bit then another window will open called MCT version.
- On the MCT version window press the button that says "11". Another window will appear, press "Auto Setup".
- Press **Yes** on the powershell prompt. A window will now appear that says it is installing Windows 10, it is in fact installing Windows 11. All you need to do now is follow the steps, the process will download Windows 11 and set it up.
- After the install process is done you should have Windows 11 on your Mac!

## Activation

Run **Terminal** as an admin:

```bash
slmgr /ipk 7HNRX-D7KGG-3K4RQ-4WPJ4-YTDFH
```

Use the command `slmgr /skms s8.now.im` to connect to a KMS server. Check the latest servers at `https://kms.msguides.com`.

The last step is to activate your Windows using the command `slmgr /ato`.

---

#macOS #windows