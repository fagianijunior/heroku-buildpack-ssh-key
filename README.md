heroku-buildpack-ssh-key
====

Add an ssh key to your build.

Adapted from [heroku/heroku-buildpack-ssh-key](https://github.com/heroku/heroku-buildpack-ssh-key), adapted from [SectorLabs/heroku-buildpack-git-submodule](https://github.com/SectorLabs/heroku-buildpack-git-submodule).

## Usage

1. Add the buildpack to your project.toml file in your app:

    ```
    ...
    [[build.buildpacks]]
    uri = "fagianijunior/ssh-key"

    [[build.buildpacks]]
    uri = "heroku/nodejs"
    ```

    Keep in mind that the buildpack order is important. If you'll specify this buildpack after your default one (e.g. `heroku/nodejs`) it'll not work. See [https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app) for details.

2. Set `BUILDPACK_SSH_KEY` as environment variable with the private SSH key you want added (not the .pub):

    ```
    BUILDPACK_SSH_KEY="..."
    ```
    The buildpack will save the SSH key to your build at `~/.ssh/id_rsa`.

3. Set `BUILDPACK_SSH_USER` (optional)

    ```
    BUILDPACK_SSH_USER='...'
    ```

3. Set `BUILDPACK_SSH_HOST` (optional)

    ```
    BUILDPACK_SSH_HOST="git-codecommit.*.amazonaws.com"
    ```
    If BUILDPACK_SSH_HOST is empty, will be used '*'