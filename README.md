<div align="center">
  <img src="images/logo.png" alt="Simple Contacts logo" width="80" height="80">

  <h1>Simple Contacts</h1>

  <p>A lightweight, offline-first desktop contact manager for Windows — keep people and companies organized, linked together, and easy to find.</p>

  <p>
    <img src="https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet&logoColor=white" alt=".NET 8">
    <img src="https://img.shields.io/badge/UI-WPF-0078D4?logo=windows&logoColor=white" alt="WPF">
    <img src="https://img.shields.io/badge/platform-Windows-0078D4" alt="Platform: Windows">
    <img src="https://img.shields.io/badge/license-MIT-green" alt="License: MIT">
  </p>
</div>

---

## Table of Contents

- [About](#about)
- [Screenshots](#screenshots)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [License](#license)

## About

Simple Contacts is a native Windows desktop app for managing contacts and companies in one place. It's built for people who want a fast, local, no-account-needed alternative to cloud-based address books — your data stays on your own machine, in your own SQLite database, and nowhere else.

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
- 🔗 **Two-way linking** — connect a contact to one or more companies; see the relationship from either side.
- 📇 **Rich fields** — multiple phone numbers, emails, and addresses per record, each tagged by kind (Work, Home, Mobile, Direct, Other…).
- 📝 **Notes** — freeform notes attached to any contact or company.
- 🔍 **Instant search** — filter contacts and companies as you type.
- 🔄 **Import / Export (vCard)** — bring contacts in from a standard `.vcf` file, or export your data to share or back up.
- 💾 **Local & offline** — everything lives in a local SQLite database; no account, no cloud, no internet connection required.

## Tech Stack

| Layer | Technology |
|---|---|
| UI | WPF (.NET 8), [CommunityToolkit.Mvvm](https://github.com/CommunityToolkit/dotnet) |
| Data access | Entity Framework Core 8 |
| Database | SQLite |
| vCard import/export | [FolkerKinzel.VCards](https://github.com/FolkerKinzel/VCards) |

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

On first launch, the app automatically creates its local SQLite database under `%AppData%\SimpleContacts\` — no manual setup required.

## Project Structure

```
SimpleContacts/              # WPF app — UI, views, startup
SimpleContacts.Services/     # Business logic — contacts, companies, vCard, notifications
SimpleContacts.Data/         # EF Core DbContext, entities, migrations
SimpleContacts.DataMapping/  # Mapping between data entities and domain models
SimpleContacts.Models/       # Domain/UI models (MVVM observable objects)
```

## License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for details.

---

<div align="center">
  <sub>Built with WPF and .NET 8.</sub>
</div>
