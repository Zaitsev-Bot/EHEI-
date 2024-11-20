# Base Ubuntu image
FROM ubuntu:22.04

# Install Octave and necessary dependencies
RUN apt-get update && apt-get install -y \
    software-properties-common \
    && add-apt-repository ppa:octave/stable -y \
    && apt-get update && apt-get install -y octave \
    && apt-get clean

# Set environment for CLI mode
ENV DISPLAY=:0

# Verify Octave installation
RUN octave --version

