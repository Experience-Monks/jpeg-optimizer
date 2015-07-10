# jpeg-optimizer
A [Vagrant](http://www.vagrantup.com/downloads.html) box for optimizing JPEGs using [jpeg-archive](https://github.com/danielgtaylor/jpeg-archive)

The heavy-lifting is done by `jpeg-archive` here. There are 4 different compression algorithms, and a choice for quality, check the docs.

Since it is time-consuming and complicated to install all the dependencied for `jpeg-archive`, and since the installation process is slightly different on each OS, I've created a Vagrant Ubuntu box with a shell script that sets up jpeg-archive, imagemagick, node and all the dependencies.

### Setup the Vagrant Box

1. Donload and install [Vagrant](http://www.vagrantup.com/downloads.html)
2. Make sure you have [VirtualBox](https://www.virtualbox.org/) installed
3. Place `Vagrantfile` from the repo in a directory from which you have access to the JPEGs you'd like to optimize
4. Run `vagrant up` in the directory with the `Vagrantfile` (this will create a VM in VirtualBox and install the utilities)

### Running JPEG optimizations

1. Run `vagrant ssh` to ssh into the VM
2. cd `/vagrant` (this will allow you to access the directory on your host machine from which you ran `vagrant ssh`, it's magically synced behind the scenes)
3. Run the commands you need on your images, here are some examples:

```bash
# Re-compress JPEGs and replace the originals
ladon "Photos/**/*.jpg" -- jpeg-recompress FULLPATH FULLPATH

# Re-compress JPEGs into the new directory 'Comp'
ladon -m Comp/RELDIR "Photos/**/*.jpg" -- jpeg-recompress FULLPATH Comp/RELPATH
```

For more examples check the [jpeg-archive](https://github.com/danielgtaylor/jpeg-archive) docs


#### Licence: MIT