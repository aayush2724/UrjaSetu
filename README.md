# UrjaSetu ☀️

**An Indian rooftop solar planning and energy intelligence platform.**

UrjaSetu aims to help Indian households make informed decisions about rooftop solar by combining solar generation estimates, electricity tariff calculations, government subsidies, appliance-level energy planning, and weather-aware scheduling.

Instead of presenting a single optimistic savings estimate, UrjaSetu is designed to explain what a solar installation could realistically generate, how much it could save, and which assumptions influence the result.

> **Status:** Under development. Features described below are planned unless explicitly implemented.

## The Problem

Choosing a rooftop solar system involves more than estimating sunlight. Households need to understand electricity tariffs, subsidy eligibility, seasonal generation, appliance consumption, and the financial value of exported electricity.

UrjaSetu aims to bring these factors together in one transparent planning experience.

## Planned Features

- **Solar generation planner:** Estimate monthly generation for 1 kW, 2 kW, and 3 kW rooftop solar systems, including low, expected, and high scenarios.
- **Electricity bill intelligence:** Model state-specific tariffs, fixed charges, surcharges, taxes, billing periods, and applicable free-unit schemes.
- **Savings and payback analysis:** Compare estimated bills with and without solar, including installation costs, subsidies, and export credits.
- **Appliance coverage:** Explain which household appliances solar generation can support and estimate their electricity consumption.
- **Subsidy and metering guidance:** Represent applicable central and state subsidies, metering policies, and export rates.
- **Weather-aware scheduling:** Recommend suitable time windows for shiftable appliances using solar generation forecasts.
- **Transparent estimates:** Distinguish verified tariff data from estimates and expose uncertainty instead of presenting uncertain calculations as exact.
- **Privacy-conscious accounts:** Support authenticated users, saved sites, consent management, and personal data export and deletion.

## Initial Scope

The first end-to-end implementation will focus on **Karnataka**, starting with Bengaluru and BESCOM.

The architecture is intended to support expansion across Indian states and electricity distribution companies (DISCOMs).

## Planned Architecture

UrjaSetu will begin as a modular monolith built with Java and Spring Boot.

### Technology Stack

| Component | Technology |
|---|---|
| Language | Java 25 |
| Backend framework | Spring Boot 4.1.x |
| Build tool | Apache Maven |
| Architecture | Spring Modulith |
| Database | PostgreSQL |
| Database migrations | Flyway |
| Solar generation planning | PVGIS API |
| Weather-aware scheduling | Open-Meteo API |
| Testing | JUnit, Mockito, WireMock, Testcontainers |
| Infrastructure | Docker Compose |
| Continuous integration | GitHub Actions |

Technology versions and external service compatibility will be verified during implementation.

### Application Modules

The planned module boundaries are:

- `tariff`: Pure Java electricity bill calculation engine.
- `tariffdata`: Tariff configuration, validation, versioning, and source tracking.
- `geo`: PIN-code, location, and DISCOM resolution.
- `solar`: Monthly rooftop solar generation estimates.
- `policy`: Subsidies and metering rules.
- `appliance`: Appliance catalogue and energy consumption modelling.
- `planner`: Solar sizing, savings, and payback calculations.
- `user`: Authentication, saved sites, consent, and privacy.
- `forecast`: Weather and hourly solar irradiance forecasts.
- `scheduler`: Appliance scheduling and daily plan generation.
- `notification`: Email and Telegram notifications.

The tariff engine will be developed and tested independently of Spring and the database before being integrated into the application.

## Design Principles

1. **Accuracy over optimistic promises:** Show ranges and assumptions when estimates are uncertain.
2. **Versioned rules:** Associate tariff schedules with their sources and effective dates.
3. **Testable business logic:** Keep core calculations independent of infrastructure wherever practical.
4. **Idempotent background jobs:** Prevent duplicate daily plans and notifications.
5. **Efficient external API usage:** Cache forecasts and share requests across users in the same geographic grid cell.
6. **Privacy by design:** Minimize location data and enforce ownership checks on user resources.
7. **Incremental development:** Build, test, and commit each milestone before proceeding.

## Development Roadmap

| Milestone | Objective | Status |
|---|---|---|
| 0 | Project skeleton, configuration, Docker Compose, and CI | ⏳ Planned |
| 1 | Basic electricity tariff engine | ⏳ Planned |
| 2 | Complex tariff rules and boundary testing | ⏳ Planned |
| 3 | Versioned tariff data and database integration | ⏳ Planned |
| 4 | PIN-code and DISCOM resolution | ⏳ Planned |
| 5 | Monthly solar generation estimates | ⏳ Planned |
| 6 | Subsidies and metering policies | ⏳ Planned |
| 7 | Appliance catalogue and consumption calibration | ⏳ Planned |
| 8 | First working solar planner API | ⏳ Planned |
| 9 | Authentication, saved sites, and privacy | ⏳ Planned |
| 10 | Weather-aware scheduling and notifications | ⏳ Planned |
| 11 | Frontend, deployment, health checks, and documentation | ⏳ Planned |

Status key: ✅ Done · 🚧 In progress · ⏳ Planned

The initial implementation will prioritize a reliable, testable core over adding every state and feature at once.

## Getting Started

The project skeleton has not been created yet. Build, test, and run instructions will be added with Milestone 0.

The planned development prerequisites are:

- Java 25 JDK
- Apache Maven 3.9+
- Docker Engine with Docker Compose

## Accuracy and Data Sources

Solar generation estimates are planned to use PVGIS long-term generation data, while the scheduler will use Open-Meteo forecasts.

Tariff calculations will be based on documented regulatory schedules and their effective dates. Unverified policies and assumptions will remain explicitly marked as estimates or drafts until validated against authoritative sources.

The accuracy of predictions will depend on input quality, local weather, system losses, appliance usage, metering arrangements, and applicable electricity tariffs.

## Project Goal

Build an explainable solar planning platform that helps Indian households answer three practical questions:

1. How much electricity could my rooftop solar system generate throughout the year?
2. How much could I realistically save under my electricity tariff and subsidy eligibility?
3. When should I run my appliances to make better use of available solar energy?

**UrjaSetu: Bridging homes to smarter energy.**

