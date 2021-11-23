# files-management module

The files-management module implements the creation / rights management of folders, symlinks and files as well as emptying a directory or changing the rights of files.
The execution order is : 
 - directories
 - symlinks
 - files
 - rights
 - empty_directories
 - delete_files

# Variables:

## directories

Each directory described in this array will be created if it does not exist already. Specified rights will be applied on the directory, and - if *recurse* is set to yes - to all the subdirectories/files

One directory is represented by the following object :
```
{
  path: FULL_PATH_OF_DIRECTORY_TO_CREATE, // Mandatory
  mode: OCTAL_MODE_FOR_THE_DIRECTORY, // Optional, default: 0755
  owner: USER_OWNER_OF_THE_DIRECTORY, // Optional, default: root
  group: GROUP_OWNER_OF_THE_DIRECTORY, // Optional, default: root
  recurse: APPLY_RECURSIVELY // Optional, default: no
}
```
## symlinks

Each symlinks described in this array will be created with the specified option. If *force* is set to yes then it first delete *dst* before creating the link and will not check if *src* exist.

One symlink is represented by the following object:
```
{
  src: FULL_PATH_OF_THE_SOURCE_OF_THE_LINK_TO_CREATE, // Mandatory
  dst: FULL_PATH_OF_THE_DESTINATION_OF_THE_LINK_TO_CREATE, // Mandatory
  mode: OCTAL_MODE_FOR_THE_LINK, // Optional, default: 0755
  owner: USER_OWNER_OF_THE_LINK, // Optional, default: root
  group: GROUP_OWNER_OF_THE_LINK, // Optional, default: root
  force: FORCE_CREATION_OF_LINK // Optional, default: no
}
```
## files

Each files describe in this array will be created if it does not exist and apply the correct rights if it exists

One file is represented by the following object:
```
{
  path: FULL_PATH_OF_FILE_TO_CREATE, // Mandatory
  mode: OCTAL_MODE_FOR_THE_FILE, // Optional, default: 0755
  owner: USER_OWNER_OF_THE_FILE, // Optional, default: root
  group: GROUP_OWNER_OF_THE_FILE // Optional, default: root
}
```
## rights

Each files described in this array will have the specified apply to it but no file will be created if they do not exist

One file is represented by the following object:
```
{
  path: FULL_PATH_OF_FILE_TO_MODIFY, // Mandatory
  mode: OCTAL_MODE_FOR_THE_FILE, // Mandatory
  owner: USER_OWNER_OF_THE_FILE, // Optional, default: root
  group: GROUP_OWNER_OF_THE_FILE // Optional, default: root
  recurse: APPLY_RECURSIVELY // Optional, default: no
}
```
## empty_directories

All files and directories contained in directories specified in this array will be deleted.

One directory is represented by the following object :
```
{
  path: FULL_PATH_OF_DIRECTORY_TO_EMPTY, // Mandatory
}
```
## delete_files

All files or directories specified in this array will be deleted.

One directory is represented by the following object :
```
{
  path: FULL_PATH_OF_DIRECTORY_OR_FILE_TO_DELETE, // Mandatory
}
```
