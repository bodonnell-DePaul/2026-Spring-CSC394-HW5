# Homework 4: Authenticated Persistent Full-Stack App

**CSC 436 - Web Applications - DePaul University**

**Due: Wednesday 5/6 @ 11:59pm**

---

## Overview

Build a small authenticated full-stack application using **React**, **ASP.NET Core**, and **Entity Framework Core**.

Your app should help a specific kind of user save, organize, or personalize information from a real dataset. You will choose at least one of the data sources listed below, design an application around it, and build a working flow where the React frontend, ASP.NET Core backend, authentication system, and database all work together.

This assignment is intentionally outcome-based. You are not being given an exact schema, exact API design, exact component structure, or exact UI layout. You are responsible for making those decisions and using GitHub Copilot thoughtfully as an assistant.

---

## Learning goals

By the end of this assignment, you should be able to:

- Create a React frontend that communicates with a backend API.
- Create an ASP.NET Core backend that exposes protected endpoints.
- Use Entity Framework Core to store durable application data.
- Design related data instead of relying on one flat list.
- Add authentication and protect both frontend routes and backend data.
- Integrate a public dataset into a user-centered application.
- Review, adapt, and debug AI-generated code instead of accepting it blindly.

---

## Core idea

Your app must combine two kinds of data:

1. **External reference data** from one public dataset or API.
2. **User-owned application data** stored in your own database.

For example, if you use a book API, the book records may come from Open Library, but your app should store each user's reading list, notes, ratings, statuses, or saved collections in your own database.

The external dataset gives your app real content. Your database stores what your users do with that content.

---

## Choose one data source

Choose one of the following public data sources. You may use the source through live API calls, by downloading data and importing a useful subset into your database, or by combining both approaches.

You do not need to use every field from the dataset. Choose the fields that support your app's purpose.

| Option | Data source | Access | Possible app ideas |
| --- | --- | --- | --- |
| 1 | **Open Library** | API, JSON | Reading tracker, course reading planner, book club organizer, personal library |
| 2 | **The Metropolitan Museum of Art Collection** | API, JSON | Museum visit planner, art collection favorites, exhibit curator, art study journal |
| 3 | **Open-Meteo** | API, JSON | Weather-aware activity planner, campus commute planner, outdoor habit tracker, local weather journal |
| 4 | **Chicago Data Portal** | API, JSON, CSV downloads | Neighborhood resource explorer, food inspection tracker, public facility finder, city data dashboard |
| 5 | **REST Countries** | API, JSON | Travel planner, country comparison dashboard, study abroad shortlist, geography study tool |

### Option 1: Open Library

Use this if you want an app about books, authors, reading, classes, recommendations, or collections.

- Main site: `https://openlibrary.org/`
- API docs: `https://openlibrary.org/developers/api`
- Example search: `https://openlibrary.org/search.json?q=web+development`

Possible user-owned data:

- Saved books.
- Reading status.
- Personal notes.
- Ratings.
- Book club lists.
- Course reading plans.

### Option 2: The Metropolitan Museum of Art Collection

Use this if you want an app about art, exhibits, museums, history, culture, images, or curation.

- API docs: `https://metmuseum.github.io/`
- Example search: `https://collectionapi.metmuseum.org/public/collection/v1/search?q=van%20gogh`
- Example object: `https://collectionapi.metmuseum.org/public/collection/v1/objects/436535`

Possible user-owned data:

- Favorite artworks.
- Planned museum visits.
- Curated collections.
- Study notes.
- Exhibit themes.
- Reflection entries.

### Option 3: Open-Meteo

Use this if you want an app about weather, planning, habits, commuting, activities, or local conditions.

- API docs: `https://open-meteo.com/en/docs`
- Example forecast: `https://api.open-meteo.com/v1/forecast?latitude=41.8781&longitude=-87.6298&hourly=temperature_2m,precipitation_probability`
- Image note: Open-Meteo does not provide content images. If you choose this source, include relevant images from another free source, such as your own photos, public-domain weather icons, or properly attributed freely licensed images.

