# Fantasy Dashboard v2

A comprehensive fantasy football analytics dashboard built with Vue 3, TypeScript, and Tailwind CSS.

## Features

- **Standings**: League standings with all-play records, divisions, and AI-generated league news
- **Power Rankings**: Advanced power rankings with historical tracking and trend charts
- **Matchups**: Head-to-head matchup cards with projections and historical comparisons
- **History**: Career statistics and championship history
- **Draft**: Draft grades and analysis with team-by-team breakdowns

## Setup Instructions

### 1. Install Dependencies

```bash
npm install
```

### 2. Set Up Environment Variables

Copy `.env.example` to `.env`:

```bash
cp .env.example .env
```

Then add your OpenAI API key to `.env`:

```
VITE_OPENAI_API_KEY=your-actual-api-key-here
```

### 3. Run Development Server

```bash
npm run dev
```

The app will be available at `http://localhost:5173`

### 4. Build for Production

```bash
npm run build
```

The built files will be in the `dist/` folder.

## Deploying to GitHub Pages

### Step 1: Update Base URL

In `vite.config.ts`, update the base path to match your GitHub repo name:

```ts
export default defineConfig({
  base: '/your-repo-name/'
})
```

### Step 2: Build

```bash
npm run build
```

### Step 3: Deploy

You can use GitHub Actions or manually push the `dist` folder to the `gh-pages` branch.

**Using GitHub Actions** (recommended):

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Node
        uses: actions/setup-node@v3
        with:
          node-version: '18'
          
      - name: Install dependencies
        run: npm install
        
      - name: Build
        run: npm run build
        
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

## Setting Up the Serverless Backend (for AI Features)

The AI-generated content requires a serverless function to keep your OpenAI API key secure.

### Option 1: Vercel (Recommended)

1. Install Vercel CLI: `npm i -g vercel`
2. Create `api/generate.ts` in your project root (see documentation)
3. Run `vercel` to deploy
4. Add your OpenAI key to Vercel environment variables

### Option 2: Netlify Functions

1. Create `netlify/functions/generate.ts`
2. Deploy to Netlify
3. Add environment variables in Netlify dashboard

## Project Structure

```
src/
├── components/     # Reusable Vue components
├── views/          # Page components (Standings, Power Rankings, etc.)
├── stores/         # Pinia state management
├── services/       # API services (Sleeper, OpenAI)
├── types/          # TypeScript type definitions
├── router/         # Vue Router configuration
└── assets/         # Static assets
```

## Technologies

- **Vue 3** - Progressive JavaScript framework
- **TypeScript** - Type-safe JavaScript
- **Tailwind CSS** - Utility-first CSS framework
- **Pinia** - State management
- **ApexCharts** - Interactive charts
- **Vite** - Build tool

## Contributing

Feel free to submit issues or pull requests!

## License

MIT
