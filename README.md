## Forkify – Modern Recipe Finder & Manager

Forkify is a single-page recipe application that lets you search thousands of recipes, view detailed cooking instructions, adjust servings, bookmark favorites, and even upload your own recipes. This version has been modernized with a minimalist UI, dark mode support, and a clean ES6+ codebase.

---

### Key Features

- **Powerful Recipe Search**  
  - Search recipes by ingredient or dish name using a public REST API.  
  - Shows a clean list of results with active state highlighting for the selected recipe.

- **Pagination for Large Result Sets**  
  - Results are split across multiple pages for better performance and UX.  
  - Next/Previous controls are dynamically rendered based on the current page and total results.

- **Interactive Recipe View**  
  - Detailed recipe panel with image, cooking time, servings, and full ingredients list.  
  - Servings can be increased or decreased, and ingredient quantities update automatically.

- **Custom Recipe Uploads**  
  - Modal form to upload your own recipes with validation on ingredient format.  
  - Uploaded recipes are persisted via the API and appear like any other recipe in the app.

- **Bookmarking & Persistence**  
  - Bookmark favorite recipes and access them quickly from the header dropdown.  
  - Bookmarks are stored in `localStorage`, so they survive page reloads.

- **Modern UI & Dark Mode**  
  - Clean, minimalist layout built with SASS and CSS variables.  
  - Built‑in light/dark theme toggle with the current theme stored in `localStorage`.

---

### Tech Stack

- **Vanilla JavaScript (ES6+)** – Application logic, state management, and view updates.  
- **SASS (SCSS)** – Componentized styling, variables, mixins, and theming support.  
- **Parcel** – Zero‑config bundler for JS, SASS, and asset pipelines.  
- **MVC Architecture** – Clear separation of concerns between data, UI, and orchestration.

---

### Architecture – Why MVC?

- **Model** (`model.js`)  
  - Owns the central application `state` (recipe, search, bookmarks).  
  - Handles all data fetching (AJAX calls), transformation, pagination, and persistence to `localStorage`.  
  - Exposes small, focused functions (`loadRecipe`, `loadSearchResults`, `updateServings`, `addBookmark`, `uploadRecipe`, etc.) that are easy to test and reason about.

- **Views** (`src/js/views/*.js`)  
  - Each UI section (recipe, results, bookmarks, pagination, search, upload) has its own view class.  
  - Views are responsible only for DOM rendering and DOM event binding, not business logic.  
  - A shared base `View` class encapsulates rendering, diffing, spinners, and error messages.

- **Controller** (`controller.js`)  
  - Acts as the mediator between Model and Views.  
  - Responds to user events from the views, calls model methods, and triggers the appropriate view updates.  
  - Centralizes the application flow (loading recipes, handling searches, pagination, bookmarking, recipe uploads, and theme initialization).

Using MVC here keeps the codebase **modular, testable, and easier to extend** (for example, adding new views or enhancing existing ones without touching the data layer).

---

### Getting Started

#### 1. Install Dependencies

```bash
npm install
```

#### 2. Run the Development Server

```bash
npm start
```

Parcel will start a local development server and open the app in your default browser. Any changes to JS or SASS files will trigger automatic rebuilds and live reloads.

#### 3. Build for Production (Optional)

```bash
npm run build
```

This creates an optimized production build (bundled, minified, and asset‑processed) in the `dist` folder.

---

### What I Learned

This project was a major step in **mastering asynchronous JavaScript and real‑world API integration**:

- Working with `async/await`, Promises, error handling, and timeouts around network calls.  
- Designing a **state‑driven architecture** where the UI reacts to changes in a central `state` object.  
- Integrating with a third‑party REST API, transforming raw responses into a clean internal data model.  
- Persisting user data (bookmarks, theme preference) with `localStorage`.  
- Structuring a modern front‑end app using **MVC**, ES6 modules, and a professional bundler (Parcel).

Overall, this repository reflects my journey from basic JS to building a fully structured, production‑ready front‑end project.
