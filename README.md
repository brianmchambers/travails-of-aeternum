# Travails of AEternum

Travails of AEternum is a retro-inspired JRPG (NES/SNES-style) currently in development using MonoGame on .NET 9. The project follows Clean Architecture principles, favors modular code, and uses Tiled for map creation. This repository also contains a static website (under /website) hosted on GitHub Pages that documents the development journey and blog.

Status
- Work in progress — early development and prototypes.
- CI and release workflows have placeholder actions under .github/workflows.

Core technologies
- C#, .NET 9
- MonoGame (latest stable)
- Tiled (map editor)
- Clean Architecture (project structure and boundaries)
- GitHub + GitHub Pages (website)
- Trello (project management)
- Toggl (timekeeping)

Repository layout (high level)
- src/           — game and engine projects (C# / MonoGame)
- content/       — assets, tilesets and Tiled maps
- website/       — static site for the project blog and pages
- .github/       — CI / Pages workflows and other GitHub configs

Getting started (developer)
1. Install prerequisites:
   - .NET 9 SDK
   - MonoGame for your platform
   - Tiled (for map editing)
2. Restore & build:
   - dotnet restore
   - dotnet build
3. Run the game:
   - dotnet run --project <path-to-game-project.csproj>
   - (Adjust project path to match the project you work on; inspect the src/ directory.)
4. Run tests (if present):
   - dotnet test

Website
- The static website is in /website and is deployed to GitHub Pages by the workflow at .github/workflows/release-website.yml.
- To preview locally, open website/index.html in a browser or use a simple static server.

Contributing
- See CONTRIBUTING.md for contribution guidelines, branch naming, PR expectations, and how we track work (Trello/Toggl).
- By contributing you agree to follow the Code of Conduct.

Reporting issues & feature requests
- Open an issue in this repository with a clear title and reproduction steps or use the issue templates (if present).
- For sensitive conduct reports, see CODE_OF_CONDUCT.md for contact options.

License
- This project is licensed under the MIT License — see LICENSE for details.

Project contacts
- Maintainer: @brianmchambers
- Website / blog documents the ongoing journey — thank you for following the development of Travails of AEternum!
