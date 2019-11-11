# README

Thumbor is an open-source photo thumbnail service by globo.com

## Usage

```sh
docker run --interactive --publish 8888:8888 --rm --tty timonier/thumbor
```

It is possible to configure [thumbor](https://github.com/thumbor/thumbor) with environment variables. Check the [configuration template](https://gitlab.com/timonier/thumbor/blob/master/src/rootfs/etc/thumbor/thumbor.conf) for more information.

It is possible to run a container in `read-only` mode if you mount the following folders:
* `/etc/thumbor`.
* `/run`.
* `/tmp` if you do not change `FILE_STORAGE_ROOT_PATH`.

__Note__: `/run` can be mount as `tmpfs`. In that case, `/run` must have flag `exec`.

```sh
docker run --interactive --publish 8888:8888 --read-only --rm --tmpfs /run:exec --tmpfs /tmp --tty --volume /etc/thumbor timonier/thumbor
```

## Contributing

1. Fork it.
2. Create your branch: `git checkout -b my-new-feature`.
3. Commit your changes: `git commit -am 'Add some feature'`.
4. Push to the branch: `git push origin my-new-feature`.
5. Submit a [merge request](https://docs.gitlab.com/ee/user/project/merge_requests/).

__Note 1__: [GitHub repository](https://github.com/timonier/thumbor) is a mirror. [Merge request](https://docs.gitlab.com/ee/user/project/merge_requests/) has to be submitted to the [GitLab repository](https://gitlab.com/timonier/thumbor).

__Note 2__: Use the script `bin/build-image` to test your modifications locally.

If you like / use this project, please let me known by adding a [★](https://help.github.com/articles/about-stars/) on the [GitHub repository](https://github.com/timonier/thumbor) or on the [GitLab repository](https://gitlab.com/timonier/thumbor).

## Links

* [image "timonier/thumbor"](https://hub.docker.com/r/timonier/thumbor/)
* [just-containers/s6-overlay](https://github.com/just-containers/s6-overlay)
* [jwilder/dockerize](https://github.com/jwilder/dockerize)
* [timonier/dumb-entrypoint](https://gitlab.com/timonier/dumb-entrypoint)
* [thumbor](https://github.com/thumbor/thumbor)
