# Contributing to Travails of AEternum

Thank you for your interest in contributing! We welcome help on code, assets, documentation, the website, and community/build tasks. Below are guidelines to make collaboration smooth.

Before you begin
- Read CODE_OF_CONDUCT.md and follow it.
- Check open issues and Trello board for existing tasks. If you start work, create or claim a Trello card so work can be tracked.
- Log development time with Toggl if you are contributing as part of larger coordinated work (optional for casual contributors).

Workflow
1. Create an issue first for significant changes or features. Discuss design and scope there.
2. Create a branch for your work:
   - Naming: feature/<short-description>, fix/<short-description>, docs/<topic>
3. Implement your changes following the project’s architecture and style rules:
   - Follow Clean Architecture boundaries.
   - Keep code modular and testable.
   - Use Tiled for map edits; add exported .tmx files or the source tilemap in content/.
   - Keep game logic separated from rendering and platform specifics.
4. Add or update tests where applicable.
5. Open a pull request describing:
   - What the change does
   - Why it’s needed
   - Any migration or manual steps (e.g., update Tiled tileset)
   - Screenshots or GIFs for visual changes
6. Address review feedback and keep commits focused. Squash if requested.

Development conventions
- Target .NET 9 and the project’s current MonoGame version.
- Follow C# naming and formatting conventions. An .editorconfig should be respected where present.
- Keep methods small and classes focused.
- Avoid large single commits; prefer a clear commit history.

Pull request checklist
- [ ] Tests added or updated (when applicable)
- [ ] Builds cleanly (dotnet build)
- [ ] No new warnings or known regressions
- [ ] Documentation updated (README, website, or in-code comments)
- [ ] Follows Clean Architecture and modular design goals

Submitting assets (art, music, etc.)
- Include source files when possible (Tiled .tmx, tileset sources).
- Provide attribution and licensing information for 3rd-party assets.
- Prefer lossless or high-quality source files in the content/ directory.

Communication & support
- Use issues for technical discussions and design decisions.
- For sensitive matters or Code of Conduct incidents, follow CODE_OF_CONDUCT.md to contact maintainers privately.

Thanks — your contributions help make Travails of AEternum better!
