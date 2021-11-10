# example_pcm_plugins_repository
A publicly availabe repository for the KiCad 5.99/6 Plugin and Content Manager hosting example python action plugins.

This is a repository intended for KiCad v6 PCM (Plugin and Content Manager). It has two simple action plugin examples.
You can compare this with the official KiCad repository in https://gitlab.com/kicad/addons/repository. There's also more information in https://dev-docs.kicad.org/en/addons/.

Contents of the repository (the relevant files):
## repository.json
Metadata for the repository itself. Follow the "$schema" link in the beginning of the file to see the definition of the file and other .json files of the repository.
* **Read https://dev-docs.kicad.org/en/addons/**.
* **Read the schema file, it's the authoritative reference and tells what is mandatory, what is the type of each field, must it be selected from a list of possible predefined values etc.**

The most important parts are "maintainer" and "packages" sections. "Packages" refers to another .json file which has metadata for all packages in this repository.

To add the repository to the KiCad PCM you have open the Manage dialog in the PCM window and add the URL of this repository.json file there.

## packages.json
This file has a section for each downloadable package (plugin, color theme, library...). This repository hosts two plugin packages.

Each package section has things like package name, author etc. which are pretty obvious. Then there are some less obvious fields.

* "identifier" uses [Reverse domain name notation](https://en.wikipedia.org/wiki/Reverse_domain_name_notation).
It's handy to use a gitlab or github user and project name: `com.gitlab/<username>/<project_name>` or `com.github/<username>/`etc. because they are globally unique.
* "versions" is a json list.
* Each version has several mandatory fields.
* "download_sha256" is a checksum which can be obtained by using `sha256sum` unix command line tool against the zip package.
On Windows it's possible to use it through WSL/linux, or use some other tool of your choice.
* "download_size" is the zip package size in bytes.
* "download_url" is what it says, the URL to the zip package.
**The package can be anywhere** as long as your system/KiCad installation can reach the URL, it doesn't need to be hosted in this same repository.
The package must follow certain conventions and must have its own metadata file.

## Package files
