# Snapp

If you're seeking a self-hosted URL shortening solution, Snapp might be what you need. It's designed for those who value control over their URL management and want to explore various technologies.

## A Brief Introduction

This project began as a personal endeavor to explore new technologies and make use of free time. With version 0.7, some development issues emerged, prompting a complete redesign and rebuild. By version 0.8, we've laid the groundwork for what will become the first version 1.

Currently, you can migrate URLs between versions using a CSV export tool. Note that these files are only valid for direct transitions from one version to the next; for example, exports from version 0.6 to 0.7 won't work for moving from 0.7 to 0.8. We’ve reverted to using Prisma to ensure a more stable and maintainable platform going forward.

This latest version supports multiple architectures, including ARM and ARM64 platforms, and offers integration with various databases, now accessible with just a ENV Variable.

## Features

- **Intuitive User Interface:** Snapp offers a user-friendly interface for easy link shortening.
- **Secure Authentication:** Enjoy secure sessions for your user. Their information is protected.
- **Custom Short Codes:** Personalize your short codes to make your links memorable and easy to share.
- **Expiration Dates:** Manage link lifespans with expiration dates. You can set expiry dates for added security or let links remain active indefinitely.
- **Secret Links:** Enhance security with secret links, allowing you to share with a select audience using unique secrets.
- **Usage Analytics:** Access detailed, anonymous analytics for your links. Snapp provides insights into link engagements.
- **Extended Metrics:** Integrate Snapp with your self-hosted or cloud-based Umami Analytics for advanced metrics.
- **URL Reputation Check:** Ensure the safety of links with VirusTotal API reputation checks.
- **REST API:** Community-requested REST API endpoints enable remote management of your Snapp instance. Find all Swagger Docs [here](https://snapp.li/dashboard/docs).

## Getting Started

Snapp is an open-source platform you can host yourself.

### Testing Version 0.8

For the 0.8 version, you’ll need to migrate URLs using the CSV Exporter. Here’s a sample configuration:

```yml
services:
  snapp:
    image: uraniadev/snapp:0.8
    ports:
      - 3000:3000
    environment:
      DATABASE_URL: 'file:./db.sqlite'
      DATABASE_PROVIDER: sqlite # mysql | sqlite | pg
      TOKEN_SECRET: # openssl rand -base64 32
      ORIGIN: https://example.com
```

**Note**: SQLite database is located in /app/prisma/{DATABASE_URL} if you want to mount it


## Default Admin Authentication

If ENV variables ADMIN_USERNAME and ADMIN_PASSWORD are not set it defaults to the very secure. 
You can always set a SMTP server and use password recovery process to change it later. (not very secure...)


```
  username: admin
  password: password

```

## I18N

Snapp at his version 0.8 includes from start Italian, English, German, French, Spanish and Galician. This are very amateurish translation with the help of ChatGPT, so errors are to be expected, feel free to open a related issue if any

## Migration

The latest versions of Snapp include CSV Export to facilitate migration. Simply log in and import your URLs from the dashboard, and continue from where you left.

## The Stack

The technology involved:

- Svelte Kit
- Prisma
- Lucia Auth
- Tailwind CSS
- MaxMind
- Phosphor Icons
- SwaggerUI
- AMCharts
- ChartJS
