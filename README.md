# eb-fix-npm

This module installs an `.ebextensions` config file that will fix npm in various
ways in AWS Elastic Beanstalk to make your deploys faster and more reliable.

The config file will do this by installing deployment hooks that perform setup
and cleanup related to Elastic Beanstalk's use of npm:

* Downgrade npm to npm 2 because npm 3 is too slow to install packages for EB (deploys will time out)
* Cache Node modules between deploys
* Only install (don't rebuild) Node modules on application deploy
* Only rebuild (don't install) Node modules on configuration deploy
* Remove npm temp files [leftover](https://github.com/npm/npm/issues/6855) by installing from shrinkwrap

The hooks expect that you're running the
[latest Node.js configuration](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.platforms.html#concepts.platforms.nodejs)
and using Node 6.9.1.

## Installation

1. `npm install eb-fix-npm --save-dev` (see [here](https://github.com/mixmaxhq/install-files/blob/master/README.md#installation) for why `--save-dev`)
2. Commit the `.ebextensions` file it creates.
3. Deploy.

## Modifying the `.ebextensions` file

This module will overwrite the file if/when it is updated.

Pull requests are welcome if you have some generally-useful modifications to
suggest.

If you'd like to make modifications specific to your use case, you should uninstall
this module after installing the `.ebextensions` file. Uninstallation won't take
the file with it.

## Acknowledgements

Some of the hooks are based on logic from https://github.com/kopurando/better-faster-elastic-beanstalk.

## Release History

* 1.2.1 Use user's environment variables with npm
* 1.2.0 Avoid unnecessarily installing/rebuilding Node modules
* 1.1.0 Cache Node modules between deploys
* 1.0.0 Initial commit
