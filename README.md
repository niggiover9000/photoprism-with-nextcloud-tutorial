# Photoprism with Nextcloud Tutorial
This is a tutorial on how to set up photoprism using the nextcloud photos folder. We will use photoprism in a docker container. Nextcloud can, but doesn't need to be set up in docker.

## Find your photos folder
You need to find the folder to which the photos are uploaded. In my case, thats _/etc/ncp/files/Photos/_

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
  -v _/etc/ncp/files/Photos/_:/photoprism/originals \
  photoprism/photoprism
  ```

Please change `PHOTOPRISM_ADMIN_PASSWORD` to something more secure!
