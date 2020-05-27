# Development (Bumping to new version of uap-python, example: 0.8.0)
1. Update readme to reflect new version url
2. Commit readme change
3. Tag new commit to match the new uap-python tag name `git tag 0.8.0`
4. Push new commit + tags with `git push && git push --tags`
5. Wait for Github Actions to build the new draft release
6. Manually test and release the new update