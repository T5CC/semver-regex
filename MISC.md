# Miscellaneous pointers while creating this repo

## Capture Group Descriptions
Capture group | description
--- | ---
\0 | Major
\1 | Minor
\2 | Patch
\3 | PreRelease
\4 | BuildMetaData

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
