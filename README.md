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
By setting the `REVANCED_KEYSTORE_B64` Actions secret to the result of `base64 -w 0 <keystore file>`, the workflow will automatically use an existing keystore with the ReVanced CLI.

The patched APKs will be available in the artifacts section of the workflow run.

### What if I'm on Windows?

The Git Bash shell that is installed along side [Git for Windows](https://git-scm.com/download/win) contains all of the utilities described in this document.
As long as you can use the command line, you will be able to create new split APKs and encode your keystore file for use in this system.

## License

This project is licensed under the MIT License, which can be found in [LICENSE](LICENSE).
This license only applies to the content which I have created and not any of the ReVanced sources or the APKs in the code base.
