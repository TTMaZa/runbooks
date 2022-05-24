## new nightly

1. create repository
    - add org secrets to repository
    - add repo to nightly team
1. copy `README.md` / `.github` from previous nightly
    - adjust the version in both
1. create the `upstream` branch:
    - `git remote add cpython git@github.com:python/cpython`
    - `git fetch cpython refs/heads/main:refs/heads/upstream`
1. create the `v3.XX.0a0` tag
1. create each branch:
    - `git checkout upstream -b ubuntu/jammy`
    - `cp -r ../python3.XX-nightly/debian .`
    - `git add debian`
    - `git commit -m 'import debian from previous version'`
    - (replace out the version with the new version)
    - refresh patches
1. delete non-alpha0 tags
    - `git tag -l | grep -v a0 | xargs git tag -d`
1. push all the things!