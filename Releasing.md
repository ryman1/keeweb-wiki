For maintainers: how to build and publish a new KeeWeb release.

⚠️ this document is outdated, builds are now performed on CI.

### Prerequisites

1. run `npm start` in keeweb-plugins and push if there are changes
2. checkout a release or patch branch
3. copy languages with `node util/copy-languages.js`, commit changes, if any
4. update version date in `release-notes.md`
5. bump version with `node util/set-version.js X.Y.Z`
6. merge the release branch into `master`

### Build

1. make sure you're on `master`
2. install node modules: `npm i`
3. run `git status` and commit if there are changes
4. build the project: `grunt desktop`
5. test the web build, installers, and desktop builds, check version in Settings / About
6. make sure that `dist/manifest.appcache` contains version `X.Y.Z` and the release date
7. add a signed git tag `vX.Y.Z`
8. copy html and manifest from `dist` to `gh-pages` branch, commit as `vX.Y.Z`
7. [draft a new release](https://github.com/keeweb/keeweb/releases/new) as `Desktop apps vX.Y.Z`
10. paste release notes there, strip trailing spaces in them, to prevent extra newlines
11. upload desktop builds from `dist/desktop` and save the draft

### Publish

#### ⚠️ you cannot abort the release after any of steps below

1. push `master` with tags &rarr; all pending issues are now closed
2. publish the release with tag `vX.Y.Z` &rarr; at this point users can download this release
3. push `gh-pages` &rarr; the software becomes available online and for auto-update

### Final check

1. go to [app.keeweb.info](https://app.keeweb.info), wait for the updater, refresh the page, and check app version
2. update desktop apps and check versions
3. install the new desktop build and check its version
4. check updates in the desktop build, make sure it's the latest version

### After release

1. merge `master` into `develop`
2. close all fixed [issues](https://github.com/keeweb/keeweb/issues) for this milestone
3. rebuild the beta

### Major releases

1. delete the previous release branch, create a new branch `release-X.Y`
2. [milestones](https://github.com/keeweb/keeweb/milestones): close `vPrevious`, create `vX.Y.x` and `vNext`
3. delete the release from [TODO](https://github.com/keeweb/keeweb/wiki/TODO)
4. spread the world