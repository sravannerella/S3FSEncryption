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
https://github.com/sravannerella/S3FSEncryption/archive/master.zip

After downloading the code, extract the files to a folder.
Open a terminal and browse to the extracted folder and type ./configure.
This will check for the packages for the running the S3FS.
Once the configure is succeeded, run: sudo make.
Then run: sudo make install.
This will start compiling the code. If everything goes as expected, a executable will be created inside the src directory.

After that find key.txt file in the folder and move it to /home/your_pc_name/key.txt.
Now open fdcache.cpp file and go to Cryption::getkey function and change the "/home/sravan/key.txt" to "/home/your_pc_name/key.txt".

How To Use:
-----------
First create a Amazon S3 account, then name your bucket and then be sure to get yout Access Key and Secret Key from the Security Credentials.

Create a directory inside the mnt folder using root access. Command: "sudo mkdir -p /mnt/s3/"

Then execute following command in your terminal: "Path_to_your_src_folder/s3fs yourBucketName /mnt/s3 -o allow_other"

After that, press "df" command to make sure your s3 bucket is mounted.

Now you can browse to your bucket by typing cd /mnt/s3. You can also view all the files in your S3 using "ls -l /mnt/s3".

After that you can create files in the bucket using your text editors. After you press save, the file will be uploaded to S3FS and it will be encrypted. To view your file again, type cat filename.fileextension or move the file to your local directory.
