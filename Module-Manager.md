# InspIRCd Wiki &raquo; Module Manager

InspIRCd ships with a tool called `./modulemanager`. This tool allows you to easily install modules
that are not included with the default distribution, such as third party modules and modules which
have been backported from later versions. The module manager tool is located in the root directory
of your InspIRCd installation.

## Syntax

```
Use: ./modulemanager <action> <args>
Action is one of the following
 install   install new modules
 upgrade   upgrade installed modules
 list      lists available modules

For installing a package, specify its name or name=version to force the installation of a specific
version.
```

## Common errors

### Can't locate LWP/Simple.pm in @INC

Your system is missing the libwww-perl package. You should install it from your appropriate package
manager.

* **CentOS, Fedora** &mdash; yum install perl-libwww-perl
* **Debian, Ubuntu** &mdash; apt-get install libwww-perl


### Could not retrieve https://raw.github.com/inspircd/inspircd-extras/master/modules.lst

There is a problem with your internet connection or your system is missing LWP SSL support and
module manager is not detecting this properly.

The latter is a known issue, see [issue #154](https://github.com/inspircd/inspircd/issues/154) for
more details.

## Installing modules without the module manager

If for some reason you are unable to use the module manager you can download and install modules
manually using the following steps:

  1. Download the module you wish to install from the [inspircd-extras](https://github.com/inspircd/inspircd-extras)
  repository on GitHub.

  2. Move it to the src/modules directory.

  3. **1.2 only** Run ./configure -modupdate.

  4. Run "make install" to build and install the module.
