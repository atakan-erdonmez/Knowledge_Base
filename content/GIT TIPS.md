---
created: 2026-03-30T09:43
updated: 2026-05-12T10:06
---
Format: `<type>(scope): <description>`.

| **Type**     | **When to use it**                                                    | **Example**                                      |
| ------------ | --------------------------------------------------------------------- | ------------------------------------------------ |
| **feat**     | Adding a new service or feature.                                      | `feat(nginx): add reverse proxy for qnap nas`    |
| **fix**      | Fixing a bug or broken config.                                        | `fix(pve): update websocket headers for console` |
| **chore**    | Maintenance (updates, folder cleanup).                                | `chore(ansible): update galaxy requirements`     |
| **docs**     | Documentation changes only.                                           | `docs(readme): add networking diagram`           |
| **ci**       | Changes to your GitHub Actions/Pipelines.                             | `ci(github): add linting for yaml files`         |
| **refactor** | You didn't just add a feature, you improved the underlying structure. |                                                  |
