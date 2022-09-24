# Pre-compiled binaries for [`raster-retrace`](https://crates.io/crates/raster-retrace)

## Platforms

### Linux

- raster-retrace-linux-x86_64
- raster-retrace-linux-arm64

### Mac

- raster-retrace-mac-x86_64

## Linux compilation instructions

### Docker containers

- Centos `public.ecr.aws/lambda/nodejs:16`
- Fedora `public.ecr.aws/amazonlinux/amazonlinux:2022`
- Ubuntu `ubuntu:jammy`

Compile for the oldest common denominator version of the kernel version via centos.

### Commands

#### Interactive

`docker run --platform linux/amd64 --entrypoint /bin/bash -it -v "$PWD":/var/task public.ecr.aws/lambda/nodejs:16`

`docker run --platform linux/arm64/v8 --entrypoint /bin/bash -it -v "$PWD":/var/task public.ecr.aws/lambda/nodejs:16`

#### Install

`yum install -y rust cargo`

`cargo install raster-retrace`

`mv /root/.cargo/bin/raster-retrace /var/task/raster-retrace`

(Mac is located in `~/.asdf/installs/rust/1.63.0/bin/raster-retrace`)

#### Testing

##### amd64

`docker run --platform linux/amd64 --entrypoint "/bin/bash" -v "$PWD:/var/task" --rm public.ecr.aws/lambda/nodejs:16 -c "cd /var/task && ./raster-retrace-linux-x86_64 -i demo.ppm -o demo.svg"`

`docker run --platform linux/amd64 --entrypoint "/bin/bash" -v "$PWD:/var/task" --rm public.ecr.aws/amazonlinux/amazonlinux:2022 -c "cd /var/task && ./raster-retrace-linux-x86_64 -i demo.ppm -o demo.svg"`

`docker run --platform linux/amd64 --entrypoint "/bin/bash" -v "$PWD:/var/task" --rm ubuntu -c "cd /var/task && ./raster-retrace-linux-x86_64 -i demo.ppm -o demo.svg"`

##### arm64

`docker run --platform linux/arm64/v8 --entrypoint "/bin/bash" -v "$PWD:/var/task" --rm public.ecr.aws/lambda/nodejs:16 -c "cd /var/task && ./raster-retrace-linux-arm64 -i demo.ppm -o demo.svg"`

`docker run --platform linux/arm64/v8 --entrypoint "/bin/bash" -v "$PWD:/var/task" --rm public.ecr.aws/amazonlinux/amazonlinux:2022 -c "cd /var/task && ./raster-retrace-linux-arm64 -i demo.ppm -o demo.svg"`

`docker run --platform linux/arm64/v8 --entrypoint "/bin/bash" -v "$PWD:/var/task" --rm ubuntu -c "cd /var/task && ./raster-retrace-linux-arm64 -i demo.ppm -o demo.svg"`
