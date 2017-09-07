Example Dockerfile Python App
=============================

This sample application shows how you can deploy Dockerfile-based
Python applications to [Deis Workflow][].

## Usage

```console
$ git clone https://github.com/deisthree/example-dockerfile-python
$ cd example-dockerfile-python
$ deis create
Creating Application... done, created actual-gatepost
Git remote deis added
remote available at ssh://git@deis-builder.deis.rocks:2222/actual-gatepost.git
$ git push deis master
Counting objects: 63, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (61/61), done.
Writing objects: 100% (63/63), 10.81 KiB | 0 bytes/s, done.
Total 63 (delta 15), reused 0 (delta 0)
Starting build... but first, coffee!
Step 1 : FROM gliderlabs/alpine:3.4
---> 4ccfa836b1ef
Step 2 : RUN apk-install python
---> Running in 572ae393ecbd
fetch http://alpine.gliderlabs.com/alpine/v3.4/main/x86_64/APKINDEX.tar.gz
fetch http://alpine.gliderlabs.com/alpine/v3.4/community/x86_64/APKINDEX.tar.gz
(1/10) Installing libbz2 (1.0.6-r4)
(2/10) Installing expat (2.1.1-r0)
(3/10) Installing libffi (3.2.1-r2)
(4/10) Installing gdbm (1.11-r1)
(5/10) Installing ncurses-terminfo-base (6.0-r7)
(6/10) Installing ncurses-terminfo (6.0-r7)
(7/10) Installing ncurses-libs (6.0-r7)
(8/10) Installing readline (6.3.008-r4)
(9/10) Installing sqlite-libs (3.13.0-r0)
(10/10) Installing python (2.7.11-r3)
Executing busybox-1.24.2-r8.trigger
OK: 51 MiB in 21 packages
---> fbecd3fd8d74
Removing intermediate container 572ae393ecbd
Step 3 : ADD . /app
---> ce8ecbeddcc0
Removing intermediate container 5db31a5ffb53
Step 4 : WORKDIR /app
---> Running in adec7d5be4f0
---> a3359044cf9d
Removing intermediate container adec7d5be4f0
Step 5 : CMD python -m SimpleHTTPServer 5000
---> Running in 54f58e80e26c
---> 8d77fa1e8f6a
Removing intermediate container 54f58e80e26c
Step 6 : EXPOSE 5000
---> Running in c791be404095
---> e98493484c2f
Removing intermediate container c791be404095
Successfully built e98493484c2f
Pushing to registry
Build complete.
Launching App...
Done, actual-gatepost:v2 deployed to Deis

Use 'deis open' to view this application in your browser

To learn more, use 'deis help' or visit https://deis.com/

To ssh://git@deis-builder.deis.rocks:2222/actual-gatepost.git
 * [new branch]      master -> master

$ curl http://actual-gatepost.deis.rocks
<h1>Powered by Deis</h1>
```

## Additional Resources

* [GitHub Project](https://github.com/deisthree/workflow)
* [Documentation](https://deis.com/docs/workflow/)
* [Blog](https://deis.com/blog/)

[Deis Workflow]: https://github.com/deisthree/workflow#readme
