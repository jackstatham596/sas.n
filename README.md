<div align="center">
  <img src="images/logo.png" alt="Simple Contacts logo" width="80" height="80">

  <h1>Simple Contacts</h1>

  <p>A lightweight, offline-first desktop contact manager for Windows — keep people and companies organized, linked together, and easy to find.</p>

  <p>
    <img src="https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet&logoColor=white" alt=".NET 8">
    <img src="https://img.shields.io/badge/UI-WPF-0078D4?logo=windows&logoColor=white" alt="WPF">
    <img src="https://img.shields.io/badge/platform-Windows-0078D4" alt="Platform: Windows">
    <img src="https://img.shields.io/badge/database-SQLite-003B57?logo=sqlite&logoColor=white" alt="SQLite">
    <img src="https://img.shields.io/badge/license-MIT-green" alt="License: MIT">
  </p>
</div>

---

## Table of Contents

- [About](#about)
- [Screenshots](#screenshots)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [License](#license)

## About

Simple Contacts is a native Windows desktop app for managing contacts and companies in one place. It's built for people who want a fast, local, no-account-needed alternative to cloud-based address books — your data stays on your own machine, in your own SQLite database, and nowhere else.

The UI is a hand-built dark theme with a custom title bar and a collapsible sidebar, backed by a clean, layered .NET architecture underneath.

## Screenshots

<p align="center">
  <img src="images/screenshot-company.png" alt="Company detail view" width="85%"><br>
  <sub>Company detail view — contact info, linked contacts, and notes</sub>
</p>

<p align="center">
  <img src="images/screenshot-contact.png" alt="Contact detail view" width="85%"><br>
  <sub>Contact detail view — multiple phones, emails, addresses, and linked companies</sub>
</p>

## Features

- 👤 **Contacts & Companies** — manage both as first-class records, each with a full profile.
- 🔗 **Two-way linking** — connect a contact to one or more companies (many-to-many); see the relationship from either side.
- 📇 **Rich fields** — multiple phone numbers, emails, and addresses per record, each tagged by kind:
  - Phone: `Mobile`, `Home`, `Work`, `Direct`, `Other`
  - Email: `Personal`, `Work`, `Other`
  - Address: `Home`, `Work`, `Other`
- ⭐ **Preferred values** — mark a phone, email, or address as preferred; it's the one shown first in lists.
- 📝 **Notes** — freeform notes attached to any contact or company.
- 🔍 **Instant search** — filter contacts and companies as you type.
- 🔄 **Import / Export (vCard)** — bring contacts in from a standard `.vcf` file, or export your data (vCard 3.0 or 4.0) to share or back up.
- 🔔 **Toast confirmations** — a small, unobtrusive toast after every save or delete.
- 💾 **Local & offline** — everything lives in a local SQLite database; no account, no cloud, no internet connection required.

## Tech Stack

| Layer | Technology |
|---|---|
| UI | WPF (.NET 8), [CommunityToolkit.Mvvm](https://github.com/CommunityToolkit/dotnet) |
| Data access | Entity Framework Core 8 (`Microsoft.EntityFrameworkCore.Sqlite`) |
| Database | SQLite |
| vCard import/export | [FolkerKinzel.VCards](https://github.com/FolkerKinzel/VCards) |

## Architecture

The solution is split into five focused projects:

```
SimpleContacts              →  WPF UI (views, theme, custom window chrome)
SimpleContacts.Services     →  Business logic (contacts, companies, vCard, logging)
SimpleContacts.DataMapping  →  Maps EF Core entities to domain models and back
SimpleContacts.Models       →  Domain models (MVVM observable objects)
SimpleContacts.Data         →  EF Core DbContext, entities, and migrations
```

The UI never talks to the database directly — it goes through `AppServices` → `IContactService` / `ICompanyService` → `AppDbContext`, with `DataMapper` translating between EF Core entities and the observable domain models the UI binds to.

## Getting Started

### Prerequisites

- Windows 10 (version 1809) or later
- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- Visual Studio 2022 with the **.NET desktop development** workload (includes WPF)

### Build & Run

```bash
git clone https://github.com/<your-username>/SimpleContacts.git
cd SimpleContacts
```

1. Open `SimpleContacts.sln` in Visual Studio 2022.
2. Make sure **SimpleContacts** is set as the startup project (it is by default).
3. Press **F5**, or use `Build → Build Solution` followed by `Debug → Start Without Debugging`.

Or run it straight from the CLI:

```bash
dotnet run --project SimpleContacts/SimpleContacts/SimpleContacts.csproj
```

On first launch, the app automatically creates its local SQLite database (`contacts.db`) under `%AppData%\SimpleContacts\` and applies the latest migrations — no manual setup required.

## Project Structure

```
SimpleContacts/                    # WPF app — UI, views, startup
  Views/                           # Home, Contacts, Companies, Edit forms, Import, Export, Settings
  Themes/Theme.xaml                # Dark color palette and control styles
  Assets/Icons/                    # App icons
  Services/                        # AppServices, DataStore, ModelBridge

SimpleContacts.Services/           # Business logic
  SimpleContacts.Services.Contacts/
  SimpleContacts.Services.Companies/
  SimpleContacts.Services.VCard/
  SimpleContacts.Services.Logging/
  SimpleContacts.Services.Notifications/

SimpleContacts.Data/               # EF Core DbContext, entities, migrations
SimpleContacts.DataMapping/        # Mapping between data entities and domain models
SimpleContacts.Models/             # Domain/UI models (MVVM observable objects)
```

## License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for details.

---

<div align="center">
  <sub>Built with WPF and .NET 8.</sub>
</div>
