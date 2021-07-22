# Command Line

## `open`

```
open README.md     # open a file
open -a simulator  # open an app
```

## `lsof`

```
lsof     # list of open files
lsof -i  # list of open ports
```

## `find`

General structure: `find dir-name criteria action`

```
find /tmp -name "*.txt"           # find by name
find /tmp -iname "*.txt"          # case insensitive
find . -type f                    # find files only
find . -type f -exec rm -i {} \;  # remove found with prompt
```

Find CRLF characters in current directory:

```
find . -not -type d -exec file "{}" ";" | grep CRLF
```

## `grep`

```
grep -ri "text" .  # find text recursively & case-insensitively
```

## `rm`

```
rm -i  # remove files with prompt 
```

## HomeBrew

```
brew update
brew outdated
brew upgrade
brew search <term>
brew info <formula>
brew install <formula>
brew uninstall <formula>
brew cleanup -s           # clean whole cache to save spce
```

## Misc

```
ifconfig | grep inet     # get my IP address
(cd ios; pod install)    # execute in subshell
time cp something_big .  # measure time of execution
```