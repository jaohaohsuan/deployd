# Dockerizing MongoDB: Dockerfile for building MongoDB images
# Based on ubuntu:latest, installs MongoDB following the instructions from:
# http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/

# Format: FROM    repository[:version]
FROM ubuntu:14.04

# Format: MAINTAINER Name <email@addr.ess>
MAINTAINER Henry Jao jaohaohsuan@gmail.com

# Installation:
# Import MongoDB public GPG key AND create a MongoDB list file
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
RUN echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.0.list

# Update apt-get sources AND install MongoDB
#ENV MONGODB_VERSION 3.2.1
RUN apt-get update && apt-get install -y mongodb-org
# Tip: You can install a specific version of MongoDB by using a list of required packages with versions, e.g.:
#RUN apt-get update && apt-get install -y \
#	mongodb-org=MONGODB_VERSION \
#	mongodb-org-server=MONGODB_VERSION \
#	mongodb-org-shell=MONGODB_VERSION \
#	mongodb-org-mongos=MONGODB_VERSION \
#	mongodb-org-tools=MONGODB_VERSION

# Create the MongoDB data directory
RUN mkdir -p /data/db

# Expose port 27017 from the container to the host
EXPOSE 27017

# Set usr/bin/mongod as the dockerized entry-point application
ENTRYPOINT ["/usr/bin/mongod"]
