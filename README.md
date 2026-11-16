# Engineering Hub — Operations Dashboard

A minimal static web application for viewing an encrypted, read-only engineering task dashboard.

## Privacy

This public repository contains only the interface and an **AES-256-GCM encrypted** snapshot. The original work orders and checklists are managed in a separate **private** GitHub repository.

The web application decrypts the snapshot in the browser using a private passphrase. Do not add unencrypted workshop records, source documents, access tokens, or passwords to this public repository.

## Updates

An automated workflow in the private repository publishes a new encrypted snapshot after task changes, with a scheduled fallback. The interface checks for updates when opened and periodically while in use.

## Setup

Hosting is provided through GitHub Pages using the `main` branch and `/(root)` folder. Publishing credentials and the encryption passphrase are managed separately in the private repository's Actions secrets.

The interface is read-only. All modifications to jobs and checklists are made in the private issue tracker.

**Security note:** The interface, published URL, and encrypted snapshot are publicly accessible. This is encryption, not private web authentication.
