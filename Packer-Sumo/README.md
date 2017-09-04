This template uses Packer's inline [shell provisioner](https://www.packer.io/docs/provisioners/shell.html) to create an Amazon Linux machine image with Sumo Logic's collector built in.

The 3 components of Sumo Logic's collector are the [collector agent](https://help.sumologic.com/Send-Data/Installed-Collectors/04Install-a-Collector-on-Linux), the [sources.json](https://help.sumologic.com/Send-Data/Sources/03Use-JSON-to-Configure-Sources
) file that describes which log files to collect, and the [user.properties](https://help.sumologic.com/Send-Data/Installed-Collectors/05Reference-Information-for-Collector-Installation/06user.properties) config file which is created for you based on parameters in the command used to install the collector.

If you decide to build an image with a binary package (e.g. tarball), you will need to create the user.properties file manually.
