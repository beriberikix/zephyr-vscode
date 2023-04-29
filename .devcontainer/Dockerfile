FROM ghcr.io/beriberikix/zephyr-arm:v3.3.0-0.16.0sdk

ARG ZEPHYR_SDK_VERSION=0.16.0
ARG ZEPHYR_SDK_INSTALL_DIR=/opt/zephyr

RUN \
  export sdk_file_name="zephyr-sdk-${ZEPHYR_SDK_VERSION}_linux-$(uname -m)_minimal.tar.xz" \
  && apt-get -y update \
  && apt-get -y install --no-install-recommends \
  wget \
  xz-utils \
  && wget -q "https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v${ZEPHYR_SDK_VERSION}/${sdk_file_name}" \
  && mkdir -p ${ZEPHYR_SDK_INSTALL_DIR} \
  && ${ZEPHYR_SDK_INSTALL_DIR}/setup.sh -h \
  && tar -xvf ${sdk_file_name} -C ${ZEPHYR_SDK_INSTALL_DIR} --strip-components=1 \
  && rm ${sdk_file_name} \
  && apt-get remove -y --purge \
  wget \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*