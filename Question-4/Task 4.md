Create a Pod named `secured` that uses the image nginx. Mount an `emptyDir` volume to the directory `/data/app`

Files created on the volume should use the filesystem group ID `3000`

Shell into the running container and create a new file named `logs.txt` in the directory `/data/app` then list the contents of the directory and write them down.

