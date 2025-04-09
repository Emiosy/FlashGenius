# FlashGenius

FlashGenius is a web application that supports effective learning through automatic generation of educational flashcards using artificial intelligence. It solves the time-consuming problem of creating learning materials by enabling quick generation of high-quality flashcards for spaced repetition learning.

## Table of Contents
- [Project Description](#project-description)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Available Scripts](#available-scripts)
- [Project Scope](#project-scope)
- [Project Status](#project-status)
- [License](#license)

## Project Description

FlashGenius automates the process of creating educational flashcards while maintaining high-quality materials. The application enables effective learning through the use of a spaced repetition algorithm.

### Main Features:
- Generating flashcards with AI based on input text
- Independent generation of flashcards by AI on a selected topic
- Manual creation of flashcards
- Flashcard management (browsing, editing, deleting)
- Categorizing flashcards
- User account system
- Integration with a spaced repetition algorithm (SM-2)

## Tech Stack

### Frontend
- [Astro](https://astro.build/) v5.5.5 - framework for building fast web applications
- [React](https://react.dev/) v19.0.0 - library for building user interfaces
- [TypeScript](https://www.typescriptlang.org/) v5 - typed JavaScript
- [Tailwind CSS](https://tailwindcss.com/) v4.0.17 - utility-first CSS framework
- [Shadcn/ui](https://ui.shadcn.com/) - library of accessible React components

### Backend
- [Supabase](https://supabase.com/) - comprehensive backend solution:
  - PostgreSQL database
  - Built-in user authentication
  - SDK for multiple programming languages

### AI
- [Openrouter.ai](https://openrouter.ai/) - communication with AI models:
  - Access to various models (OpenAI, Anthropic, Google, and others)
  - Financial limit management for API keys

### CI/CD and Hosting
- GitHub Actions - CI/CD process automation
- DigitalOcean - application hosting using Docker containers

## Getting Started

### Requirements
- Node.js v22.14.0 (as specified in the `.nvmrc` file)
- npm (included with Node.js)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/your-organization/flashgenius.git
cd flashgenius
```

2. Install dependencies:
```bash
npm install
```

3. Run the development server:
```bash
npm run dev
```

4. The application will be available at `http://localhost:4321`

## Available Scripts

- `npm run dev` - Start the development server
- `npm run build` - Build the application for deployment
- `npm run preview` - Preview the built application
- `npm run astro` - Run the Astro CLI
- `npm run lint` - Run ESLint
- `npm run lint:fix` - Automatically fix problems detected by ESLint
- `npm run format` - Format code using Prettier

## Project Scope

### Included in MVP
- Generating flashcards with AI based on input text
- Generating flashcards with AI on a selected topic without source text
- Manual creation and management of flashcards
- User account system (registration, login, profile management)
- Flashcard categorization
- Basic integration with the SM-2 spaced repetition algorithm
- Basic security mechanisms (password hashing, HTTPS)

### Not Included in MVP
- Custom advanced spaced repetition algorithm
- Import of various document formats (PDF, DOCX)
- Sharing flashcard sets between users
- Integrations with other educational platforms
- Mobile applications
- Advanced flashcard formats (audio, video, code)
- Personalization of SM-2 algorithm parameters
- Advanced error logging system

## Project Status

The project is currently in the development phase. We are working on implementing the basic MVP functionalities.

## License

MIT
