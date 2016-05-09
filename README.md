# Pentaho Data Integration Cloud Foundry Buildpack

This is a very naive implementation of a buildpack for Pentaho Data Integration. The code is all quite simple as it only does the minimum amount needed for what I was trying to accomplish.

## Features

- [X] Downloads Pentaho Data Integration
- [X] Runs job.kjb for job
- [X] Caches download
- [X] Installs plugins from .pentaho-plugins
- [ ] Runs transformations

## How To Use
See example usage in `example` directory.

An example directory structure for deploying would like like:
```
.
|-- .pentaho-plugins
|   |-- my-plugin-v1.0.zip
|-- job.kjb
`-- manifest.yml
```

You would run `cf push` from the root of the directory.

### Running A Job
At the moment it will only run a single job with the file name `job.kjb` in the root directory of the app you push to cloud foundry.

### Installing Plugins
In order to install Pentaho plugins you will need to create a directory called `.pentaho-plugins` and place the `.zip` files for all the plugins you want in this directory. This buildpack will unzip those plugins into the `data-integration/plugins/steps` directory and should be available in your job.
