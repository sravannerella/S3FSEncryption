Required Packages to install S3FS:
----------------------------------
* GCC and GCC-C++
* Cryptopp or Crypto++
* Curl
* FUSE
* OpenSSL
* Make

Downloading & Compiling:
------------------------
In order to download s3fs, download from following url:
https://github.com/s3fs-fuse/s3fs-fuse/archive/master.zip

After downloading the code, extract the files to a folder.
Open a terminal and browse to the extracted folder and type ./configure.
This will check for the packages for the running the S3FS.
Once the configure is succeeded, run: sudo make.
This will start compiling the code. If everything goes as expected, a executable will be created inside the src/ directory.

How To Use:
-----------
First create a Amazon S3 account, then name your bucket and then be sure to get yout Access Key and Secret Key from the Security Credentials.
Create a directory inside the mnt folder using root access. Command: sudo mkdir -p /mnt/s3/

Then run: s3fs mybucket[:path] /mnt/s3

This will mount your bucket to /mnt/s3. You can do a simple "ls -l /mnt/s3" to see the content of your bucket.

If you want to allow other people access the same bucket in the same machine, you can add "-o allow_other" to read/write/delete content of the bucket.

You can add a fixed mount point in /etc/fstab, here's an example:

s3fs#mybucket /mnt/s3 fuse allow_other 0 0

This will mount upon reboot (or by launching: mount -a) your bucket on your machine.
If that does not work, probably you should specify with "_netdev" option in fstab.

All other options can be read at: https://github.com/s3fs-fuse/s3fs-fuse/wiki/Fuse-Over-Amazon
