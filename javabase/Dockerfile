FROM jeanblanchard/java:8
MAINTAINER Ian McEwen <mian@iplantcollaborative.org>
ARG git_commit=unknown
LABEL org.iplantc.de.javabase.git-ref="$git_commit"

RUN apk add --update curl \
    && mkdir -p /tmp/jce \
    && curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" -o /tmp/jce/jce.zip http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip \
    && unzip -d /tmp/jce -o /tmp/jce/jce.zip \
    && cp /tmp/jce/UnlimitedJCEPolicyJDK8/*.jar /opt/jdk/jre/lib/security/ \
    && rm -rf /tmp/jce \
    && apk del curl \
    && rm -rf /var/cache/apk/*

RUN mkdir -p /logs/ /bin/
WORKDIR /
EXPOSE 60000

