# Start from debian stretch-slim
FROM debian:stretch-slim

# Setup JAVA_HOME
ENV JAVA_HOME="/usr/lib/jvm/default-jvm"

# Install Oracle JRE (Java SE Runtime Environment) 8u192 with Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files for JDK/JRE 8
RUN JAVA_VERSION=8 && \
    JAVA_UPDATE=192 && \
    JAVA_BUILD=12 && \
    JAVA_PATH=750e1c8617c5452694857ad95c3ee230 && \
    JAVA_SHA256_SUM=f23a3e2b9decef82b74f850157580d929ab35e9f19be5e0a10c779b68be51d43 && \
    JCE_SHA256_SUM=f3020a3922efd6626c2fff45695d527f34a8020e938a49292561f18ad1320b59 && \ 
    apt-get update && \
    apt-get -y install wget unzip && \
    cd "/tmp" && \
    wget --header "Cookie: oraclelicense=accept-securebackup-cookie;" "http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION}u${JAVA_UPDATE}-b${JAVA_BUILD}/${JAVA_PATH}/jre-${JAVA_VERSION}u${JAVA_UPDATE}-linux-x64.tar.gz" && \
    echo "${JAVA_SHA256_SUM}" "jre-${JAVA_VERSION}u${JAVA_UPDATE}-linux-x64.tar.gz" | sha256sum -c - && \
    wget --header "Cookie: oraclelicense=accept-securebackup-cookie;" "http://download.oracle.com/otn-pub/java/jce/${JAVA_VERSION}/jce_policy-${JAVA_VERSION}.zip" && \
    echo "${JCE_SHA256_SUM}" "jce_policy-${JAVA_VERSION}.zip" | sha256sum -c - && \
    tar -xzf "jre-${JAVA_VERSION}u${JAVA_UPDATE}-linux-x64.tar.gz" && \
    mkdir -p "/usr/lib/jvm" && \
    mv "/tmp/jre1.${JAVA_VERSION}.0_${JAVA_UPDATE}" "/usr/lib/jvm/java-${JAVA_VERSION}-oracle" && \
    ln -s "java-${JAVA_VERSION}-oracle" "$JAVA_HOME" && \
    ln -s "$JAVA_HOME/bin/"* "/usr/bin/" && \
    unzip -jo -d "$JAVA_HOME/lib/security" "jce_policy-${JAVA_VERSION}.zip" && \    
    rm -rf "$JAVA_HOME/plugin" \    
           "$JAVA_HOME/bin/javaws" \
           "$JAVA_HOME/bin/jjs" \
           "$JAVA_HOME/bin/keytool" \
           "$JAVA_HOME/bin/orbd" \
           "$JAVA_HOME/bin/pack200" \
           "$JAVA_HOME/bin/policytool" \
           "$JAVA_HOME/bin/rmid" \
           "$JAVA_HOME/bin/rmiregistry" \
           "$JAVA_HOME/bin/servertool" \
           "$JAVA_HOME/bin/tnameserv" \
           "$JAVA_HOME/bin/unpack200" \           
           "$JAVA_HOME/lib/"*javafx* \
           "$JAVA_HOME/lib/plugin.jar" \
           "$JAVA_HOME/lib/ext/jfxrt.jar" \
           "$JAVA_HOME/lib/javaws.jar" \
           "$JAVA_HOME/lib/desktop" \
           "$JAVA_HOME/lib/"deploy* \
           "$JAVA_HOME/lib/"*javafx* \
           "$JAVA_HOME/lib/"*jfx* \
           "$JAVA_HOME/lib/amd64/libdecora_sse.so" \
           "$JAVA_HOME/lib/amd64/"libprism_*.so \
           "$JAVA_HOME/lib/amd64/libfxplugins.so" \
           "$JAVA_HOME/lib/amd64/libglass.so" \
           "$JAVA_HOME/lib/amd64/libgstreamer-lite.so" \
           "$JAVA_HOME/lib/amd64/"libjavafx*.so \
           "$JAVA_HOME/lib/amd64/"libjfx*.so \
           "$JAVA_HOME/lib/ext/nashorn.jar" \
           "$JAVA_HOME/lib/jfr.jar" \
           "$JAVA_HOME/lib/jfr" \
           "$JAVA_HOME/lib/oblique-fonts" \           
           "$JAVA_HOME/THIRDPARTYLICENSEREADME-JAVAFX.txt" \
           "$JAVA_HOME/THIRDPARTYLICENSEREADME.txt" \            
           "$JAVA_HOME/README" \
           "$JAVA_HOME/Welcome.html" \
           "$JAVA_HOME/lib/security/README.txt" && \           
    apt-get -y autoremove wget unzip && \
    apt-get -y clean && \
    rm -rf "/tmp/"* \
           "/var/cache/apt" \
           "/usr/share/man" \
           "/usr/share/doc" \
           "/usr/share/doc-base" \
           "/usr/share/info/*"