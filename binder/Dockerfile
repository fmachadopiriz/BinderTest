FROM jupyter/base-notebook

# Install .NET SDK
# RUN wget https://dot.net/v1/dotnet-install.sh \
#     && chmod +x dotnet-install.sh \
#     && ./dotnet-install.sh -c 8.0 \
#     && ln -s /root/.dotnet/dotnet /usr/local/bin/dotnet

RUN wget https://dot.net/v1/dotnet-install.sh \
    && chmod +x dotnet-install.sh \
    && ./dotnet-install.sh -c 8.0

ENV PATH="/home/jovyan/.dotnet:${PATH}"

# Set up environment so dotnet is on PATH
# ENV PATH="/root/.dotnet:${PATH}"

# Install .NET Interactive
RUN dotnet tool install --global Microsoft.dotnet-interactive \
    && dotnet interactive jupyter install

# (Optional) Copy your postBuild script if you still need it
# COPY postBuild /tmp/postBuild
# RUN chmod +x /tmp/postBuild && /tmp/postBuild
