# Azure Lab 1: Secure Cloud File Share with Blob Storage

## Objective

Deploy a basic Azure storage workflow by creating a resource group, provisioning a storage account, creating a private blob container, uploading files, validating direct blob access, troubleshooting SAS access, and applying a simple lifecycle rule for cost-aware storage management.

## Environment

- Platform: Microsoft Azure
- Subscription shown in evidence: `Azure subscription 1`
- Region: `East US`
- Evidence source: screenshots captured in the Azure portal and browser validation flow

## Azure Services Used

- Resource Groups
- Azure Storage account
- Blob Containers
- Shared Access Signatures (SAS)
- Lifecycle Management

## Resource Details

- Resource group: `rg-azure-lab-storage`
- Storage account: `dallasstoragelab01`
- Container: `labfiles`
- Uploaded files confirmed in the evidence:
  - `sample txt file.txt`
  - `DSC_0240.JPG`
  - `Getting started with OneDrive.pdf`
- Lifecycle rule: `move-old-blobs`
- Lifecycle action: move base blobs to Cool storage after `30` days

## Lab Relationship

This lab is the first Azure portfolio workflow in the series. It establishes the storage and cost-awareness foundation before the later networking, RBAC, and VM labs.

## Steps Performed

1. Created the resource group `rg-azure-lab-storage`.
2. Opened Azure Storage Center and started a new storage account deployment.
3. Deployed `dallasstoragelab01` using the Blob Storage / Data Lake Gen2-capable path shown in the portal.
4. Opened the storage account overview after deployment.
5. Created the private blob container `labfiles`.
6. Uploaded sample files to the container.
7. Selected and downloaded a blob directly from the portal to confirm access.
8. Generated and tested a container-level SAS that failed during validation.
9. Generated and tested a blob-level SAS that succeeded.
10. Opened lifecycle management and created the `move-old-blobs` policy.
11. Configured the lifecycle rule to move base blobs to the Cool tier after 30 days.

## Validation

- The resource group and storage account deployed successfully.
- The `labfiles` container was created as a private container.
- Direct blob download worked from the portal.
- The initial container-level SAS attempt failed and was preserved as troubleshooting evidence.
- A blob-level SAS worked for delegated browser access.
- The final lifecycle rule moved base blobs to the Cool tier after 30 days with no delete action.

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

## What I Learned

- Azure Storage workflows are easier to document when the resource hierarchy is clear: resource group, storage account, container, then blob.
- SAS troubleshooting is part of the skill, not just the successful end state. The failed container-level test made the blob-level delegated-access model easier to understand.
- Lifecycle management is a practical way to show cost awareness in a beginner storage lab without adding unnecessary complexity.
- A first storage lab can still demonstrate security thinking by keeping the container private and treating SAS URLs as sensitive artifacts.

## Problems Encountered / Notes

- The storage account flow started from Azure Storage Center and used the Azure Blob Storage / Data Lake Storage Gen2 path shown in the screenshots.
- The first SAS validation was attempted at the container level, while the successful delegated-access test was generated and validated against a specific blob.
- The lifecycle rule was intentionally kept simple for a first lab:
  - move base blobs to the Cool tier
  - 30 days after last modification
  - no delete action

## Security Notes

- [27-container-sas-authentication-failed-sensitive.png](images/27-container-sas-authentication-failed-sensitive.png) was redacted before repository prep.
  - The browser address bar originally exposed a SAS-bearing storage URL.
- [29-blob-sas-direct-download-sensitive.png](images/29-blob-sas-direct-download-sensitive.png) was redacted before repository prep.
  - The browser address bar originally exposed a working SAS-bearing blob URL.
- Recommended cleanup if any captured SAS token was live during the screenshots:
  - rotate or let the original SAS tokens expire before publishing broadly

## Cost Control and Cleanup

- This lab stayed within a small storage-only footprint and avoided compute resources entirely.
- The lifecycle rule was configured for Cool-tier transition only, not deletion, so the evidence remained easy to review without making the lab look destructive.
- SAS was kept short-lived and treated as a sensitive delegated-access mechanism.
- `TODO`: Confirm whether `rg-azure-lab-storage` was deleted after the lab if you want the repo to claim full cleanup completion.

## Repository Notes

- Full screenshot-to-step mapping lives in [LAB_SUMMARY.md](LAB_SUMMARY.md).
- `images/desktop.ini` is a Windows artifact and should stay out of version control.

## Outcome

The lab produced a complete Azure Blob Storage workflow with private container creation, file upload and download validation, SAS troubleshooting, successful blob-level delegated access, and a simple lifecycle rule for cost-aware storage management.
