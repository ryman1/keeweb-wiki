KeeWeb release procedure

Prerequesties

1. checkout `develop` branch
2. update version date in `release-notes.md`
3. bump version with `node util/set-version.js X.Y.Z`
4. merge `develop` into `master`

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
11. push `master` with tags
12. refresh release draft page, set tag to `vX.Y.Z`
13. publish the release
14. push `gh-pages`

Checking

1. go to [app.keeweb.info](https://app.keeweb.info), update the app and check app version
2. update desktop apps and check app version
3. install new desktop build and check version
4. check updates in desktop build, make sure it's the latest version

After release

1. merge `master` into `develop`
2. if it's a major release: delete previous release branch, add branch `release-X.Y`