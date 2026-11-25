# Team Management Starter Kit

A Laravel starter kit built on Livewire and the Flux UI that gives each user a personal team and full team-management capabilities. It is the official Laravel Livewire starter for prototyping multi-user apps with organizations, roles, invitations, and team-scoped routing.

## What it does

- **Authentication and teams** — Sign up, log in, and confirm email with optional two-factor authentication (TOTP and passkeys).
- **Personal teams** — Every user automatically gets a personal team they own. Teams are identified by a URL-friendly slug.
- **Team administration** — Create, rename, delete, and switch between teams; invite members by email; accept, cancel, and prune expired invitations; manage member roles and remove members.
- **Role and permission system** — Team roles (Owner, Admin, Member) with scoped permissions for updating the team, deleting it, adding/editing/removing members, and creating/canceling invitations.
- **Team-scoped routing** — Dashboard and settings live under a `{current_team}` slug, enforced by the `auth`, `verified`, and `EnsureTeamMembership` middleware.
- **Frontend stack** — Livewire 4, the Fluent UI (Flux) component set, Tailwind CSS, and Vite.

## Tech stack

- **Laravel 13** with **Fortify** for authentication, **Sanctum** for API tokens, **Tinker**
- **Livewire 4** + **Livewire Flux** for reactive server-side UI
- **Tailwind CSS** + **Vite**
- **PHP 8.3+**

## Key features at a glance

| Area | Details |
| --- | --- |
| Authentication | Login, registration, email verification, password reset, two-factor (TOTP + recovery codes), passkey enrollment/management |
| Organizations | Teams with names and slugs; each user owns a personal team; team memberships tracked in `team_members` |
| Collaboration | Invite members by email with an expiry code, accept/update/cancel invitations, remove members, edit team details |
| Permissions | Owner > Admin > Member with granular permissions for team and member actions |
| UI | Livewire components and Blade templates using Flux (Fluent UI) with dark mode |

## Project structure

```
app/
  Http/
    Controllers/        # Base controller
    Livewire/           # Livewire component class files
    Middleware/         # EnsureTeamMembership, SetTeamUrlDefaults
  Models/               # User, Team, Membership, TeamInvitation
  Concerns/             # HasTeams, GeneratesUniqueTeamSlugs, validation rules
  Enums/                # TeamRole, TeamPermission
  Data/                 # TeamPermissions, UserTeam (DTOs for team display)
database/
  migrations/           # Users, teams, team_members, team_invitations, current_team_id, 2FA, passkeys
  factories/            # User, Team, TeamInvitation factories (seeded with a personal team)
routes/
  web.php               # Home, dashboard under {current_team}, settings
  settings.php          # Settings Livewire routes
resources/views/
  pages/                # Livewire views: dashboard, teams (index, edit, and modals), settings
  layouts/              # App layout
  welcome.blade.php     # Landing page
tests/                  # Pest feature and unit tests
```

## Getting started

```bash
# 1. Install dependencies
composer install

# 2. Configure the environment
cp .env.example .env
php artisan key:generate

# 3. Run migrations
php artisan migrate

# 4. Build the frontend assets
npm install
npm run build
```

Then start the development server:

```bash
php artisan serve
```

Open `http://localhost:8000` in your browser. Register an account and you will automatically be assigned a personal team.

## Tests

```bash
php artisan test
```

The suite covers authentication flows, team creation and membership, team invitations and expiration, security settings, and password/email confirmation.

## Customization

- Add or change team permissions in `app/Enums/TeamPermission.php` and the permission checks in `app/Concerns/HasTeams.php`.
- Extend role behavior (assignable roles, levels, permissions) in `app/Enums/TeamRole.php`.
- Replace the default Livewire views in `resources/views/pages` to match your product.

## License

MIT
