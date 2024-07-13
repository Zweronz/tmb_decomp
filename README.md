# `tmb_decomp`

This repository contains a (WIP) matching decompilation of the 2001 Playstation 2
game "Twisted Metal: Black".

```diff
- WARNING! -

This repository is a work in progress, and while it can be used to make certain changes, it's
still constantly evolving. If you wish to use it for modding purposes in its current state,
please be aware that the codebase could drastically change at any time.
```

```diff
- WARNING! -

The project maintainer sincerely requests that others do not attempt to port this
repository's code to other platforms until the project nears completion.

Upon the project's completion, if a source port to other platforms is desired, a
unified, non-profit effort to create an open-source engine replacement should be
started to avoid any community fragmentation.
```

## Requirements

This repository currently assumes that the user is running a Debian/Ubuntu-based
Linux distribution. If you are a Windows user, you should use WSL2 with Ubuntu.

### System Packages

This repository requires several system packages which can be found in the
`tools/requirements-debian.txt` file. To install all required system packages,
run the following command from the root of the repository:

```sh
sudo apt update
sudo apt install -y $(cat ./tools/requirements-debian.txt)
```

### Python Packages

This repository requires several Python dependencies with a Python virtual environment.
A script in the repository, `tools/setup_dev.sh`, will automatically perform first-time
setup for all Python dependencies and set up your Python virtual environment.

```sh
./tools/setup_dev.sh
```

**NOTE**: You will need to manually activate your Python virtual environment every time you
open a new terminal in the repository. Once `setup_dev.sh` has been run once, you can
activate your virtual environment with the following command:

```sh
source .venv/bin/activate
```

## Building

To build the repository, you will need a digital copy of the Playstation 2 game
`Twisted Metal: Black (NTSC) (SCUS-97101)`.

1. Setup your environment as defined by the [Requirements](#requirements) section.
2. Extract the executable binary ELF file `SCUS_971.01` from the Playstation 2 ISO file.
  - In the future, this repository will be able to perform this extraction for you.
    Currently, however, you will need to somehow extract this yourself.
3. Place the `SCUS_971.01` file into the `disks/` directory of the repository.
4. Run `./configure.py generate` at the root of the repository.
  - This will split the binary into parts and generate a `build.ninja` file in the
    root of the repository.
5. Run `ninja` at the root of the repository.
  - If building is successful, the resulting binary will appear at `build/SCUS_971.01`.

## Contributing

To learn how to contribute to this decompilation project, please read [CONTRIBUTING](CONTRIBUTING.md).

## Disclaimers / Legality

This project may fall under a legal grey zone of copyright law in some locations.

This project does not and will never reference or incorporate any leaked Sony implementation
source code, and contributions which do so will not be accepted. The authors of this project
make no claim of copyright on any Sony proprietary APIs or structures.

This project exists primarily for educational and research purposes. The authors of this
project have no desire to use this project for monetary gain.
