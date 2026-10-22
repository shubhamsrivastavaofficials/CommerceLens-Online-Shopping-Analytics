# GitHub and Vercel deployment

CommerceLens is a static site. `index.html` is in the project root, so the app can be hosted without a framework build step. Vercel supports importing a GitHub repository and automatically deploying later branch updates. See the official [Vercel deployment guide](https://vercel.com/docs/deployments) and [Vercel for GitHub guide](https://vercel.com/docs/git/vercel-for-github).

## Prepare the repository

1. Create a GitHub repository for CommerceLens.
2. Put the contents of this project folder at the repository root. Confirm `index.html` is at the top level.
3. Keep the included sample data clearly marked as generated. Do not add private customer data, passwords, or API keys to a public repository.

## Connect it to Vercel

1. In Vercel, choose **New Project** and import the GitHub repository.
2. Set the project root to the repository root. For this plain static site, choose the no-framework/other option if Vercel asks for a framework; no build command is needed, and the output is the root folder containing `index.html`.
3. Deploy, then open the Vercel URL and check that the dashboard loads and the sample CSV import works.

After Git integration is connected, Vercel can create deployments from repository changes. The application itself has no backend or environment variables. Before making a repository public, review the files and confirm that the sample data is the only data included.
