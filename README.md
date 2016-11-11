**MaskDelete** is one tool, in order to delete some files in *folder_A*, with all files in *folder_B* as a MASK. All the files, which existing in *folder_A*, but not existing in *folder_B*, are to be deleted, according to the file name, but ignoring file suffix (e.g. JPG, txt, tar). 

**NOTE** that this is one tool to delete files, so make sure its functionality before using it.

# Status
To be completed.

# Motivation
The motivation why I write this tool is for photography. Nowadays, some of cameras can generate both JPG and RAW photos for one shot. JPG format is for preview, and RAW is for the final output. Thus, after exporting all the photos from camera to computer, I will make a simple process to get rid of unsuccessful photos:

1. Classification: Move JPG and RAW files to two different folders seperatedly, which can be realized by build-in search.
2. Preview and Filter: Preview all the photos in JPG folder, and delete all the unsuccessful photos when browsing. Space Preview of Mac OS is very convenient for this.
3. Execute mskdel: Use mskdel command (i.e. execute "*mskdel RAW_folder JPG_folder*") to delete all of RAW photos, which have been deleted from JPG folder. JPG folder is regarded as a MASK.
4. Other post processing.

One simple example is shown below:

| Original | Classfication | \*	        | Preview and Filter | \*         | Execute mskdel | \*          |
|:--------:|:-------------:|:----------:|:------------------:|:----------:|:--------------:|:-----------:|
| 1.JPG	   | JPG folder    | RAW folder | JPG folder         | RAW folder | JPG folder     | RAW folder  |
| 1.CR2	   | 1.JPG		     | 1.CR2      | 2.JPG	             | 1.CR2      | 2.JPG	         | 2.CR2       |
| 2.JPG	   | 2.JPG		     | 2.CR2      | 4.JPG	             | 4.CR2      | 4.JPG	         | 4.CR2       |
| 2.CR2	   | 3.JPG		     | 3.CR2      |      	             | 3.CR2      |      	         |             |
| 3.JPG	   | 4.JPG		     | 4.CR2      |     	             | 4.CR2      |                |             |
| 3.CR2	   |               |            |		                 |            |		             |             |
| 4.JPG	   |               |            |		                 |            |		             |             |
| 4.CR2	   |               |            |		                 |            |		             |             |

# Usage
Execute command:

```shell
$ mskdel folder1 folder2
```

Then, the files, which existing in folder1, but not in folder2, will be deleted from folder1, according to the file name, ignoring the file suffix. Two files which having the same name, except the suffix, are regarded as the same file. 
