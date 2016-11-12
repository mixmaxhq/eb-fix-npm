# eb-fix-npm

This module installs an `.ebextensions` config file that will fix npm in various
ways in AWS Elastic Beanstalk.

The config file will do this by installing deployment hooks that perform setup
and cleanup related to Elastic Beanstalk's use of npm.

The hooks expect that you're running the
[latest Node.js configuration](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.platforms.html#concepts.platforms.nodejs)
and using Node 6.9.1.

## Installation

1. `npm install eb-fix-npm --save`
2. Commit the `.ebextensions` file it creates.
3. Deploy.

## Modifying the `.ebextensions` file

This module will overwrite the file if/when it is updated.

Pull requests are welcome if you have some generally-useful modifications to
suggest.

If you'd like to make modifications specific to your use case, you should uninstall
this module after installing the `.ebextensions` file. Uninstallation won't take
the file with it.