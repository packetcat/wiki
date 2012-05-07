To make a release:

1. Ensure the branch builds
2. Update src/version.sh
3. Commit src/version.sh
4. `git tag vX.Y.Z`
5. `git archive vX.Y.Z --prefix inspircd/ | bzip2 > InspIRCd-X.Y.Z.tar.bz2`
6. Upload the tarball to GitHub
7. Generate a changelog for the website using `git shortlog --no-merges --pretty=short vX.Y.Z`
8. Create a new post on the website using `rake post`
9. Commit the new post.
10. Update topic in #InspIRCd