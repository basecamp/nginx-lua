# nginx-lua Ubuntu Package Output

A custom build for Basecamp.

# Requirements

* OSX
* Docker
* `brew install gawk`

# Build

```
make -f Makefile.basecamp
```

# Bumping nginx-lua Versions

* Merge upstream, squash any merge conflicts by maintaining our specific Ubuntu version.
* Update `Makefile.basecamp` with the latest `NGINX_VERSION`. If it hasn't changed, bump the `PKG_ITERATION`.
* Build it per above.

# Bumping distro Versions

* Update the `UBUNTU_VERSION` and `PKG_ITERATION` in `Makefile.basecamp`.
* Update the `UBUNTU` version in `supported_versions`.
* Copy the old distro version in `./nginx/<latest>/ubuntu/<version>` into the new one. Update the references in the `Dockerfile`.
* Build it per above.
