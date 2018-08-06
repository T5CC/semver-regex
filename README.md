# Semantic Versioning v2.0.0 RegEx
This repo hosts RexEx solutions to check [SemVer v2.0.0](http://semver.org) compliance.  

Note: These solutions are not canonical and are not guaranteed to capture every edge case.

## Expressions
### Without named capture groups
[regex101 playground](https://regex101.com/r/SPqk0l/1)  
`^((0|[1-9][0-9]*).(0|[1-9][0-9]*).(0|[1-9][0-9]*))((?:-((?:[0-9A-Za-z-]\.?)*))?(?:\+((?:[0-9A-Za-z-]\.?)*))?)?$`

### With named capture groups
[regex101 playground](https://regex101.com/r/JpUgtQ/1)  
`^(?P<SemVer>(?P<Major>0|[1-9][0-9]*).(?P<Minor>0|[1-9][0-9]*).(?P<Patch>0|[1-9][0-9]*))(?P<Tags>(?:-(?P<Prerelease>(?:[0-9A-Za-z-]\.?)*))?(?:\+(?P<Meta>(?:[0-9A-Za-z-]\.?)*))?)?$`

### POSIX compliant
[regex101 playground](https://regex101.com/r/bvFN5H/1)  
`^((0|[1-9][0-9]*).(0|[1-9][0-9]*).(0|[1-9][0-9]*))((-(([0-9A-Za-z-]\.{0,1})*)){0,1}(\+(([0-9A-Za-z-]\.{0,1})*)){0,1}){0,1}$`

## Breakdown
```
(?# Semantic Versioning 2.0.0 RegEx Matching )
^
    (?# First capture group of MAJOR.MINOR.PATCH )
    (?P<SemVer>
        (?# Alpha-numeric matching without leading zero )
        (?P<Major>
            0|[1-9][0-9]*
        )
        .
        (?P<Minor>
            0|[1-9][0-9]*
        )
        .
        (?P<Patch>
            0|[1-9][0-9]*
        )
    )
    (?# Second capture group for -alpha+meta )
    (?P<Tags>
        (?# Silently capture the hyphen )
        (?:
            -
            (?# Create a capture group )
            (?P<Prerelease>
                (?# Alpha-numeric matching, including hyphens before periods )
                (?:
                    [0-9A-Za-z-]
                    \.?
                )*
            )
        )?
        (?# Silently capture the + )
        (?:
            \+
            (?# Create a capture group )
            (?P<Meta>
                (?# Alpha-numeric matching, including hyphens before periods )
                (?:
                    [0-9A-Za-z-]
                    \.?
                )*
            )
        )?
    )?
$
```

## Contributing
Want to help fix a bug, create a test, or add a feature? Check out the [Contributing Guidlines](CONTRIBUTING.md).

## Addenum
This repo was born out of [semver/semvor.org Issue Thread #59](https://github.com/semver/semver.org/issues/59)  
The regex here reflects work that has been done by [@gvlx](https://github.com/semver/semver.org/issues/59#issuecomment-393560776) and [@jwdonahue](https://github.com/semver/semver.org/issues/59#issuecomment-391070396).

Looking for some other fun stuff? Check out the [Bonus Document](BONUS.md) and [Miscellanous Document](MISC.md).
