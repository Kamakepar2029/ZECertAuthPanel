# README

## Introduction
This repository contains a bash script `startup.sh` and a Dockerfile to create a Docker image that runs the script. The script sets up a website SSL Certificate Authority (CA) and a personal SSL CA and starts a sample PHP server. 

## Prerequisites
You need to have the following software installed on your machine before you can use the bash script:
- OpenSSL 
- Bash shell

## Usage

### Running the bash script

To run the bash script, execute the following command in the terminal:
```bash
./startup.sh
```


#### Options
- `./startup.sh skipone`: Skips the setup of the website SSL CA.
- `./startup.sh skipsecond`: Skips the setup of the personal SSL CA.

The script will prompt you for the following information:
- Serial number for both the website SSL CA and the personal SSL CA. The serial number must be a number from 0 to 1000.
- OpenSSL configuration details:
    - Country Name (2 letter code)
    - State or Province Name (full name)
    - Locality Name
    - Organization Name (e.g., company)
    - Organizational Unit Name (e.g., section)
    - Email Address

The script will create the following directories:
- `ssl/`: Contains the files for the website SSL CA.
    - `crl/`: Contains Certificate Revocation Lists (CRLs) for the CA.
    - `crt/`: Contains the issued certificates for the website SSL CA.
    - `csr/`: Contains the certificate signing requests for the website SSL CA.
    - `key/`: Contains the private keys for the website SSL CA.
    - `ncrt/`: Contains the new certificate files for the website SSL CA.
- `pssl/`: Contains the files for the personal SSL CA.
    - `crl/`: Contains Certificate Revocation Lists (CRLs) for the CA.
    - `crt/`: Contains the issued certificates for the personal SSL CA.
    - `csr/`: Contains the certificate signing requests for the personal SSL CA.
    - `key/`: Contains the private keys for the personal SSL CA.
    - `ncrt/`: Contains the new certificate files for the personal SSL CA.

The script will then start a PHP server at `0.0.0.0:7783`. You can access the server in your browser by visiting `http://0.0.0.0:7783`.

### Creating a Docker Image

To create a Docker image, execute the following command in the terminal:
```bash
docker build -t my_php_server .
```

This command will run the Docker image and map port `7783` in the container to port `7783` on the host machine. You can access the PHP server in your browser by visiting `http://localhost:7783`.

## Conclusion

This README describes how to use the bash script `startup.sh`

```bash
docker run -p 7783:7783 my_php_server
```
