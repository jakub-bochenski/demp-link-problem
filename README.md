
```
cd test && \
ln -s $(pwd)/file absolute.link && \
ln -s file relative.link && \
ln -s /foo/bar broken.link && \
docker build --tag demp-link-problem . && \
docker run --rm demp-link-problem && \
mvn docker:build docker:run
```


Output:
```
$ cd test && ln -s $(pwd)/file absolute.link && ln -s file relative.link && ln -s /foo/bar broken.link && docker build --tag demp-link-problem . && docker run --rm demp-link-problem && mvn docker:build docker:run
Sending build context to Docker daemon  8.704kB
Step 1/4 : FROM busybox
 ---> 59788edf1f3e
Step 2/4 : COPY . /build-context
 ---> Using cache
 ---> 4abf27a23231
Step 3/4 : WORKDIR /build-context
 ---> Using cache
 ---> e4789fc4a7db
Step 4/4 : CMD ls -la
 ---> Using cache
 ---> 2d64af84bafe
Successfully built 2d64af84bafe
Successfully tagged demp-link-problem:latest
total 20
drwxr-xr-x    3 root     root          4096 Nov 15 09:46 .
drwxr-xr-x    1 root     root          4096 Nov 15 09:47 ..
-rw-rw-r--    1 root     root            69 Nov 14 14:55 Dockerfile
lrwxrwxrwx    1 root     root            35 Nov 15 09:46 absolute.link -> /home/bochja/tmp/linktest/test/file
lrwxrwxrwx    1 root     root             8 Nov 15 09:46 broken.link -> /foo/bar
-rw-rw-r--    1 root     root             0 Nov 14 14:06 file
-rw-rw-r--    1 root     root           944 Nov 14 14:50 pom.xml
lrwxrwxrwx    1 root     root             4 Nov 15 09:46 relative.link -> file
drwxrwxr-x    3 root     root          4096 Nov 14 14:55 target
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------------------------------------------------------------------
[INFO] Building demp-sample-zero-config 0.27.2
[INFO] ------------------------------------------------------------------------
[INFO] 
[INFO] --- docker-maven-plugin:0.27.2:build (default-cli) @ demp-sample-zero-config ---
[INFO] Building tar: /home/bochja/tmp/linktest/test/target/docker/samples/demp-sample-zero-config/0.27.2/tmp/docker-build.tar
[INFO] DOCKER> [samples/demp-sample-zero-config:0.27.2]: Created docker-build.tar in 33 milliseconds
[INFO] DOCKER> [samples/demp-sample-zero-config:0.27.2]: Built image sha256:0989a
[INFO] 
[INFO] --- docker-maven-plugin:0.27.2:run (default-cli) @ demp-sample-zero-config ---
[INFO] DOCKER> [samples/demp-sample-zero-config:0.27.2]: Start container dad2b920efe4
dad2b9> total 20
dad2b9> drwxr-xr-x    3 root     root          4096 Nov 14 14:55 .
dad2b9> drwxr-xr-x    1 root     root          4096 Nov 15 09:47 ..
dad2b9> -rw-rw-r--    1 root     root            69 Nov 14 14:55 Dockerfile
dad2b9> lrwxrwxrwx    1 root     root            30 Nov 14 14:06 absolute.link -> /home/bochja/tmp/linktest/file
dad2b9> -rw-rw-r--    1 root     root             0 Nov 14 14:06 file
dad2b9> -rw-rw-r--    1 root     root           944 Nov 14 14:50 pom.xml
dad2b9> lrwxrwxrwx    1 root     root             4 Nov 14 14:06 relative.link -> file
dad2b9> drwxrwxr-x    2 root     root          4096 Nov 14 14:55 target
^C[INFO] DOCKER> [samples/demp-sample-zero-config:0.27.2]: Stop and removed container dad2b920efe4 after 0 ms
```

