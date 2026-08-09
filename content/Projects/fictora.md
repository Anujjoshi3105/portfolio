---
publish: true
title: "Fictora"
status: Completed
category: Full Stack
description: Fictora is an entertainment discovery platform built with Next.js and the TMDB API, offering a rich interface to explore movies with detailed info, search, theming, and responsive design. Future updates will expand content to anime (Jikan API) and books (Google Books API), evolving into an all-in-one hub for media enthusiasts.
start: 2024-02-10
end: 2024-04-10
tags:
  - Next.js
  - Shadcn
  - TMDB
url: https://fictora.netlify.app/
created: 2025-06-07T22:39
github: https://github.com/Anujjoshi3105/fictora
thumbnail: _assets/fictora.png
updated: 2026-04-12T19:01
slug: fictora
---

> A unified, data-enriched platform for discovering movies, anime, and booksâ€”designed for the modern media explorer.

> Fictora combines entertainment discovery with responsive frontend engineering and real-time APIs to create a seamless, personalized user experienceâ€”one thatâ€™s scalable, accessible, and content-rich.

## **Introduction**

**Fictora** is an interactive discovery platform that unites **movies**, **TV shows**, **anime**, and **books** under one immersive interface. Initially developed with a focus on movies via the TMDB API, the project is expanding to include data from **Jikan** (anime) and **Google Books** APIs.

The platform is modular, fast, and designed with long-term content scalability in mind. Whether youâ€™re a movie buff, anime fan, or bookworm, Fictora curates and contextualizes content from across formats.

ðŸŒ [Live Site](https://fictora.netlify.app/)â€ƒâ€ƒðŸ”— [GitHub Repo](https://github.com/anujjoshi3105/fictora)

  

![[fictora.png]]

## **Problem Statement**

Modern content discovery is fragmented across platforms. Each formatâ€”movies, anime, booksâ€”has separate ecosystems with inconsistent UX and limited personalization.

- Users juggle multiple apps for content exploration
- Cross-format recommendation is nearly absent
- Minimal personalization or feedback loops
- Limited consideration of UI accessibility and theming

> Fictora addresses these issues by providing a unified, theme-aware, and extensible discovery engine that adapts to the user's content preferences.

## **Technical Stack**

|Layer|Technologies|
|---|---|
|Frontend|React (Next.js App Router), TypeScript|
|Styling|Tailwind CSS, Responsive Theming|
|Forms & UX|Context API, Planned Redux integration|
|Animations|Framer Motion|
|APIs|TMDB (active), Jikan & Google Books (planned)|
|Deployment|Vercel|

## **Architecture & Design Highlights**

- **Modular Page Architecture**: Pages and layouts follow Next.js App Router convention for flexibility
- **Client-Side State Management**: Lightweight context-based flow for responsiveness and performance
- **Search with Auto-complete**: Real-time results powered by TMDBâ€™s search endpoints
- **Theme-aware Design**: Light and dark modes with system preference compatibility
- **Zero Authentication**: Read-only browsing experience, scalable for future user auth and personalization

## **Core Features**

### **ðŸŽ¬ Movie Discovery Interface**

- Pulls trending, popular, and search-based results
- Detailed views for cast, ratings, trailers, genres, and more

### **ðŸ”Ž Search-Driven Navigation**

- Autocomplete interface with debounced API hits
- Instant redirection to detailed content pages

### **ðŸ“± Responsive and Accessible UI**

- Built mobile-first with Tailwind CSS utilities
- Keyboard-friendly and theming-compliant

### **ðŸŒ API-First Expansion Plan**

- TMDB fully integrated
- Jikan (anime) and Google Books (novels) in pipeline
- Unified interface for multi-format exploration

![[image.png]]

## **Planned Enhancements**

|Feature|Status|Description|
|---|---|---|
|Anime Integration|ðŸš§ In Progress|Jikan API-based anime search, season updates, and character data|
|Book Integration|ðŸ”œ Planned|Author bios, review scores, and recommendations via Google Books|
|TV Shows|ðŸ”œ Planned|Episode tracking and air date highlights|
|User Profiles|ðŸ”œ Planned|Watchlists, history, and favorites|
|Recommendation Engine|ðŸ”œ Planned|Personalized suggestions based on activity|
|Reviews & Ratings|ðŸ”œ Planned|User-submitted feedback on content|
|Social Sharing|ðŸ”œ Planned|Share titles with summaries and posters|
|Multi-language Support|ðŸ”œ Planned|i18n layer for global accessibility|
|PWA Support|ðŸ§ª Research|Offline caching and installability|

## **Scalability Considerations**

- Stateless rendering for performance
- Lazy-load image handling via Next.js
- Isolated data adapters for each content type
- Responsive grid and card-based layout architecture

## **Folder Structure**

```
fictora/
â”œâ”€â”€ app/                   // Next.js App Router structure
â”‚   â”œâ”€â”€ layout.tsx        // Root layout
â”‚   â”œâ”€â”€ page.tsx          // Landing
â”‚   â”œâ”€â”€ search/           // Search UI
â”‚   â”œâ”€â”€ movie/            // Dynamic movie pages
â”œâ”€â”€ components/           // Reusable UI elements
â”œâ”€â”€ lib/                  // API handlers, utility functions
â”œâ”€â”€ styles/               // Tailwind config and globals
â”œâ”€â”€ public/               // Static assets
â””â”€â”€ types/                // TypeScript interfaces
```

## **Development Process**

Fictora was built with performance-first principles and extensibility as the core directive:

- **Next.js App Router**: Modular routing and layout inheritance
- **API Abstraction Layer**: Centralized TMDB functions for easy replacement
- **Tailwind CSS**: Clean utility-first styling and theme toggling
- **Framer Motion**: Subtle interface animations for smooth user experience
- **TypeScript Everywhere**: Type-safe API consumption and prop management

## **Impact & Vision**

âœ… Provides a content discovery experience that bridges media formats  
âœ… Lightweight and performant even on mobile networks  
âœ… Zero-login exploration to reduce friction  
âœ… Architecture supports plug-and-play integration for future APIs

> Fictora is more than a movie viewer. Itâ€™s the starting point of a unified entertainment discovery ecosystemâ€”built for scale, personalization, and accessibility.

## **Contributing & Future Use**

This project is open to contributions in both development and API integration. Ideal areas for contribution:

- Integration of anime and book APIs
- UI/UX polish, accessibility audits
- Backend setup for user persistence (watchlists, ratings)
- ML-powered recommendation engine design

> For collaborations or extension into research/ed-tech, contact Anuj Joshi.

## Related

- [[projects/bitlog|BITLOG]] â€” a developer-focused blog platform on the same Next.js stack.
- [[projects/nicogauge|NicoGauge]] â€” another Next.js project with interactive, data-driven UI.
- [[projects/ekalavya|Ekalavya]] â€” full-stack Next.js SaaS with real-time features.
