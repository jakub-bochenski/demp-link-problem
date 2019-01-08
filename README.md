
```
cd test
docker build .
mvn docker:build 
```


Output:
```
17:18:33 + cd test
17:18:33 + docker build .
17:18:33 Sending build context to Docker daemon  20.99kB

17:18:33 Step 1/2 : FROM ubuntu
17:18:34 latest: Pulling from library/ubuntu
17:18:35 84ed7d2f608f: Pulling fs layer
17:18:35 be2bf1c4a48d: Pulling fs layer
17:18:35 a5bdc6303093: Pulling fs layer
17:18:35 e9055237d68d: Pulling fs layer
17:18:35 e9055237d68d: Waiting
17:18:35 be2bf1c4a48d: Verifying Checksum
17:18:35 be2bf1c4a48d: Download complete
17:18:35 a5bdc6303093: Verifying Checksum
17:18:35 a5bdc6303093: Download complete
17:18:36 84ed7d2f608f: Verifying Checksum
17:18:36 84ed7d2f608f: Download complete
17:18:36 e9055237d68d: Download complete
17:18:37 84ed7d2f608f: Pull complete
17:18:37 be2bf1c4a48d: Pull complete
17:18:37 a5bdc6303093: Pull complete
17:18:37 e9055237d68d: Pull complete
17:18:37 Digest: sha256:868fd30a0e47b8d8ac485df174795b5e2fe8a6c8f056cc707b232d65b8a1ab68
17:18:37 Status: Downloaded newer image for ubuntu:latest
17:18:37  ---> 1d9c17228a9e
17:18:37 Step 2/2 : RUN echo "Proxy: $HTTP_PROXY !" && apt-get update
17:18:37  ---> Running in 10459979bf91
17:18:37 Proxy: http://proxy.eu-west-1.ele-df.fsapi.com:8080 !
17:18:37 Get:1 http://archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
17:18:37 Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
17:18:37 Get:3 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
17:18:37 Get:4 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
17:18:38 Get:5 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [186 kB]
17:18:38 Get:6 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1344 kB]
17:18:38 Get:7 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [301 kB]
17:18:38 Get:8 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [1367 B]
17:18:38 Get:9 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [135 kB]
17:18:38 Get:10 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [11.3 MB]
17:18:38 Get:11 http://archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [13.5 kB]
17:18:38 Get:12 http://archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [6931 B]
17:18:38 Get:13 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [622 kB]
17:18:38 Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [901 kB]
17:18:38 Get:15 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [10.7 kB]
17:18:38 Get:16 http://archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [3655 B]
17:18:39 Fetched 15.4 MB in 1s (10.9 MB/s)
17:18:39 Reading package lists...
17:18:40 Removing intermediate container 10459979bf91
17:18:40  ---> 6801a4f88257
17:18:40 Successfully built 6801a4f88257
17:18:45 using global settings config with name Default global settings
17:18:45 Replacing all maven server entries not found in credentials list is false
17:18:45 [docker-test] $ /srv/tools/hudson.tasks.Maven_MavenInstallation/3.5.4/apache-maven-3.5.4/bin/mvn -f test -gs /tmp/global-settings2657447748713367430.xml -B docker:build -Ddocker.verbose=true -Ddocker.showLogs=true
17:18:45 Picked up JAVA_TOOL_OPTIONS: -Djdk.net.URLClassPath.disableClassPathURLCheck=true
17:18:46 [INFO] Scanning for projects...
17:18:47 [INFO] 
17:18:47 [INFO] -----------< io.fabric8.dmp.samples:demp-sample-zero-config >-----------
17:18:47 [INFO] Building demp-sample-zero-config 0.27.2
17:18:47 [INFO] --------------------------------[ jar ]---------------------------------
17:18:47 [INFO] 
17:18:47 [INFO] --- docker-maven-plugin:0.27.2:build (default-cli) @ demp-sample-zero-config ---
17:19:08 [INFO] Building tar: /srv/workspace/docker-test/test/target/docker/samples/demp-sample-zero-config/0.27.2/tmp/docker-build.tar
17:19:08 [INFO] DOCKER> [samples/demp-sample-zero-config:0.27.2]: Created docker-build.tar in 21 milliseconds
17:19:08 [INFO] DOCKER> Step 1/2 : FROM ubuntu
17:19:08 [INFO] DOCKER> 
17:19:08 [INFO] DOCKER> ---> 1d9c17228a9e
17:19:08 [INFO] DOCKER> Step 2/2 : RUN echo "Proxy: $HTTP_PROXY !" && apt-get update
17:19:08 [INFO] DOCKER> 
17:19:08 [INFO] DOCKER> ---> Running in a1dc5cea0827
17:19:08 [INFO] DOCKER> Proxy:  !
17:19:40 [INFO] DOCKER> Err:1 http://archive.ubuntu.com/ubuntu bionic InRelease
17:19:40   Could not connect to archive.ubuntu.com:80 (91.189.88.161), connection timed out Could not connect to archive.ubuntu.com:80 (91.189.88.149), connection timed out Could not connect to archive.ubuntu.com:80 (91.189.88.152), connection timed out Could not connect to archive.ubuntu.com:80 (91.189.88.162), connection timed out
17:19:40 Err:2 http://archive.ubuntu.com/ubuntu bionic-updates InRelease
17:19:40   Unable to connect to archive.ubuntu.com:http:
17:19:40 Err:3 http://archive.ubuntu.com/ubuntu bionic-backports InRelease
17:19:40   Unable to connect to archive.ubuntu.com:http:
17:19:40 [INFO] DOCKER> Err:4 http://security.ubuntu.com/ubuntu bionic-security InRelease
17:19:40   Could not connect to security.ubuntu.com:80 (91.189.88.152), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.26), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.23), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.161), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.149), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.162), connection timed out
17:19:40 [INFO] DOCKER> Reading package lists...
17:19:40 [INFO] DOCKER> 
17:19:40 [INFO] DOCKER> [91mW: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic/InRelease  Could not connect to archive.ubuntu.com:80 (91.189.88.161), connection timed out Could not connect to archive.ubuntu.com:80 (91.189.88.149), connection timed out Could not connect to archive.ubuntu.com:80 (91.189.88.152), connection timed out Could not connect to archive.ubuntu.com:80 (91.189.88.162), connection timed out
17:19:40 W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease  Unable to connect to archive.ubuntu.com:http:
17:19:40 W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease  Unable to connect to archive.ubuntu.com:http:
17:19:40 W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease  Could not connect to security.ubuntu.com:80 (91.189.88.152), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.26), connection timed out Could not connect to security.ubuntu.com:80 (91.189.91.23), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.161), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.149), connection timed out Could not connect to security.ubuntu.com:80 (91.189.88.162), connection timed out
17:19:40 W: Some index files failed to download. They have been ignored, or old ones used instead.
17:19:40 
17:19:41 [INFO] DOCKER> Removing intermediate container a1dc5cea0827
17:19:41 [INFO] DOCKER> ---> 288935645330
17:19:41 [INFO] DOCKER> Successfully built 288935645330
17:19:41 [INFO] DOCKER> Successfully tagged samples/demp-sample-zero-config:0.27.2
17:19:41 [INFO] DOCKER> [samples/demp-sample-zero-config:0.27.2]: Built image sha256:28893
```

