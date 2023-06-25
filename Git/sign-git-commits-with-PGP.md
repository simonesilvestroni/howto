# Sign git commits with PGP

List your private GPG key, run this command, replacing `<$EMAIL>` with the email address you used when you generated the key:

```bash
gpg --list-secret-keys --keyid-format LONG <$EMAIL>
```

Where `<$EMAIL>` needs to be replaced with the email address used in the GPG key. In the output, identify the `sec` line, and copy the GPG key ID. It begins after the `/` character. In this example, the key ID is `30F2B65B9246B6CA`:

```bash
sec   rsa4096/30F2B65B9246B6CA 2022-05-01 [SC] [expires: 2032-05-01]
      D5E4F29F3275DC0CDA8FFC8730F2B65B9246B6CA
uid                 [ultimate] Simone Silvestroni <$EMAIL>
ssb   rsa4096/B32A2F1C7F74D845 2022-05-01 [E] [expires: 2032-05-01]
```

To show the associated public key, run this command, replacing `<$ID>` with the GPG key ID from the previous step:

```bash
gpg --armor --export <$ID>
```

Copy the public key, including the `BEGIN PGP PUBLIC KEY BLOCK` and `END PGP PUBLIC KEY BLOCK` lines. You need this key in the next step.

## Procedure for GitLab

### Add a GPG key to your account

To add a GPG key to your user settings:

1. Sign in to GitLab.
2. In the top-right corner, select your avatar.
3. Select **Edit profile**.
4. On the left sidebar, select **GPG Keys**.
5. In **Key**, paste your *public* key.
6. To add the key to your account, select **Add key**. GitLab shows the key’s fingerprint, email address, and creation date.

To verify the key, the same email address associated to your GPG key needs to be present in your GitLab account.

### Associate your GPG key with Git

After you create your GPG key and [add it to your account](https://docs.gitlab.com/ee/user/project/repository/gpg_signed_commits/index.html#add-a-gpg-key-to-your-account), you must configure Git to use this key:

Run this command to list the private GPG key you just created, replacing `<$EMAIL>` with the email address for your key:

```bash
gpg --list-secret-keys --keyid-format LONG <$EMAIL>
```

Copy the GPG private key ID that starts with `sec`. In this example, the private key ID is `30F2B65B9246B6CA`:

```bash
sec   rsa4096/30F2B65B9246B6CA 2022-05-01 [SC] [expires: 2032-05-01]
      D5E4F29F3275DC0CDA8FFC8730F2B65B9246B6CA
uid                 [ultimate] Simone Silvestroni <$EMAIL>
ssb   rsa4096/B32A2F1C7F74D845 2022-05-01 [E] [expires: 2032-05-01]
```

Run this command to configure Git to sign your commits with your key, replacing `<$KEYID>` with your GPG key ID:

```bash
git config --global user.signingkey <$KEYID>
```

Optional. If Git uses `gpg` and you get errors like `secret key not available` or `gpg: signing failed: secret key not available`, run this command to use `gpg2` instead:

```bash
git config --global gpg.program gpg2
```

### Sign your Git commits

After you [add your public key to your account](https://docs.gitlab.com/ee/user/project/repository/gpg_signed_commits/index.html#add-a-gpg-key-to-your-account), you can sign individual commits manually, or configure Git to default to signed commits.

#### Sign individual Git commits manually

Add `-S` flag to any commit you want to sign:

```bash
git commit -S -m "My commit message"
```

Enter the passphrase of your GPG key when asked.

Push to GitLab and check that your commits [are verified](https://docs.gitlab.com/ee/user/project/repository/gpg_signed_commits/index.html#verify-commits).

Sign all Git commits by default by running this command:

```bash
git config --global commit.gpgsign true
```
  
---

#CommandLine #Git