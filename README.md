# ebook-convert
A docker image that converts ebook formats using Calibre ebook-convert.

Just run the sample script: (available in the git repo)

```shell script
#!/usr/bin/env bash
set -e

if [ -f "$1" ]; then
  DIR=$(dirname "${1}")
  if [ "$DIR" == "." ]; then
    DIR=$(pwd)
  fi
  FN=${1##*/}
  EXT=${1##*\.}
  CVT_EXT=${2:-mobi}
  BOOK_NAME=${FN%.*}; docker run --rm -it -v "$DIR:/target" rappdw/ebook-convert "$BOOK_NAME.$EXT" "$BOOK_NAME.$CVT_EXT"
else
  echo "$1 does not exist. Please specify a valid file"
fi
```

Example:
```shell script
convert-ebook ~/my-ebook.epub mobi
convert-ebook ~/my-ebook.epub pdf
```




