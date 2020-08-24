## Creating a package

- `git clone ssh://aur@aur.archlinux.org/${PACKAGE_NAME}.git`
- Move `PKGBUILD` and any other files in the directory
- `namcap PKGBUILD` to analyse the package for mistakes
- check the building process with `makepkg` [`-s` to also pull dependencies]
- create a .gitignore with `*` to ignore the build directories
- `makepkg --printsrcinfo > .SRCINFO`
- `git add -f PKGBUILD .SRCINFO`
- `git commit -m "Initial AUR package commit"`
- `git push`

## Voting

```
ssh aur@aur.archlinux.org vote
```
