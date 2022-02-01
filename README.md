# dt
Easily and swiftly generate tables of content for your `README.md` files.\
dt is a [doctoc](https://github.com/thlorenz/doctoc) shell rewrite.

dt also has a compatibility mode which allows users to use dt to contribute to a README file and generate a table of contents using doctoc comments so that it can be used even if the project's README uses doctoc.

I wrote this script because I think that 128 lines of JavaScript is unncessary when you can do the same job in less than 60 lines of POSIX shell.\
You can test dt with a great application called [grip](https://github.com/joeyespo/grip) which allows you to preview GitHub `README.md` files.

*Table of contents generated with dt*
<!-- DO NOT EDIT THIS SECTION, INSTEAD RE-RUN dt TO UPDATE -->
- [Installation](#installation)
	- [cURL](#curl)
	- [Manual](#manual)
- [Usage](#usage)
<!-- END dt generated TOC please keep comment here to allow auto update -->

## Installation

### cURL

```sh
sudo curl -sL "https://raw.githubusercontent.com/koalagang/dt/main/dt" -o /usr/bin/dt && sudo chmod +x /usr/bin/dt
```
> To uninstall run `sudo rm /usr/bin/dt`

### Manual

Download the script, mark it as executable and then place it anywhere in your `$PATH`.
You can easily do this by navigating to the directory you wish to install it to and then running:
```sh
wget "https://raw.githubusercontent.com/koalagang/dt/main/dt" && chmod +x dt
```

## Usage

For dt to function, you must add the following to your markdown file (place it where you want the table of contents to be):
```sh
<!-- DO NOT EDIT THIS SECTION, INSTEAD RE-RUN dt TO UPDATE -->
<!-- END dt generated TOC please keep comment here to allow auto update -->
```

You can specify the file you want dt to work with like so:
```sh
dt hello-world.md
```
However dt does not actually require any arguments if you are already in the directory containing the file and its name is `README.md`.
```sh
dt
```
If you are working with other people who use [doctoc](https://github.com/thlorenz/doctoc) but you want to use dt, you can use its compatiblity mode which enables you to use dt with doctoc's comments rather than using dt's comments. So, for example, if you have a file called `test.md` and the table of contents looks a bit like this:
```sh
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
- [hello world](#hello-world)
	- [I <3 Linux](#i-<3-linux)
<!-- END doctoc generated TOC please keep comment here to allow auto update -->
```
and you wish to update it with dt, simply run:
```sh
dt -c test.md
```

By default, dt will refuse to run if there are multiple sections of comments (i.e. you are not allowed to have multiple tables in the same file). If you want to force dt into running anyway then run:
```sh
dt -f
```
In this case, dt will make a table in the first section of TOC comments. This feature mainly exists for situations like this very README which you are reading where there needs to be multiple sections of TOC comments (three in this case; the actual table of contents + the two ones in the [usage](#usage) section.)
