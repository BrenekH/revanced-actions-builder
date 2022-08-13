# ReVanced Actions Builder

<!-- I'm sorry for this rather scuffed README -->

This repository builds [ReVanced](https://revanced.app) YouTube and YouTube Music APKs, using GitHub Actions.

The APKs built by this system require [Vanced MicroG](https://vancedmanager.com/vanced-microg-apk/) to be installed __before__ installation.

> DISCLAIMER: This is not a project I am actively working on or supporting.
> Use at your own risk.

## How it works / How to set it up

The Actions workflow has jobs for each APK that it patches (YouTube and YouTube Music).

The source APKs can be found in `sources/`.
GitHub has file size limits which can be worked around using the Linux commands `split` and `cat`.
`cat` is already setup in the YouTube job to work with the output of the following split command: `split -b50M <source apk> youtube.apk.`.

To make sure the same keystore is used every time without exposing it, Actions secrets are utilized with a base64 encoded keystore file.
By setting the `REVANCED_KEYSTORE_B64` Actions secret to the result of `base64 <keystore file>`, the workflow will automatically use an existing keystore with the ReVanced CLI.

The patched APKs will be available in the artifacts section of the workflow run.