Possible user-owned data:

- Saved locations.
- Activity plans.
- Weather-based reminders.
- Outdoor habit logs.
- Commute notes.
- Daily observations.

### Option 4: Chicago Data Portal

Use this if you want an app about Chicago neighborhoods, public services, inspections, facilities, transportation, community resources, or local data.

- Main portal: `https://data.cityofchicago.org/`
- API docs: `https://dev.socrata.com/`
- Example dataset: Chicago food inspections, `https://data.cityofchicago.org/resource/4ijn-s7e5.json`
- Image note: Many Chicago datasets are text or location based. If your chosen dataset does not include images, include relevant images from another free source, such as your own photos, public-domain icons, or properly attributed freely licensed images.

Possible user-owned data:

- Saved places.
- Neighborhood watchlists.
- Inspection notes.
- Favorite public resources.
- Comparison dashboards.
- Personal ratings or reminders.

### Option 5: REST Countries

Use this if you want an app about countries, travel, geography, languages, regions, or study abroad planning.

- API docs: `https://restcountries.com/`
- Example all countries: `https://restcountries.com/v3.1/all`
- Example search: `https://restcountries.com/v3.1/name/japan`

Possible user-owned data:

- Saved countries.
- Travel plans.
- Country comparison lists.
- Study notes.
- Region-based collections.
- Personal rankings or tags.

---

## Required behavior

Your app must prove that the full stack works together.

Your app must include:

- A public page that does not require sign-in.
- A protected area that does require sign-in.
- A way to register or use demo accounts.
- A way to sign in and sign out.
- At least one protected React route.
- At least one protected ASP.NET Core API endpoint.
- Data stored with Entity Framework Core.
- At least one relationship between durable records.
- At least one flow where a logged-in user creates or updates data from the React UI.
- Data that remains available after a browser refresh.
- Data that remains available after the backend restarts.
- Meaningful images displayed in the site.
- A UI state for loading data.
- A UI state for empty results.
- A UI state for API or validation errors.

You choose the theme, entities, fields, route names, endpoint design, components, and visual style.

---

## Authentication and authorization expectations

Your app must have authentication, but authentication alone is not enough.

Your backend should know which user is making a request. A signed-in user should only be able to view or modify data they are allowed to access.

Your app should demonstrate:

- Signed-out users cannot access protected app screens.
- Signed-out users cannot call protected data endpoints successfully.
- Signed-in users can create or update their own data.
- One user's private saved data is not exposed to another user.

Frontend route guards are required, but they are not a replacement for backend protection. The backend API must enforce the important rules.

---

## Data and persistence expectations

Your database should store your application's own data, not just a copy of the public dataset.

Your EF Core model should include:

- A user-related concept.
- At least one user-owned record.
- At least one related record.
- At least one status, category, tag, date, note, rating, or progress-like field.

Examples:

- A user saves books from Open Library into reading lists.
- A user groups museum objects into personal collections.
- A user saves locations and activity plans based on weather data.
- A user tracks Chicago places and adds personal notes.
- A user builds country shortlists and records study-abroad research.

Do not build a one-table app. Your app should have enough structure that relationships matter.

---

## External data integration expectations

Your app must integrate one public data source from the list above.

Acceptable approaches:

- Fetch from the external API when the user searches or views details.
- Download a dataset file and import a useful subset into your database.
- Seed your database with selected records from the dataset.
- Store references to external records, then save user-specific notes, statuses, ratings, or collections locally.
- Display images that support your app's theme, either from the chosen dataset or from another appropriate free source.

Your app should make it clear which data came from the external source and which data belongs to the signed-in user.

You do not need to mirror an entire public dataset. Smaller, thoughtful integration is better than importing thousands of records you do not use.

If your chosen dataset includes image URLs, use them meaningfully. If it does not, you may use your own images, public-domain images, public-domain icons, or freely licensed images that are appropriate for your theme. Do not use random copyrighted images from the web.

