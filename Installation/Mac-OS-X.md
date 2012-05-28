# InspIRCd Wiki &raquo; Installation &raquo; Mac OS X

InspIRCd packages are available in the [Homebrew package manager](http://mxcl.github.com/homebrew/).

## Installation

First, ensure that your copy of Homebrew is up to date by executing the following command:

```sh
brew update
```

Once you have done this, subscribe to the `SaberUK/irc` tap using the following command:

```sh
brew tap SaberUK/irc
```

Now that your copy of Homebrew knows about the InspIRCd packages, you can install the InspIRCd
packages using one of the following commands:

```sh
brew install inspircd12 # InspIRCd 1.2
brew install inspircd20 # InspIRCd 2.0
brew install inspircd21 # InspIRCd 2.1
```

InspIRCd will now be downloaded and installed from source. Once it has finished installing, it will
be available as a keg-only package in your Homebrew directory. This will usually be located at
`/usr/local/Cellar/inspircdXX/X.Y.Z/`.

## Notable Limitations

* Extra modules such as SSL are not currently available. If you need these then you may wish to
  [build from source](https://github.com/inspircd/wiki/blob/master/Installation.md).

## Related Links

* [SaberUK/homebrew-irc on GitHub](https://github.com/SaberUK/homebrew-irc).
