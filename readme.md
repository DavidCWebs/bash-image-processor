Image Crunch
============
A very simple Bash script that runs an Imagemagick command.

Operates recursively on files and subdirectories in the target directory.

Builds a target directory containing processed files, with the same directory structure as the original.

Uses [Imagemagick](http://www.imagemagick.org/script/index.php).

Instructions
------------

* Add this file to a directory in your shell(Bash) path
* Make it executable (`sudo chmod +x /usr/local/bin/image-crunch`)
* In your terminal, move into the images directory
* Enter `image-crunch`
* Select a width when prompted
* Select compression or not
* Select a name for the new directory

The script copies all files and subdirectories into the newly specified subdirectory.

It then applies an Imagemagick command to all files in this directory:

```bash
if [ true == $compression ]
then
  # Imagemagick command on all files, recursive, with compression
  find ./ -name "*.jpg" -exec mogrify -resize $image_width -density 72 -quality "70%" {} \;
else
  # Imagemagick command on all files, recursive, No compression
  find ./ -name "*.jpg" -exec mogrify -resize $image_width -density 72 {} \;
fi
```
