<div align="center">

  <img src="assets/SynkroContacts-3D-Banner.png" alt="SynkroContacts Banner" width="100%" />

  <h1>SynkroContacts</h1>
  <p><b>A fast, local-first Windows desktop contact & company manager built with .NET 8 and MVVM.</b></p>

  <p>
    <img src="https://img.shields.io/badge/.NET-8.0-512BD4?style=flat-square&logo=dotnet&logoColor=white" />
    <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20(x64)-0078D6?style=flat-square&logo=windows11&logoColor=white" />
    <img src="https://img.shields.io/badge/EF%20Core%20SQLite-8.0.11-003B57?style=flat-square&logo=sqlite&logoColor=white" />
    <img src="https://img.shields.io/badge/MVVM%20Toolkit-8.3.2-68217A?style=flat-square&logo=csharp&logoColor=white" />
    <img src="https://img.shields.io/badge/vCard-7.2.1-0284C7?style=flat-square" />
  </p>

</div>

---

## 📸 Screenshots

| Cyber Blue Theme | Amber Gold Theme |
| :---: | :---: |
| <img src="assets/contacts-blue.png" width="100%" /> | <img src="assets/contacts-gold.png" width="100%" /> |
| <img src="assets/companies-blue.png" width="100%" /> | <img src="assets/companies-gold.png" width="100%" /> |

---

## ⚡ Highlights

* **Bidirectional Linking:** Many-to-many relationship between **Contacts** and **Companies** with instant cross-navigation.
* **Rich Entity Profiles:** Structured names, auto-generated monogram initials, notes, and unlimited phones, emails, and addresses with `IsPreferred` priority resolution.
* **vCard (`.vcf`) Engine:** Full import/export support powered by `FolkerKinzel.VCards`.
* **100% Local & Private:** Zero cloud dependencies. Powered by a local SQLite database (`%AppData%\SynkroContacts\contacts.db`).
* **Modern Fluent UI:** Clean 3-pane master-detail dark interface with customizable accent themes.

---

## 🏗 Architecture & Tech Stack

Built on a decoupled **5-project architecture** targeting `net8.0-windows10.0.19041.0` (Windows 10 1809+ `x64`):

```text
SynkroContacts.sln
├── SynkroContacts/             # Presentation Layer (8 Views, ViewModels, UI Shell)
├── SynkroContacts.Services/    # Business Logic (Contacts, Companies, vCard, Logging, Notifications)
├── SynkroContacts.Data/        # Persistence Layer (EF Core 8 Context, Entities & SQLite Migrations)
├── SynkroContacts.DataMapping/ # Entity <-> Domain Model Mappers
└── SynkroContacts.Models/      # Domain Models, Computed Properties & Enums
```

| Package | Version | Role |
| :--- | :---: | :--- |
| `Microsoft.EntityFrameworkCore.Sqlite` | `8.0.11` | Local SQLite ORM & migrations |
| `CommunityToolkit.Mvvm` | `8.3.2` | Source-generated MVVM bindings & commands |
| `FolkerKinzel.VCards` | `7.2.1` | `.vcf` parsing and serialization |

---

## 🚀 Quick Start

**Prerequisites:** Windows 10/11 (x64), [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0), and **Visual Studio 2022** (`.NET desktop development` workload).

```bash
git clone https://github.com/jackstatham596/SynkroContacts.git
cd SynkroContacts
```

Open **`SynkroContacts.sln`** in Visual Studio 2022, set platform to **`x64`**, and press <kbd>F5</kbd>.

---

<div align="center">
  <img src="assets/SynkroContacts-3D-Icon.png" width="56" />
  <p><sub>Licensed under the MIT License • Built with C# & .NET 8</sub></p>
</div>
