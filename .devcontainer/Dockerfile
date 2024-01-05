# [Choice] Go version (use -bookworm, or -bullseye variants on local arm64/Apple Silicon): 1, 1.21, 1.20, 1-bookworm, 1.21-bookworm, 1.20-bookworm, 1-bullseye, 1.21-bullseye, 1.20-bullseye
ARG VARIANT=1.21
FROM golang:${VARIANT}

# # VARIANT can be either 'hugo' for the standard version or 'hugo_extended' for the extended version.
# ARG VARIANT=hugo_extended
# # VERSION can be either 'latest' or a specific version number
# ARG VERSION=latest

# Download Hugo
# RUN apk add --update --no-cache ca-certificates openssl git curl libc6-compat 
# && \
#   case ${VERSION} in \
#   latest) \
#   export VERSION=$(curl -s https://api.github.com/repos/gohugoio/hugo/releases/latest | grep "tag_name" | awk '{print substr($2, 3, length($2)-4)}') ;;\
#   esac && \
#   echo ${VERSION} && \
#   wget -O ${VERSION}.tar.gz https://github.com/gohugoio/hugo/releases/download/v${VERSION}/${VARIANT}_${VERSION}_Linux-64bit.tar.gz && \
#   tar xf ${VERSION}.tar.gz && \
#   mv hugo* /usr/bin/hugo && \
#   go get github.com/yaegashi/muslstack && \
#   muslstack -s 0x800000 /usr/bin/hugo
ENV CGO_ENABLED=1
RUN go install -tags extended github.com/gohugoio/hugo@latest
RUN hugo version

# [Optional] Uncomment the next line to use go get to install anything else you need
# RUN go get -x <your-dependency-or-tool>

# Hugo dev server port
EXPOSE 1313

# [Optional] Uncomment this section to install additional OS packages you may want.
#
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment if you want to install more global node packages
# RUN sudo -u node npm install -g <your-package-list-here>

# FROM mcr.microsoft.com/vscode/devcontainers/base
# COPY --from=0 /usr/bin/hugo /usr/bin
