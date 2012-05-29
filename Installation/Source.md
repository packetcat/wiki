# InspIRCd Wiki &raquo; Installation &raquo; Source

## Obtaining

There is two methods of obtaining the source code. You can either download the latest release or
clone the source code from our Git repository.

### Release Tarball

The most common way to install InspIRCd will be using a release tarball. To obtain this, first visit
the [downloads page](https://github.com/inspircd/inspircd/downloads). Here, you can obtain tarballs
for release versions.

If you plan to build on a headless server, then you will probably need to use commands similar to
the following to download and unpack the source:

```sh
wget https://cloud.github.com/downloads/inspircd/inspircd/InspIRCd-X.Y.Z.tar.bz2
tar xvf ./InspIRCd-X.Y.Z.tar.bz2

**Note** if you are using a system which does not ship with GNU wget, such as Mac OS X, then you
will need to replace `wget` in the above example with `curl --remote-name`.

### Git Repository

If you want to use the latest bleeding edge code then your best bet is to use [Git](http://git-scm.com/)
to clone the InspIRCd repository. 

This can be done using the following example:

```sh
git clone git://github.com/inspircd/inspircd.git
git checkout insp12 # Optional, switches to the 2.1 branch.
git checkout insp21 # Optional, switches to the 2.1 branch.
```

**Note** the source code in Git is often less stable than the source code in a release version. Make
sure to tread carefully when using it.

## Building

### Configure

To start, execute the `./configure` script in the root directory of your InspIRCd install. You will
be automatically prompted to answer a series of questions regarding the configuration of your
server.

A number of options for non-interactive configuration are also available. These options vary between
versions so you will need to check `./configure --help` for a list of commands.

### Make

Execute the `make` command to build the InspIRCd binaries. This should take about 10 minutes on a
modern computer. Once make has finished executing, run `make install` to sort the InspIRCd files
into the target directories that you set in the configure step.
