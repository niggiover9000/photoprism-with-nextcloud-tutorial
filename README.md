# Photoprism with Nextcloud Tutorial
This is a tutorial on how to set up photoprism using the nextcloud photos folder. We will use photoprism in a docker container. Nextcloud can, but doesn't need to be set up in docker.

## Find your photos folder
You need to find the folder to which the photos are uploaded. In my case, thats **"/etc/ncp/files/Photos/"**

## Install Photoprism
You will need to map the path of your photos to your photoprism container:
```
sudo docker run -d \
  --name photoprism \
  --security-opt seccomp=unconfined \
  --security-opt apparmor=unconfined \
  -p 2342:2342 \
  -e PHOTOPRISM_UPLOAD_NSFW="true" \
  -e PHOTOPRISM_ADMIN_PASSWORD="password" \
  -v /photoprism/storage \
  -v **/etc/ncp/files/Photos/**:/photoprism/originals \
  photoprism/photoprism
  ```
Please change `PHOTOPRISM_ADMIN_PASSWORD` to something more secure!

In the photoprism web interface (`localhost:2342`) navigate to _library_ and start to index. This will take a while depending on your photo library.

## Questions?
Leave them [here](https://github.com/niggiover9000/photoprism-with-nextcloud-tutorial/issues)

## Suggestions?
suggestions for improvement of this tutorial? Please make a pull request.
