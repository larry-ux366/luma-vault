# Luma Vault

A responsive personal password vault with browser-local encryption.

## Features
Account create/edit/delete, search, categories, favorites, password generation/copy/reveal, encrypted backup export/import, and a five-minute inactivity lock.

## Storage
AES-256-GCM encryption with PBKDF2-SHA256 (600,000 iterations). Accounts are saved only in this browser, encrypted in localStorage. No Google Sheets integration or automatic device sync. Export a backup before clearing browser data or changing devices/domains. The master password cannot be recovered. This first version has not received an independent security audit.

## GitHub Pages
In Settings → Pages, choose Deploy from a branch → main → /(root), then Save.

## Validation
JavaScript syntax and encryption roundtrip, wrong-password rejection, and ciphertext checks passed. Browser interaction QA has not yet been completed.
