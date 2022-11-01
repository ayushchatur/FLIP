# Table of Contents
1. [Overview](#overview)
2. [Pre-Requisites](#pre-requisites)
3. [Step-by-Step Guide](#step-by-step-guide)
    2. [Docker Compose](#docker-compose)
    3. [Using the Data](#using-the-data)

# Overview
This document covers the OMOP Database Emulator and how to get it installed on your local environment.

# Pre-Requisites
You will need

- Docker
- psql (or a DB  Client of your choosing)

# Step-by-Step Guide

## Login to GitHub Repository

See:
https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry

The above guide comprehensively covers what you need to do to log in to the GHCR docker repository in order to #
download the required OMOP image.

## Docker Compose

The following docker-compose file can be used to create a running container, containing the

- OMOP Schema
- OMOP Vocabularies
- OMOP Concepts
- UAT Dress Rehearsal Data

Copy the below in a file called docker-compose.yml

```dockercompose
version: "3.8"
services:
omop:
    image: "ghcr.io/answerconsulting/loaded_omop:latest"
    ports:
      - "5432:5432"
    environment:
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
    volumes:  
      - ./data:/var/lib/postgresql/data

```
Then to start the container from where docker-compose.yml was copied to:

```shell
docker compose up
```

## Using the Data

You can use the psql command to access the database (or any IDE of your choosing)

```shell
psql -h locahost -U postgres
```

You will then be prompted for a password which is "postgres", for the OMOP UAT dataset
the following tables are populated accessible with the queries below

The _Person_ table

```sql
SELECT * FROM omop.person;
```

The _Radiology_Occurrence_ Table

```sql
SELECT * FROM omop.radiology_occurrence;
```

