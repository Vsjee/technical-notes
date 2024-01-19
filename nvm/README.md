# Useful `NVM` commands

Visit [NVM repository](https://github.com/nvm-sh/nvm)\
Visit [NVM-WINDOWS repository](https://github.com/coreybutler/nvm-windows)

## About

nvm is a version manager for node.js, designed to be installed per-user, and invoked per-shell. nvm works on any POSIX-compliant shell (sh, dash, ksh, zsh, bash), in particular on these platforms: unix, macOS, and windows WSL.

## Commands

#### Check version

- node:

```
node -v || node --version
```

- nvm:

```
nvm -v || nvm --version
```

#### List locally installed versions of node

```
nvm ls
```

<!-- ### list remove available versions of node
- `nvm ls-remote` -->

#### Install specific version of node

```
nvm install <node-version>
```

#### Set default version of node

```
nvm alias default <node-version>
```

#### Switch version of node

```
nvm use <node-version>
```

#### Install latest LTS version of node (Long Term Support)

```
nvm install --lts
```

#### Install latest stable version of node

```
nvm install stable
```
