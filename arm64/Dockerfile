FROM python:3.9

ENV TZ=America/Chicago \
    DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y curl unzip less vim jq groff iputils-ping
RUN python3 -m pip install --upgrade pip ansible kubernetes
# Install kubectl
RUN curl -o kubectl https://s3.us-west-2.amazonaws.com/amazon-eks/1.22.6/2022-03-09/bin/linux/arm64/kubectl
RUN chmod 755 ./kubectl
RUN cp ./kubectl /bin/kubectl
# Install eksctl
RUN curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
RUN mv /tmp/eksctl /usr/local/bin
# Install awscli
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip" -o "awscliv2.zip"
RUN unzip awscliv2.zip
RUN ./aws/install
WORKDIR /root/