---

## Technical expectations

Use:

- React for the frontend.
- ASP.NET Core for the backend.
- Entity Framework Core for database access.
- SQLite or another instructor-approved relational database for local development.

Your frontend and backend may run as separate local development processes. The frontend should call the backend over HTTP.

Your repository should include enough instructions for someone else to run your project locally.

---

## Design note

Include a short design note in your repository. This may be part of your README.

Answer:

- Which data source did you choose?
- Who is your app for?
- What problem does your app solve?
- What external data does your app use?
- What user-owned data does your app store?
- Which records are related?
- Where do the images in your app come from?
- Which screens or actions require sign-in?
- How does your app prevent users from accessing someone else's private data?

Keep this concise. The goal is to explain your design choices clearly.

---

## AI use

You may use GitHub Copilot.

You are responsible for the final code. Generated code must be reviewed, tested, and changed when it does not fit your app.

Include a short AI reflection in your repository. Answer:

- What are three ways Copilot helped you?
- What is one suggestion you changed or rejected?
- What is one place where you checked for an authentication, authorization, or data-modeling issue?
- What is one bug, mismatch, or incomplete feature you had to fix after using AI?

---

## Suggested development path

This is not a required sequence, but it may help:

1. Choose a data source and app idea.
2. Sketch the user-owned data your app needs.
3. Create the ASP.NET Core backend and EF Core model.
4. Add authentication.
5. Protect at least one backend endpoint.
6. Create the React frontend.
7. Add route guarding in React.
8. Connect React to the backend.
9. Integrate the external dataset.
10. Add validation, loading states, empty states, and error states.
11. Test with at least two users.
12. Write run instructions and your AI reflection.

---

## Demo expectations

Be prepared to demonstrate:

1. Open a public page while signed out.
2. Attempt to access a protected page while signed out.
3. Register or sign in.
4. Search, load, or display data from your chosen public data source.
5. Show meaningful images in the app.
6. Create or update user-owned data from the React UI.
7. Refresh the browser and show that the data remains.
8. Restart the backend and show that the data remains.
9. Sign out and show that protected data is blocked.
10. Explain one relationship in your EF Core model.
11. Explain how the backend prevents one user from accessing another user's private data.

---

## Submission requirements

Submit your GitHub repository link on D2L.

Your repository should include:

- React frontend source code.
- ASP.NET Core backend source code.
- EF Core model and migrations.
- Instructions for preparing the database.
- Instructions for running the backend.
- Instructions for running the frontend.
- Demo account or seed-data instructions.
- A short design note.
- A short AI reflection.

Do not commit secrets, API keys, passwords, generated build folders, dependency folders, or local database files that should not be shared.

---

## Grading rubric

| Criteria | Points |
| --- | ---: |
| Clear app concept, chosen data source, and design note | 10 |
| External data integration is useful and visible in the app | 10 |
| React frontend includes protected routes and data-driven screens | 15 |
| ASP.NET Core backend exposes useful protected API endpoints | 15 |
| Authentication and authorization work correctly | 20 |
| EF Core persistence includes related durable records | 15 |
| Complete React-to-API-to-database flow works | 5 |
| Site uses meaningful images appropriately | 5 |
| AI reflection shows thoughtful review of generated code | 5 |
| **Total** | **100** |

### Possible deductions

- App does not run from the submitted instructions.
- Data only exists in React state.
- Backend uses in-memory collections instead of EF Core for required durable data.
- Protected data endpoints are accessible while signed out.
- One user can access another user's private records.
- No meaningful integration with the chosen external dataset.
- No meaningful images included in the site.
- No EF Core migrations or database setup path.
- Missing design note or AI reflection.

---

## Final reminder

Your goal is not to build the biggest possible app. Your goal is to build a small, coherent app where authentication, authorization, external data, React, ASP.NET Core, and EF Core all work together.
