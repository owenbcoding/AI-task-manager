# Project Roadmap

Checklist for turning the Laravel Livewire team manager starter into a finished product.

## Setup & verification
- [x] Generate the README describing the project
- [x] Add a checklist/TODO file documenting the project
- [ ] Verify the README renders correctly (review content, headings, lists)

## Authentication
- [ ] Confirm login, registration, and password reset routes and views work
- [ ] Confirm email verification requires the email to be marked verified
- [ ] Confirm two-factor authentication (TOTP + recovery codes) can be enrolled and used
- [ ] Confirm passkey enrollment and management work end-to-end

## Teams
- [ ] Confirm a user always starts with a personal team after registration
- [ ] Confirm users can create, rename, and delete teams
- [ ] Confirm team slugs are unique and derived from the team name
- [ ] Confirm team-scoped routing works (dashboard and settings under the team slug)
- [ ] Confirm switching between teams updates the current team

## Members & invitations
- [ ] Confirm invited users can accept an invitation by code
- [ ] Confirm invitations can be cancelled by the owner/admin
- [ ] Confirm daily scheduled cleanup deletes expired invitations
- [ ] Confirm team members have roles (Owner, Admin, Member) with correct permissions
- [ ] Confirm permissions gate the correct actions (add/remove members, edit team, delete team)

## Frontend
- [ ] Confirm the dashboard renders correctly
- [ ] Confirm dark/light mode toggles work
- [ ] Confirm all team management modals render and submit correctly

## Tests
- [ ] Run the full test suite (`php artisan test`) and confirm all pass
- [ ] Add or update feature tests for team creation, invitations, and permission enforcement

## Polish
- [ ] Add a favicon and branding
- [ ] Add a default blank state when a team has no content yet
- [ ] Polish responsive behavior (mobile navigation, modals)
