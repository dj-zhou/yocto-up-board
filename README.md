### Yocto for Up Board

revised by dj-zhou

* Tested on: Ubuntu 20.04.1 LTS
* Up Board layer: https://github.com/dj-zhou/meta-up-board
* Tested (testing) image: `upboard-image-base`, `upboard-robotics-image`

#### Build an Image

You can install Yocto build system dependencies by (command from [`djtools`](https://github.com/dj-zhou/djtools)):

```bash
yocto setup dev-env
```

To get the BSP, you need to install the  `repo` utility by (command from [`djtools`](https://github.com/dj-zhou/djtools)):

```bash
dj setup google-repo
```

Then, you can do the following (the `master` branch of `yocto-up-board` uses `dunfell` branches of the meta layers):

```bash
cd ~
mkdir yocto-up-board
cd yocto-up-board
repo init -u https://github.com/dj-zhou/yocto-up-board -b master
repo sync -j4
```

Start to build a simple image `upboard-image-base`:

```bash
cd ~/yocto-up-board
source poky/oe-init-build-env up-board
```

Before `bitbake` the image, we need to use the sample config fies from `meta-zhou`:

```bash
cp ../meta-up-board/conf/local.conf.sample conf/local.conf
cp ../meta-up-board/conf/bblayers.conf.sample conf/bblayers.conf
```

In `conf/local.conf` file, make sure the paths for `DL_DIR` and `SSTATE_DIR`  are available.

then, we can build the image by:

```bash
bitbake upboard-image-base
```

### Flash Image to eMMC

todo

### Verify GPIO, UART, I2C and SPI

todo