FROM alpine:latest
#Build args
ARG VCS_REF
ARG BUILD_DATE
# Setting resource quota
ARG MIN_MEM=2G
ARG MAX_MEM=2G

RUN addgroup -S dockergroup && adduser -S dockeruser -G dockergroup
RUN  apk add --no-cache build-base gfortran &&  mkdir /src
#Adding Labels of build
LABEL maintainer="Gautham Prakash <github.com/gauthamp10>"
LABEL org.label-schema.build-date=$BUILD_DATE
LABEL org.label-schema.vcs-url="https://github.com/gauthamp10/dockerfile-boilerplates"
LABEL org.label-schema.vcs-ref=$VCS_REF

USER dockeruser
COPY src/main.f90 /src
WORKDIR /src
USER root
#Compiling source
RUN gfortran main.f90 -o main
USER dockeruser
#Execution
CMD ["./main"]