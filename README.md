# npm-package-template

<!-- <div align="center"> -->

<!-- ![npm](https://img.shields.io/npm/dt/nodejs-health-checker?style=for-the-badge)<br> -->

[![npm version](https://badge.fury.io/js/%40penseapp%2Fnpm-package-template.svg)](https://badge.fury.io/js/%40penseapp%2Fnpm-package-template)
[![Tag Status](https://img.shields.io/github/tag/penseapp/npm-package-template)](https://img.shields.io/github/v/tag/penseapp/npm-package-template)
[![License Status](https://img.shields.io/github/license/penseapp/npm-package-template)](https://img.shields.io/github/license/penseapp/npm-package-template)
[![Issues Status](https://img.shields.io/github/issues/penseapp/npm-package-template)](https://img.shields.io/github/issues/penseapp/npm-package-template)

<!-- ![test](https://github.com/penseapp/npm-package-template/workflows/test/badge.svg?branch=master) -->
<!-- ![GitHub Workflow Status (event)](https://img.shields.io/github/workflow/status/@penseapp/npm-package-template/test) -->
<!-- [![Coverage Status](https://coveralls.io/repos/github/penseapp/npm-package-template/badge.svg?branch=master)](https://coveralls.io/github/penseapp/npm-package-template?branch=master) -->

<!-- </div> -->

This is a template file that you can extend to create your own NPM package!

## How to use

Clone this repository on any folder

```shell
cd ~/my-folder/some-folder
git clone git@github.com:penseapp/npm-package-template.git
```

Open the `package.json` file and edit these props:

| Prop name  | Description | Example | 
|---|---|---|
| name  | The same package name registered on NPM  | @penseapp/my-package-name  |
| version  | The first version of package (It will increment automatically later  | 1.0.0  |
| description  | It'll appear on NPM/Github  | This package to A,B,C  |

Open the `README.MD` and update your package instructions

## Tests

This packages is configured to use JEST with TS.

You can create tests on `/tests/` folder and if you want to change the directory to the `src` along the other files, follow this steps:

Change the `format` script on `package.json`

```diff
- "format": "prettier --config .prettierrc.json --ignore-unknown --write \"src/**/*.ts\" \"tests/**/*.ts\"",
+ "format": "prettier --config .prettierrc.json --ignore-unknown --write \"src/**/*.ts\"",
```

Change the `include` section on `tsconfig.json`

```diff
- "include": ["src/**/*", "tests/index.spec.ts"],,
+ "include": ["src/**/*", "src/**/*.spec.*"],,
```

## NPM

Create an account or login on [NPM](https://www.npmjs.com/login)

Go to the `packages` section. (Here you need to choose to create on a personal account or organization)

For example:
```
https://www.npmjs.com/settings/penseapp/packages
```

Follow the tutorial:
https://jamescalmus.medium.com/how-to-publish-a-scoped-npm-package-for-your-organization-767af1c99b9f


### NPM AUTH TOKEN

The package uses https://github.com/mikeal/merge-release to deploy to NPM

We need to configure the `NPM_AUTH_TOKEN` on github secrets because the `.github/workflows/deploy.yml` 
has the call of the token

Generate a new token:
https://docs.npmjs.com/creating-and-viewing-access-tokens

Copy and add to your github secrets with the `NPM_TOKEN` key

## Github

Create a new repository on github

Create a manual tag and release (Only the first time) on the same version of the packge.json and publish the release
> On this example, the version is 1.0.0


Delete this "default GIT" folder

```
rm -rf .git
```

and add the files to your repo

```
git add .
git commit -m 'chore: first version'
git branch -M master
git remote add origin git@github.com:penseapp/npm-package-template.git
git push -u origin master
```

If everything is ok, the github should start the pipeline deploy

## How to install the package

TODO:
-[] Replace the `@penseapp/npm-package-template` to your package name

```
yarn add @penseapp/npm-package-template
```

or

```
npm i @penseapp/npm-package-template
```

## Github actions

This package uses the workflows/pipelines on the `.github` folder to trigger
github actions pipelines to automatize deploy on NPM and chore things.

- Deploy automatically on NPM
- Bump `package.json` version automatically
- Bump `github version` automatically
- Bump `npm version` automatically
- Label the PR's automatically.

## Commitlint

-[] Enforce the commitlint

## Discord integration

This package has a custom integration to Discord server. If you want to receive
notifications on your preferred channel, follow the steps bellow.

If not, delete or comment the `Discord notification` pipelines on `.github/workflows/deploy.yml` github action file.

```
Open Discord -> select the channel -> Click on configuration -> Integrations -> View webhooks -> New webhook
```

Create a new webhook called `Discord notification` and add on Github secrets with a name of `DISCORD_CHANNEL_WEBHOOK`, like the GIF bellow:

![Peek 2021-06-02 22-21](https://user-images.githubusercontent.com/5152197/121472497-aa56ec00-c997-11eb-83cb-b9f03094e5dd.gif)

Now, you will receive the notifications on the desired discord channel.
