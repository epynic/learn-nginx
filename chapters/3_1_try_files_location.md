# try_files syntax

try_files can be used in either in server context or location context.

````
try_files /thumb.png /test;
````

This would look for files thumb.png if not found looks into /test location block.