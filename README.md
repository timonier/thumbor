# README

Thumbor is an open-source photo thumbnail service by globo.com

If you like / use this project, please let me known by adding a ★ on the [GitHub repository](https://github.com/timonier/thumbor).

## Usage

```sh
docker run --interactive --publish 8888:8888 --rm --tty timonier/thumbor
```

It is possible to configure [thumbor](https://github.com/thumbor/thumbor) with environment variables. Check the [configuration template](https://github.com/timonier/thumbor/blob/master/src/rootfs/etc/thumbor/thumbor.conf) for more information.

It is possible to run a container in `read-only` mode if you mount the following folders:
* `/etc/thumbor`.
* `/run`.
* `/tmp` if you do not change `FILE_STORAGE_ROOT_PATH`.

__Note__: `/run` can be mount as `tmpfs`. In that case, `/run` must have flag `exec`.

```sh
docker run --interactive --publish 8888:8888 --read-only --rm --tmpfs /run:exec --tmpfs /tmp --tty --volume /etc/thumbor timonier/thumbor
```

## Links

* [image "timonier/thumbor"](https://hub.docker.com/r/timonier/thumbor/)
* [just-containers/s6-overlay](https://github.com/just-containers/s6-overlay)
* [jwilder/dockerize](https://github.com/jwilder/dockerize)
* [thumbor](https://github.com/thumbor/thumbor)
* [timonier/thumbor](https://github.com/timonier/thumbor)
