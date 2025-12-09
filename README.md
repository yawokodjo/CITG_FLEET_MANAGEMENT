# CITG Fleet Management

Lightweight fleet management application for CITG — backend API + frontend. This repository contains the API and frontend projects plus helpful tooling (Docker compose, Adminer, composer lock, etc.) to get you started quickly.

> Note: This README was generated from the repository layout (fleet-mgt-api, fleet-mgt-frontend, docker-compose.yml, adminer.php, composer files). If you want this committed to the repository, tell me and I can push it for you.

## Table of contents

- About
- Features (planned / typical)
- Repository structure
- Requirements
- Quick start (Docker)
- Manual setup (developer flow)
  - API
  - Frontend
  - Database
- Environment variables (example)
- Useful files
- Development tips
- Contributing
- License
- Contact

## About

CITG Fleet Management is an application for managing vehicles, drivers, assignments, maintenance records and related fleet operations. The repo splits responsibilities into two sub-projects:

- fleet-mgt-api — backend API (PHP / Composer-based)
- fleet-mgt-frontend — frontend (JS-based, PostCSS indicated)

The repo includes a docker-compose.yml for local development and adminer.php for quick DB access.

## Features (typical)

- CRUD for vehicles, drivers and assignments
- Vehicle maintenance & inspection records
- User authentication and roles (admin, dispatcher, driver)
- Search and filtering of vehicles and assignments
- Simple reporting and export capability

(Your actual features may vary; update this list to match the implemented functionality.)

## Repository structure

- .gitignore
- docker-compose.yml — development / local orchestration
- adminer.php — DB administration single-file tool (Adminer)
- composer.json / composer.lock — PHP dependencies for the API
- fleet-mgt-api/ — backend project (PHP)
- fleet-mgt-frontend/ — frontend project (JS/CSS)
- vendor/ — PHP vendor (tracked here currently) — consider adding to .gitignore if you prefer not to track vendor

## Requirements

- Docker & Docker Compose (recommended for local development)
- PHP 8.x (if running the API outside of Docker)
- Composer (for PHP dependency management)
- Node.js & npm / yarn (for frontend, if running outside Docker)

## Quick start (recommended — Docker)

1. Copy or create an .env file for services if necessary (see Environment variables below).
2. Build and start services:
   - docker-compose up --build
3. Visit the frontend in your browser (address depends on docker-compose ports; commonly http://localhost:3000 or http://localhost:8080).
4. Use Adminer to inspect the database:
   - If adminer is served as a container or adminer.php is in the web root, open the corresponding URL and connect using the DB credentials in your .env or docker-compose.

Stopping and removing containers:
- docker-compose down

Notes:
- docker-compose.yml in this repo contains the developer orchestration; open it to see exact service names and ports.

## Manual setup (developer flow)

If you prefer not to use Docker, follow these developer steps.

API (fleet-mgt-api)
1. cd fleet-mgt-api
2. composer install
3. copy .env.example to .env and configure DB credentials and other environment values
4. Run migrations / seeders if your project includes them (framework-specific). Example (Laravel-like):
   - php artisan migrate --seed
   If using a different framework, run the appropriate setup commands.

Frontend (fleet-mgt-frontend)
1. cd fleet-mgt-frontend
2. npm install (or yarn)
3. configure environment variables (e.g., REACT_APP_API_URL or VITE_API_URL)
4. Start dev server:
   - npm run dev
   or build for production:
   - npm run build

Database
- Create the database with the name configured in your .env file.
- Run migrations and seeders (if available).
- Use adminer.php or Adminer container to browse and manage the DB.

## Example environment variables

API (.env)
- DB_CONNECTION=mysql
- DB_HOST=127.0.0.1
- DB_PORT=3306
- DB_DATABASE=fleet_db
- DB_USERNAME=fleet_user
- DB_PASSWORD=secret
- APP_URL=http://localhost:8000
- APP_ENV=local

Frontend (.env or framework-specific)
- VITE_API_URL=http://localhost:8000/api
- NODE_ENV=development
- PORT=3000

Adjust values to match your docker-compose or hosting environment.

## Useful files

- docker-compose.yml — local development stack (services, ports, volumes)
- adminer.php — single-file DB admin interface (drop into a PHP server or use with Docker)
- composer.json / composer.lock — backend dependencies and versions

## Development tips

- Keep the vendor/ directory out of Git unless you have a reason to commit dependencies; add vendor/ to .gitignore and use composer install in CI.
- Add a README inside fleet-mgt-api and fleet-mgt-frontend describing project-specific commands (migrations, seeds, tests, scripts).
- Add automated tests and a CI workflow (GitHub Actions) to run tests on PRs.

## Contributing

1. Fork the repository
2. Create a branch: git checkout -b feature/your-feature
3. Make your changes and add tests where appropriate
4. Push your branch and open a Pull Request describing the change
5. Ensure CI passes and address review comments

If you’d like, open issues for planned features or bugs before implementation.

## License

Specify a license for the repository. If you want MIT, add an MIT license file. (No license file found in the repo yet — add one to make reuse clear.)

## Contact

Maintainer: yawokodjo  
Repository: https://github.com/yawokodjo/CITG_FLEET_MANAGEMENT

---

If you'd like, I can:
- Commit this README.md into the repository on a new branch and open a PR (I can push if you tell me to and provide the repo owner/confirm).
- Generate README files for the fleet-mgt-api and fleet-mgt-frontend subprojects with concrete commands based on their contents.
- Inspect docker-compose.yml and produce exact service names, ports, and a tailored "Quick start" section. Tell me which of these you want next.
