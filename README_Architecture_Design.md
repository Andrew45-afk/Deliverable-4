# Deliverable-4

## Part 4: Alternative Development Matrix

### Alternative Matrix – Custom Development Decision

| Criteria                        | Custom Development (Chosen) | Off-the-Shelf Software | SaaS Solution (e.g. TeamSnap) | Low-Code Platform | Open Source |
|---------------------------------|-----------------------------|------------------------|-------------------------------|-------------------|-------------|
| **Initial Cost**                | Low (Student team)          | Medium–High            | Low–Medium (Subscription)     | Low               | Low         |
| **Customization / Fit**         | Excellent (Exact match)     | Poor                   | Limited                       | Moderate          | Moderate    |
| **Time to Deploy**              | Medium                      | Fast                   | Very Fast                     | Fast              | Medium      |
| **Long-term Maintenance**       | Easy (Simple PHP stack)     | Difficult              | None (Vendor managed)         | Moderate          | Moderate    |
| **Security & Data Control**     | High (Full control)         | Medium                 | Low–Medium                    | Medium            | High        |
| **Scalability**                 | Good (Cloud + Docker)       | Limited                | Excellent                     | Good              | Good        |
| **Alignment with Requirements** | Excellent                   | Poor                   | Moderate                      | Moderate          | Moderate    |

### Narrative & Justification

After evaluating multiple development alternatives, our team selected **Custom Development** as the best approach for the **Player Management System**.

**Key Reasons:**

- **Perfect Fit for Requirements**: Our system has very specific needs (League, Team, Player, and Game management with custom reporting and workflows). Off-the-shelf and SaaS solutions do not fully support our exact data model and processes.

- **Low Long-Term Cost**: As a student team with a limited budget, building a simple PHP-based system allows us to avoid expensive licensing fees and recurring SaaS subscriptions.

- **Full Control & Security**: We retain complete ownership of our data and can implement security measures tailored to our needs (role-based access, input sanitization, etc.).

- **Easy Maintenance**: Using plain HTML + PHP (as decided in our tech stack) makes the system simple for our team to understand, update, and maintain throughout the semester and beyond.

- **Educational Value**: Custom development gives our team hands-on experience with the full software development lifecycle, which aligns with the goals of this IS436 course.

While SaaS solutions offer speed and low upfront cost, they lack the customization and data control we require. Off-the-shelf software would force us to change our processes to fit the tool rather than building the tool to fit our needs.

**Final Decision**: Custom Development is the most suitable approach for our Player Management System.

**Part 5: Architecture Diagram**
Our Player Management System is a web-based application for managing leagues, teams, players, and games. After evaluating the five architectural options against our four key non-functional requirements (99.5% uptime, fast dashboards, easy student maintenance, and low cost), we selected a Thin-Client / Cloud Computing hybrid architecture.

Why Thin-Client + Cloud is the best fit:

All business logic and data processing runs on the server (PHP), while the client is only plain HTML/CSS/JavaScript. This matches our “plain HTML + PHP” decision perfectly.
Cloud hosting (low-cost VPS or PaaS) gives us 99.5% uptime through managed infrastructure and easy scaling.
Dashboards load quickly because heavy queries and reporting run server-side with optimized MySQL.
Maintenance is extremely simple for a student team — just edit PHP files and push to Git. No complex client installations.
Cost stays under $10/month using student-friendly platforms (DigitalOcean, Render, or Hetzner).

How this architecture supports scalability:
The thin-client model allows us to scale horizontally by adding more web servers behind a load balancer in the future without changing client code. Cloud hosting makes this trivial and inexpensive.
Final Decision:
Thin-Client Cloud Architecture (PHP web application hosted on a low-cost cloud VPS or PaaS with Docker).
Trade-offs & Reasoning:

Trade-off: Slightly higher initial learning curve for Docker/cloud vs. pure local hosting.
Reason: Worth it for 99.5% uptime and future scalability.
Trade-off: Less “thick” offline capability.
Reason: Our system is primarily used online by league officials and coaches — offline access is not required.
We rejected pure Client-Based and Thick-Client because they fail on uptime and maintenance. Pure Server-Based (no cloud) cannot reliably meet 99.5% uptime on a student budget.

Hardware, Software & Programming Language Specification
Server Configuration

Hardware: 1–2 vCPU, 2–4 GB RAM (low-cost VPS or PaaS instance)
Operating System: Ubuntu 22.04 LTS (or Debian-based)
Web Server: Nginx or Apache
Application Server: PHP 8.2+ (FPM)
Database: MySQL 8.0 (Docker container in development, managed or same server in production)
Containerization: Docker + Docker Compose (already implemented)
CI/CD: GitHub Actions (existing repo)

Client Configuration

Hardware: Any modern device with a web browser (laptop, tablet, phone)
Software: Modern web browser (Chrome, Firefox, Edge, Safari)
Programming Languages & Technologies:
Frontend: Plain HTML5, CSS3, Vanilla JavaScript
Backend: PHP 8.2+
Database: MySQL 8.0 + SQL
Styling: Bootstrap 5 (CDN) for responsive design (optional but recommended for clean UI)

<img width="825" height="441" alt="image" src="https://github.com/user-attachments/assets/a24a078f-d6c0-4454-b73a-cf1ecf9e1de1" />
