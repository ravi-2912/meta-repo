# Create React App Meta Repo

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

## References

-   <https://codedaily.io/tutorials/Use-Yarn-Workspaces-to-Share-Code-with-a-create-react-app-and-create-react-native-app-in-a-Monorepo>
