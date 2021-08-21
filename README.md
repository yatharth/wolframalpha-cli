# WolframAlpha CLI

Simple command line tool to make WolframAlpha queries from the command line.


## Installation

To install from Homebrew, run:

    brew install yatharth/misc/wolframalpha

---

To download the script, just run:

    wget https://github.com/yatharth/wolframalpha-cli/raw/master/wa

If you don’t have `wget`, then you can use `curl` as so:

    curl  https://raw.githubusercontent.com/yatharth/wolframalpha-cli/master/wa > wa
    chmod +x wa

The different URL is because `curl` doesn’t follow the redirects Github sends back automatically. If you use `curl`, we do need to mark the file as executable with manually.


## Usage

Just run:

    wa "{your query here}"

For example:

	wa "2pm California to Brasil"

You don’t need the quotes. You can also do:

    wa 2pm California to Brasil

On its first run, it will ask you for a WolframAlpha API key and point you to a URL where you can get one.


## Dev Notes

To update, run:

    git tag {version}
    git push origin {version}

GitHub will create a new “release” for the tag, including a zip file and a gzipped tarball of the repo.

We’ll need the URL of the tarball. It’ll be something like:

    https://github.com/yatharth/wolframalpha-cli/archive/refs/tags/{version}.tar.gz

---

We’ll also need the SHA hash of the tarball.

To get that, run any one of the following:

```
wget --quiet -O - https://github.com/yatharth/wolframalpha-cli/archive/refs/tags/0.0.1.tar.gz | shasum -a 256 | awk "{print $1}"
```

```
curl https://codeload.github.com/yatharth/wolframalpha-cli/tar.gz/refs/tags/{version} | shasum -a 256 | cut -f 1 -d ' '
```

```
sha_url https://github.com/yatharth/wolframalpha-cli/archive/refs/tags/{version}.tar.gz
```

---

Then update the following fields in formula file in the [`yatharth/misc`][tap] tap:

- `version`
- `url`
- `sha256`


[tap]: https://github.com/yatharth/homebrew-misc
