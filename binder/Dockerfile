FROM jupyter/base-notebook

# Install ICU library for .NET globalization support
USER root
RUN apt-get update && apt-get install -y libicu-dev
USER $NB_USER

# Install .NET SDK to jovyan's home directory
RUN wget https://dot.net/v1/dotnet-install.sh \
    && chmod +x dotnet-install.sh \
    && ./dotnet-install.sh -c 7.0 --install-dir /home/jovyan/.dotnet

ENV PATH="/home/jovyan/.dotnet:${PATH}"

# Install .NET Interactive as a global tool for jovyan
RUN /home/jovyan/.dotnet/dotnet tool install --global Microsoft.dotnet-interactive \
    && /home/jovyan/.dotnet/tools/dotnet-interactive jupyter install

ENV PATH="/home/jovyan/.dotnet/tools:${PATH}"

WORKDIR /home/jovyan
EXPOSE 8888