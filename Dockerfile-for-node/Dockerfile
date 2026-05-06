#==========Build stage==========


#base image for node project alpine--lightweight--naminf this stage as builder
FROM node:22-alpine AS builder

#setting working dir for the container
WORKDIR /app

#coping all the dependencies file to the containers working dir
COPY package*.json ./

#installing all the dependencies---using npm ci---strict, faster, used in ci/cd
RUN npm ci

#coping all the code from source to the container
COPY . .

#Build application
RUN npm run build


#===========Production stage==========

#new image for production alpine--lightweight--naminf this stage as builder
FROM node:22-alpine

#setting env to production so that the system knows its in production environment
ENV NODE_ENV=production

#
