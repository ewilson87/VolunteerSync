# VolunteerSyncEvan Wilson
# CST-451_452 Capstone Project
# Grand Canyon University
# Instructor: Professor Michael Landreth
# Revision: 6.0

VolunteerSync Capstone Project Portfolio Summary

VolunteerSync is a full-stack volunteer management platform, and the idea for it actually came from personal experience. I’ve been in the Navy for 18 years now, and I’ve done a lot of volunteering during that time, but I never really kept formal records. Like a lot of service members, it was always scattered emails, sign-in sheets, or more often than not, nothing at all. Later on, when I realized I needed that documentation to submit for the Military Outstanding Volunteer Service Medal, I realized how hard it is to go back and prove work you already did. That is why I decided to build VolunteerSync around verifiable volunteer records from the start.

At the same time, the idea also aligns closely with a Christian worldview, specifically the emphasis on service, stewardship, and helping others. That said, VolunteerSync is not a religious application and it is not limited to any specific belief system. The goal is simply to support and encourage service in a practical, inclusive way that works for anyone who wants to give back to their community.

At a high level, the platform connects volunteers with organizations and manages the entire lifecycle of a volunteer event. Organizers can register, submit their organization for approval, and once approved, create and manage events. Events have capacity limits, locations, dates, and tags. Volunteers can browse and search for events by things like date, location, organizer, or tags, sign up for opportunities they’re interested in, get reminders, and keep a running, verifiable record of their volunteer hours.

One of the core features is what happens after an event. Once an event is completed, organizers mark attendance directly in the system. After attendance is finalized, VolunteerSync generates a signed PDF certificate for each volunteer. Each certificate includes a unique verification ID that can be checked on a public verification page. That means schools, employers, or scholarship programs can verify the record instantly without needing to contact the organization, which makes the whole process cleaner and harder to fake.

From an architecture standpoint, the application follows a pretty straightforward three-tier design. The front end is an Angular single-page app, the backend is a REST API built with Node and Express, and everything is backed by a MySQL database. Each layer has a clear responsibility, which makes the system easier to maintain and extend.

On the front end, the app is built with Angular 19 and TypeScript. Everything is role-based, so Admins, Organizers, and Volunteers all see different dashboards and features, plus there’s a public Verifier view. Angular route guards are used to protect role-specific areas, and an HTTP interceptor automatically attaches JWT tokens to API requests so authentication stays centralized and consistent.

To keep the app responsive and reduce unnecessary API calls, the client uses query-key-based caching with a stale-while-revalidate pattern. That means data is reused when it’s still fresh, but quietly refreshed in the background when needed. The front end is broken into focused services like authentication, API access, caching, and validation, instead of having everything tangled together. Error handling is also structured, with clear pages for things like unauthorized access, forbidden requests, server errors, and not-found routes.

For the UI and reporting side, the front end uses Bootstrap and Bootstrap Icons for layout, RxJS for reactive data handling, Chart.js for dashboards and analytics, jsPDF for generating certificates, and xlsx for CSV and Excel exports. Angular SSR is used for server-side rendering, and testing and CI are handled with Jasmine, Karma, and GitHub Actions.

On the backend, VolunteerSync is a modular REST API built with Node.js, Express, and TypeScript. The codebase is split into clear layers. Routes define endpoints and wire middleware, controllers handle request and response logic, a DAO layer handles all database access and SQL, and shared services support things like email, logging, auditing, and metrics.

The API supports full CRUD for events, users, organizations, signups, attendance, certificates, tags, and support messages. It also includes approval workflows for organizations, tag and organization following, audit logs, and admin-level metrics. There are scheduled background jobs that handle things like hourly event reminders and daily cleanup tasks.

Security was treated as a priority throughout the project. Authentication is handled with JWTs and role claims, passwords are hashed with bcrypt, and all inputs are validated and sanitized. The API uses rate limiting, Helmet for security headers, properly configured CORS, centralized error handling, and safe handling of unhandled promise rejections. Logging is done with Winston using rotating log files, and the app can run over HTTPS with SSL certificates in a production setup.

Overall, VolunteerSync was built to be more than just a functional capstone project. The goal was to design something that reflects how a real-world, production-ready volunteer platform would actually be built. It demonstrates clean architecture, role-based security, performance awareness, and a real use case that comes directly from my own experience.

# GIT URLS:	

    Project Portfolio: https://github.com/ewilson87/VolunteerSync
    Back-end API: https://github.com/ewilson87/VolunteerSync-API/tree/main
    Front-end Angular: https://github.com/ewilson87/VolunteerSync-Angular-Frontend/tree/main

# Screencast URLS:	

    YouTube VolunteerSync Playlist (All Milestones): https://www.youtube.com/playlist?list=PLsicDUNz539oU69jqgdwGfWyBzUrsYafJ
    Milestone 3 (November 23rd, 2025): https://youtu.be/A95dBOsipZ4
    Milestone 4 (January 11th, 2026): https://youtu.be/_47rNvOhEIY
    Milestone 5 (January 25th, 2026): https://youtu.be/TtyhlmYfZcg
    Milestone 6 (February 3rd, 2026): https://youtu.be/KInZfGMCeVM
