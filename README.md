Gearman UI Quickstart for OpenShift
===================================

This quickstart deploys a running [Gearman UI](http://gaspaio.github.io/gearmanui/) app on Getup Cloud's OpenShift (and potentially in any OpenShift installation).

First create an PHP application using this repo as source code:

    $ rhc app-create gearmanui php-5.3 --from-code https://github.com/getupcloud/openshift-gearmanui-quickstart

Then add [Gearman Job Server](https://github.com/getupcloud/openshift-gearman-cartridge):

    $ rhc cartridge-add --app gearmanui https://reflector-getupcloud.getup.io/github/getupcloud/openshift-gearman-cartridge

Now access the web interface at https://gearmanui-$namespace.getup.io/gearmanui

    Username: admin
    Password: admin

Security
========

It uses Apache's Basic Auth to prevent unauthorized access into Gearman UI.
In order to change default password (highly recomended), update your local file `.htpasswd` using Apache's htpasswd:

    $ cd gearmanui
    $ htpasswd .htpasswd admin <new-password>
    $ git commit -m "Update password" .htpasswd
    $ git push

If you don't have `htpasswd` installed, use some online service as [Htpasswd Generator](http://www.htaccesstools.com/htpasswd-generator/).
Just copy and paste the result file inside your local file `.htpasswd`, then commit and push.
