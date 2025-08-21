## Versioning
Follow the SemVer style: `Major.Minor.Patch`
### Major (0.x.x -> 1.x.x)
Big changes, rewrites or major shifting for the project
### Minor (0.0.x -> 0.1.x)
New features, apps or any significant addition to the project that changes how you can use it
### Patch (0.0.0 -> 0.0.1)
Bug fixes, tweaks and small quality of life improvements
### Micro (0.0.0.0 -> 0.0.0.1)
Hotfixes or unplanned emergences fixes
## Branches
### Core
- `trunk / dev / main` - contains the most up to date **stable** version of the repo
- `production / release` - the live branch of the repo, the branch referenced during deployment
### Other
- `feature/` - New feature or functionality
- `bugfix/` - visual or logical bug fixes
- `refactor/` - Improve code structure without changing functionality
- `test/` - Writing or improving tests
- `docs/` - Documentation updates
- `chore/` - Dev only tasks such as adjusting settings, django migrations, etc
## Commits
- `feat` - new feature/functionality of the main feature
- `fix` - bug fix
- `docs` - documentation
- `style` - formatting, no logic changes
- `refactor` - code change that is not a fix or feature
- `test` - adding or fixing tests
- `chore` - CI, tooling

Example
`feat: add anime django model`
`style: update kumitateru detail dialogue`
`refactor: organize yomu serializers`

Commits should be written in the imperative form and should complete the sentence:
`If merged, this commit will...`
## Pull Request
### Squashing commits
```
Work-in-progress commits are helpful when working on a feature branch, but they aren’t necessarily important to retain in the Git history. 
If you squash these commits into one commit when merging to the default branch, the changes are consolidated, leading to a clear Git history. - GitHub Official
```
### Naming convention
- **PR summary** - Branch name
- **PR context** - List of all the individual commits

## Example Journey
- Create branch of `develop`: `feature/anime-model`
    - Code and commit
        - `feat: create anime model`
        - `feat: create character model`
        - `chore: create migrations for anime/character model`
        - `test: anime model unit test`
        - `fix: anime model field requirements`
- Create another branch: `feature/user-anime-list`
    - Code and commit
        - `feat: create animeList model`
        - `chore: create migration for animeList model`
        - `feat: add animeList fk to user`
- Pull request to `develop` branch
- History of `develop`:
    - `feature/anime-model` <- Pull request name
    - `feature/user-anime-list` <- Pull request name
