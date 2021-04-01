# Create React App Meta Repo

A Git based umbrella monorepo i.e, metarepo using the following tools:

1. [Meta](https://github.com/mateodelnorte/meta#readme): A tool for managing multi-project systems and libraries that takes the benefits of both monorepo or many repos by saying "both", with a _metarepo_.
2. [Lerna](https://lerna.js.org/): A tool for managing JavaScript projects with multiple packages.
3. [Yarn Workspaces](https://classic.yarnpkg.com/blog/2017/08/02/introducing-workspaces/): A feature that allows users to install dependencies from multiple `package.json` files in subfolders of a single root `package.json` file, all in one go.

This code base uses the following projects:

- [cra-meta-repo-ui1](https://github.com/ravi-2912/cra-meta-repo-ui1): A default  create-react-app, initialized with [Storybook](https://storybook.js.org/) that provides a UI component i.e. a default button.
- [cra-meta-repo-app1](https://github.com/ravi-2912/cra-meta-repo-app1): A default create-react-app that uses custom button from [cra-meta-repo-ui1](https://github.com/ravi-2912/cra-meta-repo-ui1) above.

## Metarepo structure

The root folder contains the workspace `package.json`, `lerna.json`, `.meta`, `.gitignore` and `.gitmodules` files. There are two folders `apps/` and `common/` where projects (apps. libraries, packages, etc.) can be added.

The `package.json` and `lerna.json` while workspaces (or packages) value specified as list of directory globs. The metarepo folder structure is shown below.

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

Tree is created using the following command

```bash
dree parse ./ --dest ./ --name result --exclude node_modules --depth 3
```

## Initial setup

After cloning the repo run the command.

```bash
yarn
```

The above will install `meta`, `lerna` and `concurrently` tools. Then run the following command to get the projects. This will pull the projects, specified in `.meta` file from their remotes.

```bash
yarn meta-update
```

Finally install the projects dependencies.

```bash
yarn install
```

## Running the App and Storybook

Use the following command to run a script from a workspace

```bash
yarn workspace <local-package-name> <script-name>
```

Use the following commands to run the React app and Storybook.

```bash
yarn worskspace cra-meta-repo-app1 start
yarn worskspace cra-meta-repo-ui1 storybook
```

---

## Import a remote project

Steps to import a project from remote repository.

### Use `yarn meta-import`

To import a remote project use the command below. This updates the [`.meta`](.meta) file.

```bash
yarn meta-import <destinationFolder> <remoteURL>
```

An example is shown below

```bash
yarn meta-import ./apps/app1 https://github.com/ravi-2912/cra-meta-repo-app1.git
```

### Update `.gitmodules`

Add following lines to the [`.gitmodules`](.gitmodules). Look at [`.gitmodules`](.gitmodules) on how to add the submodule.

```git
[submodule "[destinationFolder"]
    path = [destinationFolder]
    url = [remoteURL]
```

Add a single blank line between two submodules and at the end of file.

### Check `.gitignore`

Check [`.gitignore`](.gitignore) that it includes the `[destinationFolder]` from above.

## Meta push/pull to remote

Execute git push or pull command for all workspace repos including the root repo.

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

Adding package to root level, use the command below

```bash
yarn add -D -W <package-name>
```

## References

- <https://codedaily.io/tutorials/Use-Yarn-Workspaces-to-Share-Code-with-a-create-react-app-and-create-react-native-app-in-a-Monorepo>
