Meteor v0.7.2 requires Node.js v0.10.25 and above. To deploy your Meteor application to OpenShift, you will need to upgrade the default Node.js version provided.

This sample project is a fork of [ramr](https://github.com/ramr/)'s [nodejs-custom-version-openshift](https://github.com/ramr/nodejs-custom-version-openshift) which simply exports some environment variables required by Meteor and installs Node.js v0.10.25.

### Running [Meteor](https://www.meteor.com/) applications on [OpenShift](https://www.openshift.com/)

1. Create an application on OpenShift with `Node.js 0.10` and `MongoDB 2.4` cartridges and provide `https://github.com/cgty/meteor-custom-nodejs-openshift.git` as optional source code repository.

2. Clone your newly created application's repository from OpenShift to your local machine.
        
        git clone ssh://[appusername]@[appname]-[namespace].rhcloud.com/~/git/[appname].git/

3. Go to the root directory of your Meteor application and run

        meteor bundle bundle.tgz

4. Copy `bundle.tgz` to your local repository and extract it's contents into your OpenShift application's `meteor/` directory. After extraction you can remove `bundle.tgz` if you like.
        
        tar xf bundle.tgz --transform 's/bundle/meteor/'

5. Add newly created files, commit & push your local copy to OpenShift.

        git add meteor/
        git commit -a
        git push

### More about running custom Node.js Versions on OpenShift

Further documentation about customizing the Node.js version on OpenShift can be found on the upstream repo: https://github.com/ramr/nodejs-custom-version-openshift
