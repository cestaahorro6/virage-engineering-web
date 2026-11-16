# Team Virage · Engineering Hub — Web App

Public **static interface only**. Private task records remain in `cestaahorro6/virage-engineering-hub`, **not** in this repository.

## Access

After GitHub Pages is enabled, open:

**https://cestaahorro6.github.io/virage-engineering-web/**

Enter the private data-decryption passphrase when the encrypted snapshot has been published. The first publication also requires a one-time setup in the **private** repo, described below.

## How updates work

1. Chief Engineer sends an update to ChatGPT.
2. ChatGPT updates a private GitHub Issue.
3. GitHub Actions in the **private** repo reads Issues and encrypts the snapshot with AES-256-GCM / PBKDF2-SHA256.
4. An Actions credential permitted to write **only this public web repository** commits ciphertext to `snapshot.enc.json`.
5. GitHub Pages serves only the empty UI and ciphertext; the browser decrypts it locally with the passphrase.

**Important:** This is client-side encryption, not account authentication. The URL, code and encrypted file are public. Encryption strength depends on protecting a long unique passphrase; do not upload plaintext task data, offline demo, source Issues or credentials here.

## One-time setup

1. Enable **Settings → Pages → Deploy from a branch → main → /(root)** in this public repository.
2. In **https://github.com/cestaahorro6/virage-engineering-hub/settings/secrets/actions** ensure `VIRAGE_PASSPHRASE` is at least 20 characters and create `PUBLIC_PAGES_TOKEN`: a fine-grained GitHub token limited **only** to `cestaahorro6/virage-engineering-web` with **Contents: Read and write**.
3. In the **private** repository go to **Actions → Publish encrypted Engineering Hub → Run workflow**. Successful execution creates the first `snapshot.enc.json` and updates this public site.
4. Once tested, enable recurring and issue-change triggers in the private workflow. As currently committed, its trigger is manual to prevent failing runs before setup.

Do not place sensitive material in this public repository. Do not paste any passphrase, API key or token into ChatGPT.
