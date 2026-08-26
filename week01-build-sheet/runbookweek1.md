# Windows 11 VM Baseline Build Runbook

## Executive Summary

A Windows 11 baseline is a standardized virtual machine (VM) configured in a known-good state before any additional software or configuration changes are made. Maintaining a clean baseline image ensures consistency, simplifies troubleshooting, and provides a reliable recovery point if future updates or changes cause system instability.

---

# Prerequisites

## Approved Software and Media

- Microsoft Windows 11 Enterprise or Windows 11 Pro ISO (organization-approved version)
- Valid Windows 11 license or activation key
- Supported hypervisor:
  - VMware Workstation
  - Hyper-V
  - VirtualBox
- Access to Windows Update services

## VM Hardware Requirements

| Setting | Recommended Value |
|----------|------------------|
| CPU | 2 vCPUs minimum |
| Memory | 8 GB RAM |
| Storage | 80 GB dynamically expanding VHD/VMDK |
| Firmware | UEFI |
| TPM | TPM 2.0 enabled |
| Secure Boot | Enabled |
| Network | NAT or Bridged Adapter |

---

# Procedure

## 1. Create the Virtual Machine

1. Open the hypervisor.
2. Select **Create New Virtual Machine**.
3. Attach the approved Windows 11 ISO.
4. Configure VM hardware:
   - 2 vCPUs or greater
   - 8 GB RAM
   - 80 GB virtual disk
   - UEFI firmware
   - TPM 2.0 enabled
   - Secure Boot enabled
5. Save the VM configuration.

## 2. Install Windows 11

1. Start the VM.
2. Follow the Windows installation wizard.
3. Select the approved Windows 11 edition.
4. Create the system partition using default settings.
5. Complete the installation process.
6. Sign in using the designated administrative account.

## 3. Configure Initial Settings

1. Verify the correct computer name.
2. Set the correct date, time, and time zone.
3. Confirm network connectivity.
4. Remove unnecessary startup applications if present.
5. Enable Remote Desktop if required by organizational standards.

## 4. Apply Windows Updates

1. Open **Settings → Windows Update**.
2. Select **Check for updates**.
3. Install all available security and quality updates.
4. Restart the VM when prompted.
5. Repeat the update process until no additional updates are available.

## 5. Document Baseline Information

Record the following information:

- Computer name
- Windows edition
- Version and build number
- Assigned IP address
- Number of vCPUs
- RAM allocation
- Virtual disk size
- Installation date

## 6. Create Baseline Snapshot

1. Shut down the VM or ensure it is in a stable state.
2. Open the hypervisor management console.
3. Create a snapshot named:

   `W01_CleanBaseline`

4. Add the description:

   "Clean Windows 11 baseline after installation and updates."

5. Verify the snapshot appears in the snapshot manager.

---

# Verification

Perform the following checks to confirm the baseline is correct:

## Inventory Verification

Confirm documentation includes:

- Computer name
- Windows edition
- OS build/version
- IP address
- CPU allocation
- Memory allocation
- Disk allocation

## Update Verification

1. Open **Settings → Windows Update**.
2. Verify the status displays:

   **"You're up to date"**

3. Review Update History for successful installation of recent updates.

## Snapshot Verification

1. Open the hypervisor snapshot manager.
2. Confirm snapshot:

   `W01_CleanBaseline`

   exists and is available for restoration.

3. Document the snapshot creation date and time.

---

# Rollback Procedure

If a later configuration change, software installation, or update causes system instability, revert the VM to the baseline snapshot.

## Steps

1. Shut down the VM.
2. Open the hypervisor management console.
3. Navigate to the VM snapshot manager.
4. Locate the snapshot:

   `W01_CleanBaseline`

5. Select **Revert**, **Restore**, or the equivalent option for the hypervisor.
6. Confirm the restoration action.
7. Power on the VM.
8. Verify the operating system loads normally.
9. Confirm the VM configuration matches the documented baseline inventory.

## Expected Result

The VM is restored to the original clean Windows 11 baseline state with all approved updates installed and no subsequent configuration changes present.
