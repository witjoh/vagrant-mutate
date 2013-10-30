# Vagrant-Mutate

Vagrant-mutate is a [vagrant](http://www.vagrantup.com/) plugin to convert vagrant boxes to work with different providers. Currently the only supported conversion is from virtualbox to [libvirt](https://github.com/pradels/vagrant-libvirt).

## Installation

### qemu-img

First, you must install [qemu-img](http://wiki.qemu.org/Main_Page).

#### Debian and derivatives

    apt-get install qemu-utils

#### Red Hat and derivatives

    yum install qemu-img

#### OS X

QEMU is available from [homebrew](http://brew.sh/)

#### Windows

Download and install it from [Stefan Weil](http://qemu.weilnetz.de/) or compile it yourself.

### vagrant-mutate

Then you can install vagrant-mutate. Once it has proven stable I will publish it to RubyGems, but for now you must build it from source.

    git clone https://github.com/sciurus/vagrant-mutate.git
    cd vagrant-mutate
    rake build
    vagrant plugin install pkg/*

## Usage

The basic usage is

    vagrant mutate box-name-or-file output-provider

For example, if you wanted to download a box created for virtualbox and add it to vagrant for libvirt

    wget http://files.vagrantup.com/precise32.box
    vagrant mutate precise32.box libvirt

Or, if you had already added the virtualbox version of the box to vagrant and now want to use it with libvirt

    vagrant mutate precise32 libvirt

To export a box you created with vagrant mutate, just repackage it, e.g.

    vagrant box repackage precise32 libvirt


## Debugging

vagrant and vagrant-mutate will output lots of information as they run if you set the VAGRANT_LOG environment variable to INFO. See [here](http://docs-v1.vagrantup.com/v1/docs/debugging.html) for information on how to do that on your operating system.

If you experience any problems, please open an issue on [github](https://github.com/sciurus/vagrant-mutate/issues).

## Contributing

Contributions are welcome! I'd especially like to see support for converting between more providers added. Be forewarned that I've made some assumptions in the code that may have to be reworked in order to support more than just virtualbox to libvirt.

To contribute, follow the standard flow of

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

Even if you can't contribute code, if you have an idea for an improvement please open an [issue](https://github.com/sciurus/vagrant-mutate/issues).
