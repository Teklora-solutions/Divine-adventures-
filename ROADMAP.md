# Roadmap

## Current status

Devine Adventures is a Flask web application for discovering and booking adventure tours. The milestones below distinguish the existing application foundation from future work.

### Milestone 1: Project Foundation (Completed)

- [x] Establish the Flask application factory and configuration for development, production, and testing.
- [x] Add SQLAlchemy models for users, operators, tours, bookings, payments, waitlists, and reviews.
- [x] Build the shared page templates and responsive static assets.
- [x] Add the root README, proprietary license, and changelog.

### Milestone 2: Core Features (In Progress)

- [x] Provide traveler registration, login, tour browsing, booking, and account dashboards.
- [x] Provide operator booking management and guest check-in tools.
- [x] Provide admin tools for tours, users, bookings, reviews, community photos, and shop items.
- [x] Implement review moderation, operator responses, and scheduled review-request processing.
- [ ] Complete and verify production payment-provider configuration and end-to-end payment flows.
- [ ] Connect contact-form submissions to a configured email delivery service.
- [ ] Add automated tests for booking, payment, and role-based workflows.

### Milestone 3: Production Readiness (Planned)

- [ ] Replace development defaults and demo account seeding with secure, environment-managed setup.
- [ ] Add and document repeatable database migrations for supported database engines.
- [ ] Document operational monitoring, backup, and recovery procedures.
- [ ] Review accessibility, security, and deployment configuration before production releases.
