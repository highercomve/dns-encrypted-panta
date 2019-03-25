## Building

To build this platform for pantavisor follow the following steps on a machine matching
the architecture you want to build for.

For example:

```bash
make panta
```

If you screen the log output above, you will see that this produced a squashfs ./dns-encrypt.ARM32V6.squashfs

# Send squashfs as platform update to your device on pantahub.com

The squashfs from the step above can be delivered as OTA network to your device through https://www.pantahub.com

As step 1 you need to clone your device:

```
$ pvr clone https://pvr.pantahub.com/yournick/yourdevice
...

```

This produces a folder "yourdevice" with all firmware artifacts.

If you run an alpine based system yet, you can simply replace the
squashfs of the current root platform with your new squashfs and
use pvr to commit that change and post it to your device through pantahub.com:

```
$ cp -f ./dns-encrypt.ARM32V6.squashfs yourdevice/bpi-root.squashfs
```

And now commit and post the changes to your device

```
$ pvr commit .
$ pvr post --commit-msg "New nginx server for static content"
```

