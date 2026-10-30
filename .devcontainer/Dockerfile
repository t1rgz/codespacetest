FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

ARG ANDROID_API=35
ARG ANDROID_BUILD_TOOLS=35.0.0
ARG ANDROID_CMDLINE_TOOLS_VERSION=13114758

ENV ANDROID_HOME=/opt/android-sdk
ENV ANDROID_SDK_ROOT=${ANDROID_HOME}
ENV PATH=${ANDROID_HOME}/cmdline-tools/latest/bin:${ANDROID_HOME}/platform-tools:${PATH}

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        openjdk-17-jdk-headless \
        unzip \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p "${ANDROID_HOME}/cmdline-tools" \
    && curl -fsSL "https://dl.google.com/android/repository/commandlinetools-linux-${ANDROID_CMDLINE_TOOLS_VERSION}_latest.zip" -o /tmp/android-commandline-tools.zip \
    && unzip -q /tmp/android-commandline-tools.zip -d /tmp/android-commandline-tools \
    && mv /tmp/android-commandline-tools/cmdline-tools "${ANDROID_HOME}/cmdline-tools/latest" \
    && rm -rf /tmp/android-commandline-tools /tmp/android-commandline-tools.zip \
    && yes | sdkmanager --licenses >/dev/null \
    && sdkmanager "platform-tools" "platforms;android-${ANDROID_API}" "build-tools;${ANDROID_BUILD_TOOLS}" \
    && chown -R vscode:vscode "${ANDROID_HOME}"