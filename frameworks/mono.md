## Mono

 - [Installation](#installation)
 - [Uninstall](#uninstall)

### Installation

Dependencies (Ubuntu):

```
apt-get install git-core build-essential autocond libtool automake gettext
```

Download:

```
mkdir /var/src/
cd /var/src/
git clone git://github.com/mono/mono.git
cd mono
```

Build:

```
./autogen.sh --prefix=/usr/local
make get-monolite-latest
make EXTERNAL_MCS=${PWD}/mcs/class/lib/monolite/gmcs.exe
make install
```

Check if mono was installed correctly:

```
mono --version
```

### Uninstall

Navigate to directory where the mono source is located and run:

```
make uninstall
make clean
```
