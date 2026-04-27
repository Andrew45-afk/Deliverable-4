# Part 6: Complete System Architecture Diagram

## System Architecture Diagram

```mermaid
graph TB
    subgraph Users["Users (Coaches, Admins, Officials)"]
        Browser[Web Browser<br/>Plain HTML + JS]
    end

    subgraph "Internet / CDN"
        HTTPS[HTTPS / SSL]
    end

    subgraph "Cloud Hosting (VPS or PaaS)"
        subgraph WebTier["Web Tier"]
            Nginx[Nginx Reverse Proxy]
            PHP[PHP 8.2 Application<br/>League/Team/Player/Game Logic]
        end

        subgraph AppLayer["Application Layer"]
            API[RESTful PHP Endpoints]
            Auth[Session + Role-Based Access]
        end

        subgraph DataLayer["Data Layer"]
            MySQL[(MySQL 8.0<br/>player_management DB<br/>Tables: League, Team, Player, Game)]
        end

        Monitoring[Monitoring & Logging<br/>UptimeRobot + Log Files]
        Backup[Automated Backups]
    end

    subgraph "Security"
        Firewall[Cloud Firewall]
        WAF[Basic WAF / Input Sanitization]
    end

    Browser --> HTTPS
    HTTPS --> Nginx
    Nginx --> PHP
    PHP --> API
    API --> Auth
    Auth --> MySQL
    MySQL --> Backup
    PHP --> Monitoring
    Nginx --> Firewall
    Firewall --> WAF
Component Explanation

Frontend: Plain HTML5, CSS3, and Vanilla JavaScript running in the user’s browser.
Web Server: Nginx acts as a reverse proxy.
Application Layer: PHP 8.2 handles all business logic, reporting, and RESTful API endpoints.
Database: MySQL 8.0 (player_management database) containing League, Team, Player, and Game tables.
Security: HTTPS encryption, session-based authentication with role-based access control, input sanitization, and cloud firewall.
Monitoring & Logging: UptimeRobot (free tier) for 99.5% uptime monitoring + server log files.
Backup: Automated daily database backups.
Deployment: Docker containers with GitHub Actions for CI/CD.

This architecture supports fast dashboard loading, easy maintenance by the student team, low cost, and 99.5% uptime through cloud hosting.
