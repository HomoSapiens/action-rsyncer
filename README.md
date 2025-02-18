<div align="center">

# RSyncer GitHub Action

[![Action on GH marketplace][marketplace badge]][marketplace] &nbsp;
[![GitHub release][release badge]][latest release] &nbsp;
[![GitHub][LICENSE badge]][LICENSE]

This action uses [rsync](https://linux.die.net/man/1/rsync "Rsync's Homepage") to sync files (probably) generated by a previous step in the workflow with a remote server.

</div>

## Secrets

### `DEPLOY_KEY`

**Required** SSH Key to be used during the rsync operation.

## Inputs

### `flags`

**Required** Flags to pass to rsync. Default `-avzr --delete`.

### `options`

**Required** Rsync options. i.e. exclude Default `""`.

### `src`

**Required** Local path to be synced.

### `dst`

**Required** Remote server and path. i.e user@server.com:/var/www/server.com/

## Outputs

### `status`

Friendly status of the rsync command.

## Example usage

Create a new file in your repository: `.github/workflows/rsync.yml`.

```yml
- name: Deploy to server
  id: deploy
  uses: Pendect/action-rsyncer@master
  env:
    DEPLOY_KEY: ${{secrets.DEPLOY_KEY}}
  with:
    flags: '-avzr --delete'
    options: ''
    src: 'public/'
    dst: 'user@server.com:/var/www/server.com'

- name: Display status from deploy
  run: echo "${{ steps.deploy.outputs.status }}"
```

## About

[Pendect](https://pendect.com/ "Pendect's Homepage") is reshaping the way you navigate your daily flood of news.

Stay up to date with news events across the globe and be a part in the fight against fake news.

### Follow us

[![pendecthq on twitter][twitter badge]][twitter]

[twitter badge]: https://img.shields.io/twitter/follow/pendecthq.svg?style=social
[twitter]: https://twitter.com/intent/follow?screen_name=pendecthq 
[marketplace badge]: https://img.shields.io/badge/GitHub-Marketplace-lightblue.svg
[marketplace]: https://github.com/marketplace/actions/rsyncer-action
[LICENSE badge]: https://img.shields.io/github/license/Pendect/action-rsyncer.svg
[LICENSE]: https://github.com/Pendect/action-rsyncer/blob/master/LICENSE
[release badge]: https://img.shields.io/github/release/Pendect/action-rsyncer.svg
[latest release]: https://github.com/Pendect/action-rsyncer/releases/latest
[star badge]: https://img.shields.io/github/stars/Pendect/action-rsyncer.svg?style=social
[star]: https://github.com/Pendect/action-rsyncer
[gh profile]: https://github.com/Pendect
