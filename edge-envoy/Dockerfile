#FROM lyft/envoy:latest
#FROM dwflynn/envoy-debug:20170501
FROM envoyproxy/envoy-dev:59b7e037a8702e1b5da477f1ec5f98138d8723cf

RUN apt-get update && apt-get -q install -y \
    curl \
    dnsutils
    
COPY envoy.yaml /etc/envoy/envoy.yaml    
