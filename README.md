# nginx based proxy for s3 - docker

Serve your static homepage from S3 while keeping the bucket private by proxying
it through nginx - running in docker.

# Usage

Clone this repo:

    git clone --recursive https://github.com/tinnet/docker-nginx-s3proxy.git

Build image:

    cd docker-nginx-s3proxy
    docker build -t nginx-s3proxy .


Run a container from that image:

    docker run \
    -e S3PROXY_BUCKET_NAME="<S3_BUCKET_NAME>" \
    -e S3PROXY_AWS_ACCESS_KEY="<AWS_ACCESS_KEY>" \
    -e S3PROXY_AWS_SECRET_KEY="<AWS_SECRET_KEY>" \
    -p 10080:80 \
    -d nginx-s3proxy

# Known issues

* OSX users: watch out for boot2docker's clock going bad, run this to fix:

      boot2docker ssh sudo ntpclient -s -h pool.ntp.org

# Credit where credit is due

Based on:
* [https://registry.hub.docker.com/_/debian/](https://registry.hub.docker.com/_/debian/)
* [(http://nginx.org/](http://nginx.org/)
* [https://github.com/anomalizer/ngx_aws_auth](https://github.com/anomalizer/ngx_aws_auth)
* [https://github.com/kreuzwerker/envplate](https://github.com/kreuzwerker/envplate)
