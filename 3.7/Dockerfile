FROM ghcr.io/martinluttap/bio-ubuntu:1.0.0

LABEL version="nightly-2016-02-25-gf39d340"
LABEL description="GATK3 nightly-2016-02-25-gf39d340"

RUN apt-get update -y \
    && apt-get install -y \
    openjdk-8-jre-headless

COPY GenomeAnalysisTK.jar /usr/local/bin

RUN ln -s /usr/local/bin/GenomeAnalysisTK.jar /usr/local/bin/gatk.jar

ENTRYPOINT ["java", "-jar", "/usr/local/bin/gatk.jar"]

CMD ["--help"]
