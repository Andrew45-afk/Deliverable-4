# Part 6: Complete System Architecture Diagram

## Diagram

```mermaid
graph TB
    subgraph Users["Users (Coaches, Admins, Officials)"]
        Browser[Web Browser<br/>Plain HTML + JS]
    end

    subgraph Internet["Internet / CDN"]
        HTTPS[HTTPS / SSL]
    end

    subgraph Cloud["Cloud Hosting (VPS or PaaS)"]
        subgraph Web["Web Tier"]
            Nginx[Nginx Reverse Proxy]
            PHP[PHP 8.2 Application<br/>League/Team/Player/Game Logic]
        end

        subgraph App["Application Layer"]
            API[RESTful PHP Endpoints]
            Auth[Session + Role-Based Access]
        end

        subgraph Data["Data Layer"]
            MySQL[(MySQL 8.0<br/>player_management DB<br/>Tables: League, Team, Player, Game)]
        end

        Monitoring[Monitoring & Logging<br/>UptimeRobot + Log Files]
        Backup[Automated Backups]
    end

    subgraph Security["Security"]
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
