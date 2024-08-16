FROM ghcr.io/martinluttap/bio-ubuntu:1.0.0 as builder

ENV VERSION=4.2.4.1

ENV URL=https://github.com/broadinstitute/gatk/releases/download/${VERSION}/gatk-${VERSION}.zip

RUN apt-get update \
	&& apt-get install -y \
		unzip \
		openjdk-8-jre \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/*

RUN wget $URL \
	&& unzip gatk-${VERSION}.zip \
	&& mv gatk-${VERSION}/* /usr/local/bin/ \
	&& rm -rf gatk-* \
	&& ln -s /usr/local/bin/gatk-package-${VERSION}-local.jar /usr/local/bin/gatk.jar \
	&& apt-get purge -y \
		unzip \
	&& ls -l /usr/local/bin
