# Windows Server 2025, 2022 & 2019 Product Keys

> **Important:** The keys below are Microsoft-published **KMS client keys (GVLKs)**. They **cannot activate a retail installation** of Windows Server.
> They only activate against an organisation's own KMS host or Active Directory-based activation.
>
> To activate a standalone or production server, you need a genuine licence. See [How to activate Windows Server legally](#how-to-activate-windows-server-legally).

Maintained by [Noxkeys](https://noxkeys.com/), an online store for genuine software licences. Corrections are welcome.

---

## Table of contents

- [Which Windows Server key do I need?](#which-windows-server-key-do-i-need)
- [Windows Server 2025 KMS keys](#windows-server-2025-kms-keys)
- [Windows Server 2022 KMS keys](#windows-server-2022-kms-keys)
- [Windows Server 2019 KMS keys](#windows-server-2019-kms-keys)
- [Windows Server 2016 KMS keys](#windows-server-2016-kms-keys)
- [Standard vs Datacenter](#standard-vs-datacenter)
- [Support lifecycle](#support-lifecycle)
- [Useful commands (slmgr & DISM)](#useful-commands-slmgr--dism)
- [Convert Evaluation to full version](#convert-evaluation-to-full-version)
- [Common activation errors](#common-activation-errors)
- [How to activate Windows Server legally](#how-to-activate-windows-server-legally)
- [FAQ](#faq)
- [References](#references)

---

## Which Windows Server key do I need?

| You want to…                                                    | Use                                  |
| --------------------------------------------------------------- | ------------------------------------ |
| Activate servers on a network that runs a KMS host              | KMS client key (GVLK) from this page |
| Switch a volume-licensed server to KMS activation               | KMS client key (GVLK) from this page |
| Activate a standalone, home-lab or production server            | A **genuine retail / OEM licence**   |
| Convert an Evaluation install to a full licensed install        | A **genuine product key** + DISM     |

---

## Windows Server 2025 KMS keys

| Edition                                       | KMS client key (GVLK)         |
| --------------------------------------------- | ----------------------------- |
| Windows Server 2025 Standard                  | TVRH6-WHNXV-R9WG3-9XRFY-MY832 |
| Windows Server 2025 Datacenter                | D764K-2NDRG-47T6Q-P8T8W-YP6DF |
| Windows Server 2025 Datacenter: Azure Edition | XGN3F-F394H-FD2MY-PP6FD-8MCRC |

---

## Windows Server 2022 KMS keys

| Edition                                       | KMS client key (GVLK)         |
| --------------------------------------------- | ----------------------------- |
| Windows Server 2022 Standard                  | VDYBN-27WPP-V4HQT-9VMD4-VMK7H |
| Windows Server 2022 Datacenter                | WX4NM-KYWYW-QJJR4-XV3QB-6VM33 |
| Windows Server 2022 Datacenter: Azure Edition | NTBV8-9K7Q8-V27C6-M2BTV-KHMXV |

---

## Windows Server 2019 KMS keys

| Edition                          | KMS client key (GVLK)         |
| -------------------------------- | ----------------------------- |
| Windows Server 2019 Standard     | N69G4-B89J2-4G8F4-WWYCC-J464C |
| Windows Server 2019 Datacenter   | WMDGN-G9PQG-XVVXX-R3X43-63DFG |
| Windows Server 2019 Essentials   | WVDHN-86M7X-466P6-VHXV7-YY726 |

---

## Windows Server 2016 KMS keys

| Edition                          | KMS client key (GVLK)         |
| -------------------------------- | ----------------------------- |
| Windows Server 2016 Standard     | WC2BQ-8NRM3-FDDYY-2BFGV-KHKQY |
| Windows Server 2016 Datacenter   | CB7KF-BWN84-R7R2Y-793K2-8XDDG |
| Windows Server 2016 Essentials   | JCKRF-N37P4-C2D82-9YXRT-4M63B |

---

## Standard vs Datacenter

| Feature                                    | Standard                    | Datacenter               |
| ------------------------------------------ | --------------------------- | ------------------------ |
| Virtual machines (Windows Server guests)   | 2 per fully licensed server | Unlimited                |
| Storage Spaces Direct                      | No                          | Yes                      |
| Software-defined networking (SDN)          | No                          | Yes                      |
| Shielded virtual machines                  | No                          | Yes                      |
| Storage Replica                            | Limited                     | Full                     |
| Licensing model                            | Per core (min. 16 cores)    | Per core (min. 16 cores) |
| Best for                                   | Physical or light VM use    | Heavily virtualised hosts |

**Rule of thumb:** choose **Standard** if the host will run up to two Windows Server VMs. Choose **Datacenter** if it will run many VMs or needs Storage Spaces Direct.

---

## Support lifecycle

| Version               | Mainstream support ends | Extended support ends |
| --------------------- | ----------------------- | --------------------- |
| Windows Server 2025   | 2029                    | 2034                  |
| Windows Server 2022   | October 2026            | 2031                  |
| Windows Server 2019   | January 2024            | 2029                  |
| Windows Server 2016   | January 2022            | January 2027          |

**Recommendation:** Windows Server 2025 is the best choice for new deployments in 2026 because it has the longest support period. Windows Server 2016 reaches end of extended support in January 2027 and should be upgraded.

---

## Useful commands (slmgr & DISM)

Run these in **Command Prompt (Admin)** or **PowerShell (Admin)**:

```bat
:: Show the installed edition
DISM /Online /Get-CurrentEdition

:: Show which editions this install can be upgraded to
DISM /Online /Get-TargetEditions

:: Install a product key
slmgr /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX

:: Point the server at a specific KMS host (optional)
slmgr /skms kms.yourdomain.local:1688

:: Activate
slmgr /ato

:: Show licence details (channel: Retail / OEM / Volume)
slmgr /dlv

:: Check whether activation is permanent
slmgr /xpr

:: Remove the current key
slmgr /upk
slmgr /cpky
```

---

## Convert Evaluation to full version

Windows Server **Evaluation** expires after 180 days. You can convert it to a full licensed version without reinstalling:

```bat
:: 1. Confirm it is an Evaluation build (e.g. ServerStandardEval)
DISM /Online /Get-CurrentEdition

:: 2. Convert to Standard with your genuine product key
DISM /Online /Set-Edition:ServerStandard /ProductKey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /AcceptEula

:: Or convert to Datacenter
DISM /Online /Set-Edition:ServerDatacenter /ProductKey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /AcceptEula
```

The server restarts during conversion. **Note:** a server promoted to a domain controller cannot be converted. Demote it first, or convert before promoting.

---

## Common activation errors

| Error code   | What it means                                 | Fix                                                              |
| ------------ | --------------------------------------------- | ---------------------------------------------------------------- |
| `0xC004F074` | No KMS server could be contacted              | A KMS key was used without a KMS host. Install a retail key      |
| `0xC004F050` | The product key is invalid for this edition   | Check the key matches the edition (Standard vs Datacenter)       |
| `0xC004C003` | The product key was blocked                   | Replace it with a genuine key from an authorised seller          |
| `0xC004F069` | The product SKU was not found                 | Usually an Evaluation build. Convert it with DISM first          |
| `0xC004C008` | The key has been used too many times          | Contact your seller for a replacement                            |

---

## How to activate Windows Server legally

KMS keys only work with a KMS host. For a standalone server, a home lab or a small business you need a **genuine licence**:

- **Windows Server 2025 Standard / Datacenter**: the latest release, with the longest support
- **Windows Server 2022 Standard / Datacenter**: proven and widely deployed
- **Windows Server 2019 Standard / Datacenter**: for compatibility with older software
- **Remote Desktop Services CALs**: required for RDS user or device connections

Genuine Windows Server licences with instant email delivery are available at **[noxkeys.com](https://noxkeys.com/)**.

---

## FAQ

**Are these Windows Server keys free to use?**
Yes. Microsoft publishes them openly, but they only activate against a KMS host. They will not activate a standalone server.

**Can I use a Windows Server 2022 key on Windows Server 2025?**
No. Each key is tied to a specific version and edition.

**What happens when Windows Server Evaluation expires?**
After 180 days the server shuts down every hour and shows a licensing warning. Convert it to a full version with DISM and a genuine key.

**Can I upgrade Standard to Datacenter without reinstalling?**
Yes. Run `DISM /Online /Set-Edition:ServerDatacenter /ProductKey:<key> /AcceptEula` with a genuine Datacenter key.

**Do I need CALs for Windows Server?**
Yes. Client Access Licences are required for users or devices that access the server, and separate RDS CALs are needed for Remote Desktop Services.

**Which is better for a home lab: Standard or Datacenter?**
Standard is enough for most home labs that run one or two Windows Server VMs. Datacenter makes sense if you plan to run many VMs.

---

## References

- [Microsoft Learn – KMS client activation keys](https://learn.microsoft.com/en-us/windows-server/get-started/kms-client-activation-keys)
- [Microsoft Learn – Upgrade and conversion options for Windows Server](https://learn.microsoft.com/en-us/windows-server/get-started/upgrade-conversion-options)
- [Microsoft Learn – Windows Server lifecycle](https://learn.microsoft.com/en-us/lifecycle/products/?terms=windows%20server)
- [Windows 11 & 10 Product Keys](https://github.com/webex9/windows-11-10-product-keys) – companion reference for Windows editions
- [Microsoft Office 2024, 2021 & 2019 Product Keys](https://github.com/webex9/microsoft-office-2024-2021-2019-product-keys) – companion reference for Office
- [Noxkeys – Genuine Windows Server licences](https://noxkeys.com/)

---

⭐ **If this helped, star the repo** so others can find it. Last updated: October 2026.
