# Azure Lab 1: Secure Cloud File Share with Blob Storage

This lab documents the first free-first Azure storage workflow I built for portfolio use. The evidence set shows the full sequence for creating a resource group, deploying a storage account, creating a private container, uploading files, validating direct blob access, troubleshooting a failed container-level SAS attempt, generating a working blob-level SAS, and configuring lifecycle management to move older blobs to the Cool tier.

## Lab Scope

- Resource group: `rg-azure-lab-storage`
- Storage account: `dallasstoragelab01`
- Container: `labfiles`
- Uploaded files confirmed in the evidence:
  - `sample txt file.txt`
  - `DSC_0240.JPG`
  - `Getting started with OneDrive.pdf`
- Lifecycle rule:
  - `move-old-blobs`
  - base blobs
  - last modified
  - move to Cool storage after `30` days

## What This Lab Demonstrates

- Azure resource group creation and validation
- Azure Blob Storage account deployment
- Blob Storage / Data Lake Gen2-capable account selection through Azure Storage Center
- Private container creation
- Blob upload and portal-side object validation
- Direct browser download validation
- SAS troubleshooting:
  - initial container-level SAS attempt failed
  - blob-level SAS access succeeded
- Lifecycle management rule creation for cost optimization

## Key Outcomes

- Created `rg-azure-lab-storage` successfully.
- Deployed `dallasstoragelab01` as a Blob Storage-capable account.
- Created the `labfiles` container.
- Uploaded files to `labfiles`.
- Confirmed direct blob download worked.
- Captured a failed container-level SAS attempt for troubleshooting evidence.
- Generated a successful blob-level SAS and verified access in the browser.
- Created a lifecycle policy that moves old blobs to the Cool tier after 30 days.

## Accuracy Notes

- The storage account flow started from Azure Storage Center and used the Azure Blob Storage / Data Lake Storage Gen2 path shown in the screenshots.
- The SAS troubleshooting mattered because the first validation was attempted at the container level, while the successful delegated-access test was generated and validated against a specific blob.
- The lifecycle rule was intentionally kept simple for a first lab:
  - move base blobs to the Cool tier
  - 30 days after last modification
  - no delete action

## Evidence Map

- Resource group creation:
  - [02-resource-group-create-form.png](images/02-resource-group-create-form.png)
  - [04-resource-group-created-toast.png](images/04-resource-group-created-toast.png)
- Storage account deployment:
  - [09-storage-account-create-basics.png](images/09-storage-account-create-basics.png)
  - [16-storage-account-deployment-succeeded.png](images/16-storage-account-deployment-succeeded.png)
  - [18-storage-account-overview.png](images/18-storage-account-overview.png)
- Container creation and uploads:
  - [19-container-create-dialog.png](images/19-container-create-dialog.png)
  - [20-container-created-list.png](images/20-container-created-list.png)
  - [22-blob-overview-selected-file.png](images/22-blob-overview-selected-file.png)
- SAS troubleshooting and validation:
  - [25-container-sas-form.png](images/25-container-sas-form.png)
  - [27-container-sas-authentication-failed-sensitive.png](images/27-container-sas-authentication-failed-sensitive.png)
  - [28-blob-sas-form.png](images/28-blob-sas-form.png)
  - [29-blob-sas-direct-download-sensitive.png](images/29-blob-sas-direct-download-sensitive.png)
- Lifecycle management:
  - [30-lifecycle-management-overview.png](images/30-lifecycle-management-overview.png)
  - [33-lifecycle-rule-cool-after-30-days.png](images/33-lifecycle-rule-cool-after-30-days.png)
  - [34-lifecycle-policy-updated.png](images/34-lifecycle-policy-updated.png)

## Security Notes

- [27-container-sas-authentication-failed-sensitive.png](images/27-container-sas-authentication-failed-sensitive.png) was redacted before repository prep.
  - The browser address bar originally exposed a SAS-bearing storage URL.
- [29-blob-sas-direct-download-sensitive.png](images/29-blob-sas-direct-download-sensitive.png) was redacted before repository prep.
  - The browser address bar originally exposed a working SAS-bearing blob URL.
- Recommended cleanup if any captured SAS token was live during the screenshots:
  - rotate or let the original SAS tokens expire before publishing broadly

## Repository Notes

- Full screenshot-to-step mapping lives in [LAB_SUMMARY.md](LAB_SUMMARY.md).
- `images/desktop.ini` is a Windows artifact and should stay out of version control.
