#docker #dockerfile #docker_layers
Слои формируются командами
 * `FROM`
 * `RUN`
 * `COPY`
 * `ADD`

For the `ADD` and `COPY` instructions, the contents of the file(s) in the image are examined and a checksum is calculated for each file. The last-modified and last-accessed times of the file(s) are not considered in these checksums. During the cache lookup, the checksum is compared against the checksum in the existing images. If anything has changed in the file(s), such as the contents and metadata, then the cache is invalidated.
https://docs.docker.com/develop/develop-images/dockerfile_best-practices/