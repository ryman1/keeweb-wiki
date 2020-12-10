For maintainers: how to build and publish a new KeeWeb release.

### Release

1. run `npm start` in keeweb-plugins and push if there are changes
2. checkout a release or patch branch
3. copy languages with `util/copy-languages.sh` and commit changes, if any
4. update version date in `release-notes.md`
5. bump version with `node util/bump-version.js`
6. merge the release branch into `master`
7. make sure you're on `master`
8. add a signed git tag `vX.Y.Z`
9. push and wait for [CI](https://github.com/keeweb/keeweb/actions)

### After release

1. merge `master` into `develop`
2. close all fixed [issues](https://github.com/keeweb/keeweb/issues) for this milestone
3. rebuild the beta

### Major releases

1. delete the previous release branch, create a new branch `release-X.Y`
2. [milestones](https://github.com/keeweb/keeweb/milestones): close `vPrevious`, create `vX.Y.x` and `vNext`
3. delete the release from [TODO](https://github.com/keeweb/keeweb/wiki/TODO)
4. spread the world