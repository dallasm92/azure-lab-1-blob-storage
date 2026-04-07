# Lab Summary

## Overview

This lab walks through Azure Blob Storage setup and validation for a simple object storage workflow. The captured sequence covers:

1. Resource group creation
2. Storage account creation
3. Private container creation
4. File upload validation
5. SAS troubleshooting
6. Blob-level direct access validation
7. Lifecycle management rule creation

## Confirmed Configuration

- Resource group: `rg-azure-lab-storage`
- Storage account: `dallasstoragelab01`
- Container: `labfiles`
- Uploaded files visible in the evidence:
  - `sample txt file.txt`
  - `DSC_0240.JPG`
  - `Getting started with OneDrive.pdf`
- Lifecycle rule:
  - name: `move-old-blobs`
  - scope: all blobs in the storage account
  - blob type: block blobs / base blobs
  - condition: last modified more than `30` days ago
  - action: move to Cool storage

## Security Warnings

- `images/27-container-sas-authentication-failed-sensitive.png`
  - warning: the original screenshot exposed a SAS-bearing container URL
  - current state: redacted in place for repository use
- `images/29-blob-sas-direct-download-sensitive.png`
  - warning: the original screenshot exposed a working SAS-bearing blob URL
  - current state: redacted in place for repository use
- `images/28-blob-sas-form.png`
  - appears safe to keep, but review before public push if you want to minimize any account-key-adjacent UI exposure

## Step-by-Step Evidence Map

| Step | Screenshot | Caption |
|---|---|---|
| 1 | `images/01-resource-manager-home.png` | Azure Resource Manager landing view before creating the lab resource group. |
| 2 | `images/02-resource-group-create-form.png` | Resource group creation form with `rg-azure-lab-storage` in East US. |
| 3 | `images/03-resource-group-review.png` | Review step confirming the resource group name and region before submission. |
| 4 | `images/04-resource-group-created-toast.png` | Success toast confirming `rg-azure-lab-storage` was created. |
| 5 | `images/05-resource-group-listed.png` | Resource group list showing the new lab resource group. |
| 6 | `images/06-resource-group-overview.png` | Resource group overview page for `rg-azure-lab-storage`. |
| 7 | `images/07-storage-account-discovery.png` | Portal navigation toward storage account creation from the resource group context. |
| 8 | `images/08-storage-center-blob-storage.png` | Storage Center entry point for Blob Storage workflows. |
| 9 | `images/09-storage-account-create-basics.png` | Storage account creation form with the lab resource group selected. |
| 10 | `images/10-storage-account-type-selection.png` | Preferred storage type selection for Azure Blob Storage / Data Lake Storage Gen2. |
| 11 | `images/11-storage-account-create-basics-confirmed.png` | Storage account basics view after type selection. |
| 12 | `images/12-storage-account-review-summary.png` | Review view showing `dallasstoragelab01` before deployment. |
| 13 | `images/13-storage-account-networking-data-protection.png` | Supporting evidence for networking and data protection settings visible during creation. |
| 14 | `images/14-storage-account-deployment-toast.png` | Deployment-in-progress toast for the storage account. |
| 15 | `images/15-storage-account-deployment-in-progress.png` | Deployment blade showing the storage account deployment in progress. |
| 16 | `images/16-storage-account-deployment-succeeded.png` | Deployment succeeded confirmation for `dallasstoragelab01`. |
| 18 | `images/18-storage-account-overview.png` | Storage account overview showing the resource group, region, performance tier, and account kind. |
| 19 | `images/19-container-create-dialog.png` | New container dialog with `labfiles` entered. |
| 20 | `images/20-container-created-list.png` | Container list showing `labfiles` created successfully. |
| 21 | `images/21-container-overview.png` | `labfiles` container overview before blob-level work. |
| 22 | `images/22-blob-overview-selected-file.png` | Blob view showing uploaded files and the selected `sample txt file.txt` object. |
| 23 | `images/23-portal-download-complete.png` | Browser download completion indicator for the sample text file. |
| 25 | `images/25-container-sas-form.png` | Container-level SAS form using account key signing. |
| 26 | `images/26-container-sas-form-detail.png` | Additional container SAS configuration detail. |
| 27 | `images/27-container-sas-authentication-failed-sensitive.png` | Failed container-level SAS attempt showing `AuthenticationFailed`. The original capture exposed a SAS URL, and the repository copy is redacted. |
| 28 | `images/28-blob-sas-form.png` | Blob-level SAS generation form for `sample txt file.txt`. |
| 29 | `images/29-blob-sas-direct-download-sensitive.png` | Successful direct browser access to `sample txt file.txt` using a blob-level SAS URL. The original capture exposed a SAS URL, and the repository copy is redacted. |
| 30 | `images/30-lifecycle-management-overview.png` | Lifecycle management page before any rule is added. |
| 31 | `images/31-lifecycle-rule-details.png` | Rule details step with `move-old-blobs` defined for all blobs. |
| 32 | `images/32-lifecycle-rule-base-blobs-initial.png` | Base blobs rule step before the final aging threshold and action are fully set. |
| 33 | `images/33-lifecycle-rule-cool-after-30-days.png` | Base blobs rule configured to move blobs to Cool storage after 30 days since last modification. |
| 34 | `images/34-lifecycle-policy-updated.png` | Success confirmation that the lifecycle management policy was updated. |

## Accuracy Notes

- The uploaded files are confirmed from the storage container view, not inferred from file names outside the screenshots.
- The SAS troubleshooting sequence is confirmed by both the Azure portal and the browser error screenshot.
- The lifecycle rule action and threshold are confirmed by the final rule configuration screenshot.
- The final repo intentionally trims duplicate completion evidence to keep the screenshot set concise.

## Trimmed Evidence

- `images/17-storage-account-deployment-complete-detail.png`
  - removed because `images/16-storage-account-deployment-succeeded.png` already captures the same milestone clearly
- `images/24-container-overview-post-download.png`
  - removed because `images/21-container-overview.png`, `images/22-blob-overview-selected-file.png`, and `images/23-portal-download-complete.png` already cover the relevant workflow

## Portfolio Framing

This lab is strong portfolio evidence because it shows more than resource creation:

- it captures troubleshooting, not just happy-path clicks
- it demonstrates understanding of the difference between container-level and blob-level SAS behavior
- it includes verification of direct object access
- it closes with a practical lifecycle policy for cost management
