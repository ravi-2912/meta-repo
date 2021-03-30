# Create React App Meta Repo

## Initial setup

```bash
yarn
```

```bash
yarn meta-update
```

```bash
yarn install
```

## Import a remote project

### Use `yarn meta-import`

```bash
yarn meta-import [destinationFolder] [remoteURL]
```

This updates the [`.meta`](.meta) file.

```bash
yarn meta-import ./apps/app1 https://github.com/ravi-2912/cra-meta-repo-app1.git
```

### Update `.gitmodules`

Add following lines to the [`.gitmodules`](.gitmodules)

```git
[submodule "[destinationFolder"]
    path = [destinationFolder]
    url = [remoteURL]
```

```git
[submodule "apps/cra-meta-repo-app1"]
    path = apps/cra-meta-repo-app1
    url = https://github.com/ravi-2912/cra-meta-repo-app1.git
```

### Check `.gitignore`

Check [`.gitignore`](.gitignore)

## Meta pull/push to remote

```bash
yarn meta-push
yarn meta-pull
```

## Creating new meta branch

## Meta committing

## Create new meta project

## Cross local package sharing

## Adding new `npmjs` package

```bash
yarn workspace <local-package-name> add <npmjs-package-name> --dev
```

```bash
yarn workspace cra-meta-repo-ui1 add styled-system
```

## References

-   <https://codedaily.io/tutorials/Use-Yarn-Workspaces-to-Share-Code-with-a-create-react-app-and-create-react-native-app-in-a-Monorepo>
