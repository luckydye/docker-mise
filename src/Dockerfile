FROM debian:latest

RUN apt update -y && apt install curl rsync bash wget git -y

# install mise
RUN curl https://mise.run | MISE_INSTALL_PATH=/usr/local/bin/mise sh
ENV PATH=$PATH:/root/.local/share/mise/shims

# install project tools
COPY .mise.toml .mise.toml
RUN mise install -y && mise reshim
RUN pip install ansible && mise reshim

CMD ["/bin/bash"]
