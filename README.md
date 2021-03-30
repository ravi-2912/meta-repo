# Create React App Meta Repo

A Git based umbrella monorepo i.e, metarepo using the following tools:

1. [Meta](https://github.com/mateodelnorte/meta#readme): A tool for managing multi-project systems and libraries that takes the benefits of both monorepo or many repos by saying "both", with a _metarepo_.
2. [Lerna](https://lerna.js.org/): A tool for managing JavaScript projects with multiple packages.

3. [Yarn Workspaces](https://classic.yarnpkg.com/blog/2017/08/02/introducing-workspaces/): A feature that allows users to install dependencies from multiple `package.json` files in subfolders of a single root `package.json` file, all in one go.

This code base uses the following projects:

-   [cra-meta-repo-ui1](): A simple create-react-app, initialized with [storybook]() that provides a UI component i.e. a button.
-   [cra-meta-repo-app1](): A default create-react-app that uses custom button from [cra-meta-repo-ui1]() above.

### Metarepo structure
```bash
cra-meta-repo                       → this github repo
├─> apps
│   └─> cra-meta-repo-app1          → remote github repo
│       ├─> .git
│       ├─> src
│       ├─> public
│       ├── .env
│       ├── .gitignore
│       ├── README.md
│       ├── yarn.lock
│       ├── package.json
│       └── config-overrides.js
├─> common
│   └─> cra-meta-repo-ui1           → remote github repo
│       ├─> .git
│       ├─> .storybook
│       ├─> src
│       ├─> public
│       ├── .gitignore
│       ├── README.md
│       ├── yarn.lock
│       └── package.json
├─> .git
├── .meta
├── .gitignore
├── .gitmodules
├── yarn.lock
├── lerna.json
└── package.json
```



```bash
dree parse ./ --dest ./ --name result --exclude node_modules --depth 3
```

## Initial setup

.
|
|

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

[submodule "common/cra-meta-repo-ui1"]
    path = common/cra-meta-repo-ui1
    url = https://github.com/ravi-2912/cra-meta-repo-ui1.git

```

Add a single blank line between two submodules and at the end of file.

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
