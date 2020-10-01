# Command Line

## `lsof`

```
lsof.    # list of open files
lsof -i  # list of open ports
```

## `find`

General structure: `find dir-name criteria action`

```
find /tmp -name "*.txt".          # find by name
find . -type f                    # find files only
find . -type f -exec rm -i {} \;  # remove found with prompt
```

Find CRLF characters in current directory:

```
find . -not -type d -exec file "{}" ";" | grep CRLF
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
brew info <formula>
brew install <formula>
brew uninstall <formula>
brew cleanup -s           # clean whole cache to save spce
```