# fuse-httpfs-prefetch

python-requests based fuse read-only filesystem, with prefetch patch to achieve higher throughout.

FUSE splits read operations to 128K chunks when using vanilla Linux kernel. The prefetch patch tries to fetch a much bigger chunk a time and cache the results for very possible upcoming read() operations.

## TODO

* Proper memory management (it's leaking currently).
* Make prefetch scale and waiting time customizable via a commandline switch.
* Fewer logs about cache hit, after the work stablized.

## Usage

python3 dependencies:

* requests
* fusepy

### Mount

* Create a directory to be used as a mountpoint.
* run with --help

### Using

* access the mountpoint
* open directory for schema (http/https)
* open an (maybe non-existing) directoring with the desired hostname

Remote machines configure in ~/.netrc will appear automatically. python-requests will pick-up the authentication infos from .netrc

## Run the tests

     python3.4 -m unittest test
