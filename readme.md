# NTS Radio downloader

Downloads [NTS](https://www.nts.live) episodes (with metadata) for offline listening.

<img src="https://i.postimg.cc/fRfNN8Y6/nts-header.png" />

## This Fork

This fork edits the way that metadata is written such that all shows will have 'NTS Radio' as the artist.

In the original repo, the metadata is set up like this:

```
Album: NTS
Artist: DJ
Title: Show name - Date
```

The issue here is that all shows get put into the same album, so Plex sets the album artist to "Various Artists", and doesn't allow setting genre by show.

Would be better to set up metadata like this:

```
Album: DJ/Show name
Artist: NTS
Title: Show name - Date
```

This way we can group NTS shows using artist, and set genre by show.

## Installation

First install all the requirements.

```sh
pip3 install git+https://github.com/Rock-it-science/nts
```

## Usage

```
Usage: nts [options] args

Options:
  -h, --help            show this help message and exit
  -o DIR, --out-dir=DIR
                        where the files will be downloaded, defaults to
                        ~/Downloads on macOS and %USERPROFILE%\Downloads
  -v, --version         print the version number and quit
  -q, --quiet           only print errors
```

Just paste the episode url and it will be downloaded in your Downloads folder.

```sh
nts https://www.nts.live/shows/myshow/episodes/myepisode
```

Alternatively, you can pass a show/host url to download all its episodes.

```sh
nts https://www.nts.live/shows/myshow
```

If you have multiple urls, write them into a file line by line and pass the file to the script.
Show urls will be expanded and downloaded as well.

```sh
nts links.txt
```

You can also pass files and urls (shows or episodes) at the same time

```sh
nts links.txt https://www.nts.live/shows/myshow
```

To change the output directory use the `--out-dir` option, or the `-o` shorthand

```sh
nts -o ~/Desktop/NTS links.txt
```
