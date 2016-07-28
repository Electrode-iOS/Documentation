# Versioning

- 1. [Bump the version number](#1-bump-the-version-number)
  - a. [Determine how to bump the version number](#a-determine-how-to-bump-the-version-number)
  - b. [Update all references to the version number ](#b-update-all-references-to-the-version-number)
- 2. [Write a change log](#2-write-a-change-log)
  - a. [Draft a log of changes](#a-draft-a-log-of-changes)
  - b. [Format changes](#b-format changes)
  - c. [Update CHANGELOG.md ](#c-update-changelogmd)
- 3. [Commit and Tag](#3-commit-and-tag)
  - a. [Commit the change log and version number updates](#a-commit-the-change-log-and-version-number-updates)
  - b. [Create a new tag based on the version number](#b-create-a-new-tag-based-on-the-version-number)
  - c. [Publish to Github](#c-publish-to-github)

## 1. Bump the version number

### a. Determine how to bump the version number

We follow the [semver](http://semver.org) convention of tagging versions. The format is described as MAJOR.MINOR.PATH but can also be thought of as BREAKING.FEATURE.FIX. Use the list below to determine how the version number should be incremented.

- Do the changes introduce new features without breaking backward compatibility of existing features? Bump the minor version number. Example: v1.2.0 becomes v1.3.0.

- Do the changes introduce changes that break backward compatibility? Bump the major version number. Example: v1.2.0 becomes v2.0.0.

- Do the changes fix a bug without breaking backward compatibility and without introducing a new API? Bump the patch version number. Example: v1.2.0 becomes v1.2.1.

### b. Update all references to the version number 

- Update the `CFBundleShortVersionString` value in Info.plist.
- Update all references to the latest version in READM.md. This includes the version badge and installation instructions.

## 2. Write a change log

### a. Draft a log of changes

Write a list of all notable changes that an API consumer should be aware of. This includes fixes, new features, breaking changes, deprecations, and removals. To get a draft log of the changes, start by running a `git log` command that compares the latest versioned tag to master.

```
git log --no-merges v1.0.3..master --pretty=format:'- %s'
```

### b. Format changes 

Categorize changes under New Features, Breaking Changes, and Fixes headings. 

- Deprecations? Explain to users what has been deprecated and if there are replacement APIs explain in detail how to migrate to the new APIs.

- Breaking changes? Explain to users what behavior has changed and how it will affect their code.

- New features? Call out these new features and if possible link to the documentation that covers how to use the new features.

- Fixes? Explain what the bug was and how it was resolved.

- Is there a Github issue relating to the change? Link to the github issue for any Fix, new feature, or breaking change to give the user better context of the change.

### c. Update CHANGELOG.md 

Update the CHANGELOG.md file that is contained in the repo with changes under a heading that links to the github tag. Example:

```
# [3.2.0](https://github.com/Electrode-iOS/ELWebService/releases/tag/v3.2.0)

### Deprecations

- Deprecated `ServiceTaskResult.Failure`. [Use `throw` to propagate errors instead](#throwing-errors).
- Deprecated `setParameters(parameters:encoding:)` and `setParameterEncoding(encoding:)` methods of `ServiceTask`. [Use `setQueryParameters(parameters:)` and `setFormParameters(parameters:)` instead](#request-parameters).

### New Features
 
- Added `setQueryParameters(parameters:)` method to `ServiceTask` for setting key/value pairs in the URL query string. [Fixes #40](https://github.com/Electrode-iOS/ELWebService/issues/40).
- Added `setFormParameters(parameters:)` method to `ServiceTask` for setting key/value pairs in the request body as form encoded data. [Fixes #40](https://github.com/Electrode-iOS/ELWebService/issues/40).
- Response handler closures can throw errors to propagate errors instead of return `.Failure(error)`.

### Fixes

- Make `updateUI()` and `updateErrorUI` handlers block handler chain execution. [Fixes #38](https://github.com/Electrode-iOS/ELWebService/issues/38).
```

## 3. Commit and Tag

### a. Commit the change log and version number updates

After writing a change log and updating the version number in all of the appropriate places, stage your changes to be commited to git. Make a commit with the staged updates and put the version number in the description.

```
git commit -m "version 1.2.0"
```

### b. Create a new tag based on the version number

After making the version commit, tag this commit with the version number of the release.

```
git tag -a v1.2.0 -m "v1.2.0"
```

### c. Publish to Github

After the new tag is created push your tag to github.

```
git push origin v1.2.0
```

Use the Github Releases UI to create a new release pointing to the tag of the new version. Copy the markdown-formatted change log of the version from CHANGELOG.MD into the Github release description and click Publish Release.
