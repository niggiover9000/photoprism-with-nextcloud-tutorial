# Photoprism with Nextcloud Tutorial
This is a tutorial on how to set up photoprism using the nextcloud photos folder. We will use photoprism in a docker container. Nextcloud can, but doesn't need to be set up in docker.

# Install Photoprism
```
docker run -d \
  --name photoprism \
  --security-opt seccomp=unconfined \
  --security-opt apparmor=unconfined \
  -p 2342:2342 \
  -e PHOTOPRISM_UPLOAD_NSFW="true" \
  -e PHOTOPRISM_ADMIN_PASSWORD="insecure" \
  -v /photoprism/storage \
  -v ~/Pictures:/photoprism/originals \
  photoprism/photoprism
  ```
