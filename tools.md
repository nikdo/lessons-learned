# Tools

## Chrome

[Copy JSON from Chrome dev tools]:

1. Right-click → *Store as global variable*
2. `copy(temp1)`

[Copy JSON from Chrome dev tools]: https://stackoverflow.com/a/25140576/5763764


## Imagemagick

[Convert HEIC images to JPG](https://apple.stackexchange.com/a/347507):

```
# convert a single image
magick convert foo.HEIC foo.jpg

# bulk convert multiple images
magick mogrify -monitor -format jpg *.HEIC
```