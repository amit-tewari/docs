---
description: How Docker Scout handles image metadata
keywords: scanning, supply chain, security, data, metadata
title: Data collection and storage in Docker Scout
---

{% include scout-early-access.md %}

Docker Scout image analysis works by collecting metadata from the container
images that you analyze. This metadata is stored on the Docker Scout platform.

## Data transmission

Docker Scout collects and sends the following image metadata to the platform.

Docker and OCI image metadata:

- Image creation timestamp
- Image digest
- Ports exposed by the image
- Environment variable names and values
- Name and value of image labels
- Order of image layers
- Hardware architecture
- Operating system type and version
- Registry URL and type

Software Bill of Materials (SBOM) metadata:

- Advisory prefix URL (PURL)
- Package author and description
- License IDs
- Package name and namespace
- Package scheme and size
- Package type and version
- Filepath within the image
- The type of direct dependency
- Total package count

SBOM metadata is used to match package types and versions with public
vulnerability data to infer whether a package is considered vulnerable.
When the Docker Scout platform receives information from its advisory database
about new CVEs (and other risks, such as leaked secrets), it "overlays" this
information on the SBOM. If there's a match, the results of the match are
displayed in the user interfaces where Docker Scout data is surfaced, such as
the Docker Scout Dashboard and in Docker Desktop.

## Data storage

For the purposes of providing the Docker Scout service, data is stored using:

- Amazon Web Services (AWS) on servers located in US-EAST, USA
- Google Cloud Platform (GCP) on servers located in US-EAST, USA

Data is used according to the processes described at
[docker.com/legal](https://www.docker.com/legal/) to provide the key
capabilities of Docker Scout.
