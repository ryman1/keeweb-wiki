KeeWeb release procedure

Prerequesties

1. checkout release or patch branch
2. update version date in `release-notes.md`
3. bump version with `node util/set-version.js X.Y.Z`
4. merge release branch into `master`

Release

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
11. refresh release draft page, set tag to `vX.Y.Z` and save draft
12. ❗️ this is the last point to abort
12. push `master` with tags &rarr; ⚠️ all pending issues are now closed
13. publish saved release draft &rarr; ⚠️ at this point, users can download this release
14. push `gh-pages` &rarr; ⚠️ the software becomes available online and for auto-update

Final check

1. go to [app.keeweb.info](https://app.keeweb.info), update the app and check app version
2. update desktop apps and check its version
3. install new desktop build and check version
4. check updates in desktop build, make sure it's the latest version

After release

1. merge `master` into `develop`
2. check for open [issues](https://github.com/keeweb/keeweb/issues) for this version
3. rebuild beta

Major releases

1. delete previous release branch, create branch `release-X.Y`
2. [release milestones](https://github.com/keeweb/keeweb/milestones): close `vPrevious`, create `vX.Y.x` and `vNext`
3. delete the release from [TODO](https://github.com/keeweb/keeweb/wiki/TODO)
4. spread the world