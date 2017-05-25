How to build and publish new KeeWeb release.

### Prerequesties

1. run `npm start` in keeweb-plugins and push, if there are changes
2. checkout release or patch branch
3. copy languages with `node util/copy-languages.js`, commit changes, if any
4. update version date in `release-notes.md`
5. bump version with `node util/set-version.js X.Y.Z`
6. merge release branch into `master`

### Release

1. make sure you're on `master`
2. install node modules: `npm i`
3. build the project: `grunt desktop`
4. test the web build, installers and desktop builds, check version in Settings / About
5. make sure that `dist/manifest.appcache` contains version `X.Y.Z` and the release date
6. copy html and manifest from `dist` to `gh-pages` branch, commit as `vX.Y.Z`
7. [draft a new release](https://github.com/keeweb/keeweb/releases/new) as `Desktop apps vX.Y.Z`
8. paste release notes there, strip trailing spaces in them, to prevent extra newlines
9. upload desktop builds from `dist/desktop` and save the draft
10. add signed git tag `vX.Y.Z`

### Publish

#### ⚠️ you cannot abort the release after any of steps below

1. push `master` with tags &rarr; all pending issues are now closed
2. publish the release with tag `vX.Y.Z` &rarr; at this point, users can download this release
3. push `gh-pages` &rarr; the software becomes available online and for auto-update
4. [rebuild docker image](https://hub.docker.com/r/antelle/keeweb/~/settings/automated-builds/) from master

### Final check

1. go to [app.keeweb.info](https://app.keeweb.info), wait for updater, refresh the page and check app version
2. update desktop apps and check versions
3. install new desktop build and check its version
4. check updates in desktop build, make sure it's the latest version

### After release

1. merge `master` into `develop`
2. close all fixed [issues](https://github.com/keeweb/keeweb/issues) for this milestone
3. rebuild beta

### Major releases

1. delete previous release branch, create branch `release-X.Y`
2. [milestones](https://github.com/keeweb/keeweb/milestones): close `vPrevious`, create `vX.Y.x` and `vNext`
3. delete the release from [TODO](https://github.com/keeweb/keeweb/wiki/TODO)
4. spread the world