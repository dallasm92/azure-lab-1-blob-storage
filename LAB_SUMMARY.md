# Lab Summary

## Lab

Azure Lab 1: Secure Cloud File Share with Blob Storage

## Goal

Create a private Azure Blob Storage workflow, upload and validate files, troubleshoot SAS access, and apply a simple lifecycle rule for cost-aware storage management.

## Skills Demonstrated

- Azure resource group and storage account deployment
- Private blob container creation
- File upload and direct download validation
- SAS troubleshooting from failed container-level access to successful blob-level access
- Lifecycle management for storage cost control

## Final State

- `rg-azure-lab-storage` created successfully
- `dallasstoragelab01` deployed as the storage account
- `labfiles` created as a private container
- Sample files uploaded and direct blob download confirmed
- Blob-level SAS validated successfully after an initial failed container-level attempt
- `move-old-blobs` configured to move base blobs to Cool storage after `30` days

## Portfolio Value

This lab shows a full storage workflow with troubleshooting and cost-awareness, not just resource creation. It demonstrates private data handling, delegated access with SAS, and lifecycle policy configuration in a way that is easy to explain in a portfolio or interview.
