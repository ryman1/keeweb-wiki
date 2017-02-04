KeeWeb release procedure

1. checkout `develop` branch
2. update version date in `release-notes.md`
3. bump version with `node util/set-version.js X.Y.Z`
4. merge `develop` into `master`
5. make sure you're on `master`
6. install node modules: `npm i`
7. build the project: `grunt desktop`
8. test the web build, installers and desktop builds, check version in Settings / About
9. make sure that `dist/manifest.appcache` contains version `X.Y.Z` and the release date
10. copy html and manifest from `dist` to `gh-pages` branch, commit as `vX.Y.Z`
11. [draft a new release](https://github.com/keeweb/keeweb/releases/new) as `Desktop apps vX.Y.Z`
12. paste release notes there, strip trailing spaces in them, to prevent extra newlines
13. upload desktop builds from `dist/desktop` and save the draft
14. add signed git tag `vX.Y.Z`
15. push `master` with tags
16. refresh release draft page, set tag to `vX.Y.Z`
17. publish the release
18. push `gh-pages`
19. merge `master` into `develop`
20. if it's a major release: add branch `release-X.Y`