<div align="center">

  <!-- HERO BANNER -->
  <img src="assets/SynkroContacts-3D-Banner.png" alt="SynkroContacts Banner" width="100%" style="border-radius: 12px;" />

  <br />
  <br />

  <!-- BADGES -->
  [![.NET 8](https://img.shields.io/badge/.NET%208.0-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
  [![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011%20(x64)-0078D6?style=for-the-badge&logo=windows&logoColor=white)](https://www.microsoft.com/windows)
  [![EF Core](https://img.shields.io/badge/EF%20Core%20SQLite-8.0.11-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://learn.microsoft.com/en-us/ef/core/)
  [![MVVM Toolkit](https://img.shields.io/badge/MVVM%20Toolkit-8.3.2-68217A?style=for-the-badge&logo=csharp&logoColor=white)](https://learn.microsoft.com/en-us/dotnet/communitytoolkit/mvvm/)
  [![vCard](https://img.shields.io/badge/vCard%20Support-7.2.1-0284C7?style=for-the-badge)](https://github.com/FolkerKinzel/VCards)

  <h1>SynkroContacts</h1>
  <p><b>A modern, fast, and privacy-first Windows desktop application for managing contacts and companies.</b></p>

  <p>
    <a href="#-features">Features</a> •
    <a href="#-screenshots">Screenshots</a> •
    <a href="#-architecture--project-structure">Architecture</a> •
    <a href="#-domain-models--schema">Data Models</a> •
    <a href="#-getting-started">Getting Started</a>
  </p>
</div>

---

## 🌟 Overview

**SynkroContacts** is a native Windows desktop application built on **.NET 8** following a clean, modular **MVVM** architecture. Designed with a sleek dark Fluent-inspired interface, it allows individuals and professionals to organize personal and business networks with bidirectional linking between **Contacts** and **Companies**, rich multi-field metadata, local **SQLite** persistence, and standard **vCard (`.vcf`)** import/export capabilities.

---

## ✨ Key Features

* 🎨 **Modern Fluent Dark UI:** Clean, distraction-free master-detail layout with dynamic accent theming.
* 👥 **Comprehensive Contact Management:** Store full name components, nicknames, titles, avatars (or auto-generated initials), notes, and multiple phone numbers, emails, and physical addresses.
* 🏢 **Company Directory & Bidirectional Linking:** Seamlessly link multiple contacts to companies and navigate between associated organizations and personnel with a single click.
* ⭐ **Smart Primary Fields:** Automatically resolves `PrimaryPhone`, `PrimaryEmail`, and `PrimaryLocation` based on preferred flags (`IsPreferred`) or fallback priorities.
* 🔄 **vCard (`.vcf`) Import & Export:** Powered by `FolkerKinzel.VCards` for reliable contact migration and backup.
* 🔒 **100% Local & Private:** All data is stored locally on your machine using **SQLite** and **Entity Framework Core 8**—no cloud dependencies or telemetry.

---

## 📸 Screenshots

### 🔵 Blue Accent Theme
| Contacts View | Companies View |
| :---: | :---: |
| <img src="assets/contacts-blue.png" alt="Contacts View - Blue Theme" width="100%" /> | <img src="assets/companies-blue.png" alt="Companies View - Blue Theme" width="100%" /> |

### 🟠 Gold Accent Theme
| Contacts View | Companies View |
| :---: | :---: |
| <img src="assets/contacts-gold.png" alt="Contacts View - Gold Theme" width="100%" /> | <img src="assets/companies-gold.png" alt="Companies View - Gold Theme" width="100%" /> |

---

## 🛠 Tech Stack & Specifications

### System & Build Target
| Property | Value |
| :--- | :--- |
| **Output Type** | `WinExe` (Windows Desktop Application) |
| **Target Framework** | `net8.0-windows10.0.19041.0` |
| **Minimum Windows Version** | `10.0.17763.0` (Windows 10 version 1809 or higher) |
| **Target Platform** | `x64` |
| **Root Namespace / Assembly** | `SynkroContacts` |

### Core Libraries & NuGet Packages
| Package | Version | Purpose |
| :--- | :---: | :--- |
| `Microsoft.EntityFrameworkCore.Sqlite` | `8.0.11` | Local SQLite database ORM & migrations |
| `CommunityToolkit.Mvvm` | `8.3.2` | Modern, source-generated MVVM implementation |
| `FolkerKinzel.VCards` | `7.2.1` | Parsing, serializing, and handling `.vcf` vCard files |

---

## 🏗 Architecture & Project Structure

The solution is divided into **5 decoupled projects** adhering to separation of concerns:

```text
SynkroContacts.sln
├── 🖥️ SynkroContacts/                  # Presentation Layer (WinExe — UI, Views, ViewModels & Startup)
├── ⚙️ SynkroContacts.Services/         # Business Logic & Application Services
│   ├── SynkroContacts.Services.Contacts
│   ├── SynkroContacts.Services.Companies
│   ├── SynkroContacts.Services.VCard
│   ├── SynkroContacts.Services.Notifications
│   └── SynkroContacts.Services.Logging
├── 🗄️ SynkroContacts.Data/             # Data Access Layer (EF Core 8 & SQLite)
│   ├── SynkroContacts.Data.Entities
│   └── SynkroContacts.Data.Migrations
├── 🔄 SynkroContacts.DataMapping/      # Entity <-> Domain Model Mappers
└── 📦 SynkroContacts.Models/           # Domain Models & Enumerations
    └── SynkroContacts.Models.Enums
```

### Application Views (8 Core Views)
* `HomeView` — Dashboard and quick overview
* `ContactsView` — Master-detail contact directory with instant search
* `ContactEditView` — Create and modify contact profiles & linked companies
* `CompaniesView` — Master-detail company directory
* `CompanyEditView` — Create and modify company profiles & linked contacts
* `ImportView` — Import contacts from `.vcf` (vCard) files
* `ExportView` — Export contacts to `.vcf` (vCard) files
* `SettingsView` — Application preferences and theme customization

---

## 📐 Domain Models & Schema

<details>
<summary><b>👤 Contact Model (Click to expand)</b></summary>
<br />

| Field | Type | Description |
| :--- | :--- | :--- |
| `Uid` | `Guid` | Unique identifier |
| `FirstName` | `string` | Contact's first name |
| `MiddleName` | `string` | Contact's middle name |
| `LastName` | `string` | Contact's last name |
| `NickName` | `string` | Contact's nickname |
| `Title` | `string` | Job title or honorific |
| `FullName` | `string` | Formatted full name |
| `Image` | `string?` | Optional path to profile image |
| `Notes` | `string` | Free-form notes |
| `Phones` | `List<ContactPhone>` | Associated phone numbers |
| `Emails` | `List<ContactEmail>` | Associated email addresses |
| `Addresses` | `List<ContactAddress>` | Associated physical addresses |
| `Companies` | `List<Company>` | Linked companies |

**Computed Properties:**
* `Initials` — Automatically generated from name components when no image is set.
* `PrimaryPhone` / `PrimaryEmail` / `PrimaryLocation` — Resolves the first `IsPreferred` item, or falls back to the first available entry.
* `HasNameComponents` — Indicates whether structured name fields are populated.

</details>

<details>
<summary><b>🏢 Company Model (Click to expand)</b></summary>
<br />

| Field | Type | Description |
| :--- | :--- | :--- |
| `Uid` | `Guid` | Unique identifier |
| `Name` | `string` | Company name |
| `Description` | `string` | Brief company overview |
| `Image` | `string?` | Optional path to company logo |
| `Notes` | `string` | Free-form notes |
| `Phones` | `List<CompanyPhone>` | Company phone numbers |
| `Emails` | `List<CompanyEmail>` | Company email addresses |
| `Addresses` | `List<CompanyAddress>` | Company office locations |
| `Contacts` | `List<Contact>` | Linked contacts associated with the company |

</details>

<details>
<summary><b>📞 Phone, ✉️ Email, 📍 Address & Enums (Click to expand)</b></summary>
<br />

#### `ContactPhone` / `CompanyPhone`
* **Fields:** `Uid` (`Guid`), `Number` (`string`), `Description` (`string`), `Kind` (`PhoneKind`), `IsPreferred` (`bool`)
* **`PhoneKind` Enum:** `Mobile`, `Home`, `Work`, `Direct`, `Other`

#### `ContactEmail` / `CompanyEmail`
* **Fields:** `Uid` (`Guid`), `Address` (`string`), `Description` (`string`), `Kind` (`EmailKind`), `IsPreferred` (`bool`)
* **`EmailKind` Enum:** `Personal`, `Work`, `Other`

#### `ContactAddress` / `CompanyAddress`
* **Fields:** `Uid` (`Guid`), `Street` (`string`), `City` (`string`), `State` (`string`), `PostalCode` (`string`), `Country` (`string`), `Kind` (`AddressKind`), `IsPreferred` (`bool`)
* **Computed Property:** `CityLine` (Formatted city, state, and postal code)
* **`AddressKind` Enum:** `Home`, `Work`, `Other`

</details>

---

## 💾 Database Storage

SynkroContacts uses a local **SQLite** database managed via **Entity Framework Core 8** (`AppDbContextFactory` configured with `UseSqlite`).

* **Default Database Path:**
  ```text
  %AppData%\SynkroContacts\contacts.db
  ```

---

## 🚀 Getting Started

### Prerequisites
* **OS:** Windows 10 (version 1809 / build 17763 or newer) or Windows 11 (`x64`)
* **IDE:** [Visual Studio 2022](https://visualstudio.microsoft.com/) with the **.NET desktop development** workload installed
* **SDK:** [.NET 8.0 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)

### Build & Run
1. **Clone the repository:**
   ```bash
   git clone https://github.com/<your-username>/SynkroContacts.git
   cd SynkroContacts
   ```
2. **Open in Visual Studio:**
   * Double-click `SynkroContacts.sln` to open the solution in **Visual Studio 2022**.
3. **Run the application:**
   * Set `SynkroContacts` as the Startup Project, select the `x64` configuration, and press **`F5`** (or click **Start**).

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](../../issues) or submit a Pull Request.

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

<div align="center">
  <br />
  <img src="assets/SynkroContacts-3D-Icon.png" alt="SynkroContacts Logo" width="64" />
  <p>Built with ❤️ using .NET 8</p>
</div>
