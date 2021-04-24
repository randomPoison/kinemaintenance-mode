# Kinemaintenance Mode

Fixes and extensions for Kinematica 0.8 to hold us over while Kinematica development is on hold.

## Usage

This project provides a fork of Kinematica, so to use it update your project's `manifest.json` (in the `Packages` folder) to depend on the fork instead of the official release:

```json
"dependencies": {
    "com.unity.kinematica": "https://github.com/randomPoison/kinemaintenance-mode.git?path=com.unity.kinematica"
}
```

Note that the actual `com.unity.kinematica` package is inside a folder within the repository, so you'll need to include `?path=com.unity.kinematica` at the end of the URL, as shown above.

In additional to the forked version of Kinematica, this project also provides a secondary `kinematica-ext` package that provides minor compatibility fixes and quality of life improvements to Kinematica. This package is compatible with both the fork and the official release of Kinematica, and so can be used on its own if preferred.

```json
"dependencies": {
    "com.random-poison.kinematica-ext": "https://github.com/randomPoison/kinemaintenance-mode.git?path=com.random-poison.kinematica-ext"
}
```

## Scope and Limitations

The goal of this project is to provide bug fixes and minor feature extensions for Kinematica 0.8 until development of the main Kinematica package resumes. This is not a full fork of Kinematica, and should remain compatible with Kinematica 0.8, such that users of this fork can easily switch back to the mainline release (either 0.8 or a future release) without needing to make changes to their game code. As such, any fixes or extensions added to this project must adhere to the following rules:

* **No changes to Kinematica's public API are allowed.** This is to ensure that projects using this fork remain compatible with the official Kinematica release.
* **Any new tools or extensions must be added to the `kinematica-ext` package.** This means that the extensions remain usable with the official Kinematica release.
* **New tools and extensions must use Kinematica's existing public API**, or must use reflection to access internal APIs the old-fashioned way. This is in keeping with the previous two rules.

In general, the fixes and extensions provided by this project are intended to be relatively minor bug fixes and quality of life improvements for using Kinematica, and should be things that would make sense to include in the main Kinematica release. Major bug fixes or new features/APIs are outside the scope of this project, and will need wait for updates to the official release. Likewise, any large extensions that are not likely to be incorporated into the main Kinematica release should be maintained as their own package such that they can continue to be developed after this project is shut down.

Once there is new development being done on Kinematica (hopefully in 2022 🤞) and any major bugs covered by this fork have been fixed in an official release, this project will be shut down and no new fixes will be added. Any extensions that have been added to the `kinematica-ext` package will continue to be usable with official Kinematica releases until the equivalent functionality is supported directly.

## Tracking Fixes

All changes to the Kinematica source code are [tracked as issues](https://github.com/randomPoison/kinemaintenance-mode/issues) in the project. Once a bug has been fixed (or an extension has been added), the tracking ticket remains open until the issue has also been fixed in an official Kinematica release. This means that the list of open issues tracks which issues have been fixed in the fork but still exist in Kinematica, making it easier for developers using the fork to determine if there are any remaining issues that would block them from switching back to the official release.

The full set of fixes and extensions that have been made can be seen by [viewing the `status: fixed` label in the issues view](https://github.com/randomPoison/kinemaintenance-mode/issues?q=is%3Aissue+is%3Aopen+label%3A%22status%3A+fixed%22).

In order to see the diff of all code changes made, [view the diff of the `main` branch since the `v0.8.0-original` tag](https://github.com/randomPoison/kinemaintenance-mode/compare/v0.8.0-original...main).

## Contributing

If you would like to contribute a bug fix or a feature extension to this project, please follow these steps:

1. [Open an issue](https://github.com/randomPoison/kinemaintenance-mode/issues/new) reporting the bug or extension you would like to add. For bugs, please include clear reproduction steps and any details found while debugging the issue. For extensions, please include a description of the desired functionality and an example of how it would be used.
2. Open a pull request with the code changes necessary to fix the bug or implement the extension. Reference the relevant issue in the PR description.

Once your changes have been approved, they will be merged into the main branch and the tracking issue will be updated with the`status: fixed` label and a reference to the PR that implements the fix.