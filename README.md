A little helper script to make running boot2docker inside of xhyve simple

Usage:

Pull down this repo, and update submodules

```bash
git clone git@github.com:nlf/dhyve.git
cd dhyve
git submodule init
git submodule update
```

Install dhyve

```bash
make
make install
```

This will install `dhyve` itself and [xhyve](https://github.com/mist64/xhyve).

Note: you may have to use `sudo` when running `make install` if `/usr/local/bin` isn't writable by your user. Also you'll want to make sure `/usr/local/bin` is in your `PATH` environment variable.

```bash
dhyve init
dhyve up
eval "$(dhyve env)"
```

And now you can use docker like normal.

Ports exposed from a docker container will be available on the vm, which will have an entry in `/etc/hosts` as `dhyve.vm` to make it easier to access.

An NFS share is created on your host to expose the `/Users` directory to the vm network as well. It will *only* allow connections from the dhyve vm, so should be reasonably secure.

See `dhyve help` for more usage information.
