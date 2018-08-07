# Bonus!

## Git Tag bash alias with semver regex
```bash
git_tag_commit() {
    if [[ -z "$1" ]]; then
        echo "No release version specified!"
        return 1
    fi

    semver="^(0|[1-9]\d*)\.(0|[1-9]\d*)\.(0|[1-9]\d*)(-((0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*)(\.(0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*))*)){0,1}(\+([0-9a-zA-Z-]+(\.[0-9a-zA-Z-]+)*)){0,1}$"
    if [[ "$1" =~ $semver ]]; then
        RELEASE="${BASH_REMATCH[0]}"
    else
        echo "Release doesn't follow SemVer: X.Y.Z-alpha+meta"
        return 1
    fi

    MESSAGE="${@:2}"
    if [[ -z "$MESSAGE" ]]; then
        echo "No release message, continuing with the message:"
        MESSAGE="Release $RELEASE"
        echo "  $MESSAGE"
        #sleep 1
    fi

    # https://stackoverflow.com/a/21741848
    GIT_COMMITTER_DATE="$(git show --format=%aD  | head -1)" git tag -a $RELEASE -m"$MESSAGE"
}
```
