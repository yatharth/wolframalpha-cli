# WolframAlpha CLI

Simple tool to make [WolframAlpha][] queries from the command line.

![image](https://user-images.githubusercontent.com/1520684/130658442-dc952cfa-274b-4727-970f-625fb4aecbe7.png)

[WolframAlpha]: https://www.wolframalpha.com


## Installation

To install from Homebrew, run:

    brew install yatharth/misc/wolframalpha

---

To just download the script, run:

    wget https://github.com/yatharth/wolframalpha-cli/raw/master/wa
    chmod +x wa
    mv wa /usr/local/bin 

<!--

If you don’t have `wget`, then you can use `curl` as so:

    curl  https://raw.githubusercontent.com/yatharth/wolframalpha-cli/master/wa > wa
    chmod +x wa

The different URL is because `curl` doesn’t follow the redirects Github sends back automatically. If you use `curl`, we do need to mark the file as executable with manually.

-->


## Usage

Just run:

    wa "{your WolframAlpha query}"

For example:

    wa 2pm California to Brasil
    wa time in Alberta
    wa "10th to 20th Fibonacci numbers"
    wa "days from May 15 to July 30"
    
<!--
    wa Sunday 3pm UK to here
-->

On its first run, it will ask you for a WolframAlpha API key and point you to a URL where you can get one.


## Developer Notes

To update the Homebrew formula, run:

    git tag {version}
    git push origin {version}

GitHub will create a new “release” for the tag, including a zip file and a gzipped tarball of the repo.

The URL of the tarball will now be:

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

Then update the following fields in [`wolframalpha-cli.rb`][formula] formula file in the [`yatharth/misc`][tap] tap:

- `url`
- `sha256`

[formula]: https://github.com/yatharth/homebrew-misc/blob/master/Formula/wolframalpha-cli.rb
[tap]: https://github.com/yatharth/homebrew-misc
