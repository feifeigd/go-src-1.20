
ARG IMAGE=ubuntu:23.04
ARG ARCH=$(arch | sed s/aarch64/arm64/ | sed s/x86_64/amd64/)

FROM $IMAGE

LABEL author="feifeigd@21cn.com"

# USER root

# 替换源
RUN sed -i "s/archive.ubuntu.com/mirrors.163.com/g" /etc/apt/sources.list \
    && sed -i "s/security.ubuntu.com/mirrors.163.com/g" /etc/apt/sources.list

# 环境变量
ENV  \
    VCPKG_FORCE_SYSTEM_BINARIES=1   \
    PATH=/workspaces/go-src-1.20/go/bin:/go/bin:$PATH \
    GOROOT_BOOTSTRAP=/usr

# Install needed packages. Use a separate RUN statement to add your own dependencies.
# RUN apk add --no-cache \
#    clang libev-dev linux-headers lldb llvm cppcheck gdb valgrind

ARG USERNAME=vscode

# 安装jdk
# RUN apk add --no-cache openjdk11
# 安装 bazel
# RUN wget https://github.com/bazelbuild/bazel/releases/download/6.0.0/bazel-6.0.0-dist.zip && unzip bazel-6.0.0-dist.zip \
#   && env EXTRA_BAZEL_ARGS="--tool_java_runtime_version=local_jdk" bash ./compile.sh

# [Optional] Ucomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends cmake gccgo vim wget

RUN ARCH=$(arch | sed s/aarch64/arm64/ | sed s/x86_64/amd64/) && wget --no-check-certificate https://github.com/bazelbuild/bazelisk/releases/download/v1.15.0/bazelisk-linux-${ARCH} -O /bin/bazelisk && chmod +x /bin/bazelisk
# 安装 gccgo 用于编译go源码
# 从源码安装 go https://go.dev/doc/install/source
#RUN sudo ln -s /usr/bin/go-12 /usr/bin/go \
#    sudo update-alternatives --set go /usr/bin/go-12
# go install golang.org/x/tools/gopls@latest

# man-db
# RUN unminimize
RUN mkdir /go 
