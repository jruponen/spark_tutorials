##How to upload files greater than 200MB to the Object Storage in Bluemix?

Web browser UI to the Object Storage has maximum upload file size limit of 200MB.
To upload larger files, you can use either
1) Swift client
2) File transfer utility supporting Swift (e.g Cyberduck)
3) Swift REST API.


###ALTERNATIVE 1: SWIFT CLIENT
On below are simple instructions how to set up and use the Swift client.

**1: Install Swift client on the computer you'll need to upload large files from**  
Instructions for all operating systems:
https://swiftstack.com/docs/integration/python-swiftclient.html

**2: Create a script to initialize environment variables with your Swift credentials**  
Swift client can read the necessary authentication information from environment variables.
It is easiest to use a shell script (Mac/Linux) or batch file (Windows) to set these environment variables when needed.
Just copy/paste the Mac/Linux shell script example from below and modify to your needs:

```
#!/bin/bash
########################################################################
## Script name: bluemix_swift.sh                                      ##
## Author: Jukka Ruponen, IBM, 2016-04-13                             ##
## Usage:                                                             ##
## 1. Install python-swift client from:                               ##
##    https://swiftstack.com/docs/integration/python-swiftclient.html ##
## 2. Modify this script according to your Object Store credentials   ##
##    Hint: Use "Insert to code" from Data Source panel on your Spark ##
##    Notebook to find out your credentials.                          ##
## 3. Execute this script as profile to set the environment variables ##
##    $ source ./bluemix_swift.sh                                     ##
## 4. Use Swift command line for operations, e.g:                     ##
##    $ swift list --lh <dest_folder>                                 ##
##    $ swift upload <dest_folder> <local_file_to_upload>             ##
## For Swift command line help, use: swift --help                     ##
########################################################################

## Swift auth_url, added with API version "/v3" (do not change):
export OS_AUTH_URL=https://identity.open.softlayer.com/v3

## Swift project_id (change to your credentials):
export OS_PROJECT_ID=0d742b7e4584410a9378f60f6eb34514

## Swift region:
export OS_REGION_NAME=dallas

## Swift user_id:
export OS_USER_ID=c1a2e99676e34d4b8952c7bb8ffc05f2

## Swift password:
export OS_PASSWORD=PLA-[=w5pWgt}98!

## Swift identity API version (do not change):
export OS_IDENTITY_API_VERSION=3

## Swift authentication method version (do not change):
export OS_AUTH_VERSION=3
```

Save and close the file.
Remember to change file permissions to allow execution:
```
$ chmod 755 ./bluemix_swift.sh
```

**3: Using Swift client**  
Use the script above first to initialize environment variables for the Swift client:
```
$ source bluemix_swift.sh
```

Now you can use this command to show contents of your Object Store root folder
```
$ swift list
notebooks
test
```

Use this command to show contents of "notebooks" folder, with file sizes
```
$ swift list --lh notebooks
1.1G 2016-03-29 00:36:06 text/csv 2015.csv
 398 2016-03-30 22:09:32 text/csv NYC_taxi_passenger_tips.csv
```

Use this command to upload a local file <filename> to the "notebooks" folder
```
$ swift upload notebooks <filename>
```

###ALTERNATIVE 2: CYBERDUCK

Cyberduck is a file transfer client for Mac OS X and Windows that supports many protocols and methods, including SFTP, SCP, WebDav, S3, Swift etc.  
The following instructions are for Mac OS X. 

**1: Install Cyberduck**  
https://cyberduck.io

If you have Cyberduck installed already, make sure it's updated to the latest version.

**2: Download & open Swift Keystone 3.0 profile on Cyberduck**  

Bluemix Swift uses Keystone v3 authentication tokens but out of the box support in Cyberduck is for Keystone v1.

Therefore, you'll need to download the following Cyberduck Keystone v3 profile and open it in Cyberduck:
https://svn.cyberduck.ch/trunk/profiles/Openstack%20Swift%20(Keystone%203).cyberduckprofile

If interested, more information here: https://trac.cyberduck.io/wiki/help/en/howto/openstack

**3: Connectivity parameters**  

If not displayed already, press "Open Connection" in Cyberduck and select "Openstack Swift (Keystone 3)".
Here's the connection values you'll need to fill in:
```
Server:		identity.open.softlayer.com
Port:			443
Username:	<project>:<username>
 example:	object_storage_317aecfe:user_c2eba4f4ce7406226c4d5da9b9a7e49f20eef7a1
Password:	<password>
 example:	PLAA[!w4pXgT}89!
Path:			<target path>
 example:	/

Additional login credentials:
Project domain name:	<domain_name>
 example:					791473
```
**Hint:** Use "Insert to code" from Data Source panel on your Spark Notebook to find out your Swift object store credentials.


