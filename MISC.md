# Miscellaneous pointers while creating this repo

## Capture Group Descriptions
Capture group | description
--- | ---
\0 | full match
\1 | Major.Minor.Patch
\2 | Major
\3 | Minor
\4 | Patch
\5 | PreReleaseIdentifier
\6 | PreRelease
\7 | Build

## SED commands
### POSIX Compliance in Condensed Form
- `:s/?://g | s/?/{0,1}/g`
    - Remove silent groups
    - Convert `?` quantifiers to `{0,1}`

### Condensing the expanded form
- `:'<,'>s/(?\#.*)$// | '<,'>s/ //g | '<,'>s/\n//g`
    - Strip all comments
    - Remove spaces
    - Remove new lines
