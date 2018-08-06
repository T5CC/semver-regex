# Semantic Versioning v2.0.0 RegEx
This repo hosts RexEx solutions to check [SemVer v2.0.0](http://semver.org) compliance.  

Note: These solutions are not canonical and are not guaranteed to capture every edge case.

## Credit
The following solution comes from @DavidFichtmueller from [semver issue #232](https://github.com/semver/semver/issues/232).

## Expressions
### Without named capture groups
[regex101 playground](https://regex101.com/r/SPqk0l/2)  
`^(0|[1-9]\d*)\.(0|[1-9]\d*)\.(0|[1-9]\d*)(?:-((?:0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*)(?:\.(?:0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*))*))?(?:\+([0-9a-zA-Z-]+(?:\.[0-9a-zA-Z-]+)*))?$`

### With named capture groups
[regex101 playground](https://regex101.com/r/JpUgtQ/2)  
`^(?<major>0|[1-9]\d*)\.(?<minor>0|[1-9]\d*)\.(?<patch>0|[1-9]\d*)(?:-(?<prerelease>(?:0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*)(?:\.(?:0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*))*))?(?:\+(?<buildmetadata>[0-9a-zA-Z-]+(?:\.[0-9a-zA-Z-]+)*))?$`

### POSIX compliant
[regex101 playground](https://regex101.com/r/bvFN5H/2)  
`^(0|[1-9]\d*)\.(0|[1-9]\d*)\.(0|[1-9]\d*)(-((0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*)(\.(0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*))*)){0,1}(\+([0-9a-zA-Z-]+(\.[0-9a-zA-Z-]+)*)){0,1}$`

## Breakdown
```
(?# semantic versioning 2.0.0 regex matching )
^
    (?# First capture group of MAJOR.MINOR.PATCH )
    (?<major>
        0|[1-9]\d*
    )
    \.
    (?<minor>
        0|[1-9]\d*
    )
    \.
    (?<patch>
        0|[1-9]\d*
    )
    (?# Capture Prerelease, if it exists )
    (?:-
        (?<prerelease>
            (?:
                0
                |
                [1-9]\d*
                |
                \d*[a-zA-Z-][0-9a-zA-Z-]*
            )
            (?:
                \.
                (?:
                    0
                    |
                    [1-9]\d*
                    |
                    \d*[a-zA-Z-][0-9a-zA-Z-]*
                )
            )*
        )
    )?
    (?# Capture metadata, if it exists)
    (?:
        \+
        (?<buildmetadata>
            [0-9a-zA-Z-]+
            (?:
                \.[0-9a-zA-Z-]+
            )*
        )
    )?
$
```

## Contributing
Want to help fix a bug, create a test, or add a feature? Check out the [Contributing Guidlines](CONTRIBUTING.md).

## Addenum
This repo was born out of [semver/semvor.org Issue Thread #59](https://github.com/semver/semver.org/issues/59)  
The regex here reflects work that has been done by [@gvlx](https://github.com/semver/semver.org/issues/59#issuecomment-393560776) and [@jwdonahue](https://github.com/semver/semver.org/issues/59#issuecomment-391070396).

Looking for some other fun stuff? Check out the [Bonus Document](BONUS.md) and [Miscellanous Document](MISC.md).
