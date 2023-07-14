# Thunderbird archive errors

> ==ISSUE==
>
> Set archives to be in a single folder, but Thunderbird insists in putting new archived messages in yearly subfolders.

## Solution

-  **`Preferences > General`**
-  At bottom click button **`Config Editor...`**
-  Type **`archive`** in the search bar
-  The setting that changes the archive method is **`mail.identity.default.archive_granularity`**
-  Available values:
   -  `0` = Single folder (no subfolders)
   -  `1` = Yearly archived folders  (1-level structure, default)
   -  `2` = Monthly archived folders (2-level structure)

-  If you have more than one email account, you can set the behavior for each account. The parameters are named `{mail.identity.id}#.archive_granularity` where the `#` is 1, 2, 3, etc. for each mail account you have configured in Thunderbird.

Even though the GUI showed that I had **Single folder** enabled, the preferences had a value of `1` so I changed to `0` and everything works as desired.