ARG PYTHON_TAG
FROM python:${PYTHON_TAG:-3.6.10-buster}

LABEL maintainer="Deltodon <web@deltodon.com>"

# download and install ESA SNAP 7.0
RUN wget http://step.esa.int/downloads/7.0/installers/esa-snap_sentinel_unix_7_0.sh \
      #change file execution rights for snap installer
      && chmod +x esa-snap_sentinel_unix_7_0.sh \ 
      # install snap with gpt
      && ./esa-snap_sentinel_unix_7_0.sh -q \
      # link gpt so it can be used systemwide
      && ln -s /usr/local/snap/bin/gpt /usr/bin/gpt \
      # set gpt max memory to 4GB
      && sed -i -e 's/-Xmx1G/-Xmx4G/g' /usr/local/snap/bin/gpt.vmoptions \
      # install snappy the SNAP python module
      && /usr/local/snap/bin/snappy-conf /usr/local/bin/python \
      && cd /root/.snap/snap-python/snappy/ \
      && python setup.py install \
      && ln -s /root/.snap/snap-python/snappy /usr/local/lib/python3.6/site-packages/snappy \
      # Clean up
      && rm /esa-snap_sentinel_unix_7_0.sh \
      && rm -rf /var/lib/apt/lists/*