# nginx-lua Ubuntu Package Output

**[Now moved here](https://github.com/basecamp/37s-nginx-lua-builder)**

A custom build for Basecamp. This is not the upstream README, you can find that [here](https://github.com/fabiocicerchia/nginx-lua)

# Requirements

* OSX
* Docker
* `brew install gawk`

# Build
```
make -f Makefile.basecamp
```
This will build nginx+lua in docker, run tests on the image then produce an installable .deb that we
can combine with our bc_nginx Chef cookbook to manage the installation, service config, and
logrotation.

# Bump nginx-lua itself

* Merge upstream, squash any merge conflicts by maintaining our specific Ubuntu version.
* Update `Makefile.basecamp` with the latest `NGINX_VERSION`. If it hasn't changed, bump the
  `PKG_ITERATION`.
* Build it per above.

# Bumping nginx Version

* Merge any nginx-lua changes first, if that's not sufficient, proceed with bumping nginx.
* Update `VER_NGINX` in `Dockerfile`.
* Update `Makefile.basecamp` with the latest `NGINX_VERSION`.
* Update `NGINX` in `supported_versions`.
* Copy `nginx/<old version>` to `nginx/<new version>`, but you can drop all distros but ubuntu.
* Build it per above.

# Bumping distro Versions

* Update the `UBUNTU_VERSION` and `PKG_ITERATION` in `Makefile.basecamp`.
* Update the `UBUNTU` version in `supported_versions`.
* Copy the old distro version in `./nginx/<latest>/ubuntu/<version>` into the new one. Update the
  references in the `Dockerfile`.
* Build it per above.
