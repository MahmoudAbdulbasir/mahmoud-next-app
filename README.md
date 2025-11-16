##  Deployment

This application is deployed on Vercel:  

**Live URL:**
https://mahmoudabdulbassir-next-app.vercel.app/

**Deployment Steps:**

1. Push code to the GitHub repository.
2. GitHub Actions triggers CI/CD workflow on `main` branch.
3. Workflow installs dependencies, runs tests, builds the app, and deploys to Vercel automatically.
4. The Vercel project uses the following secrets in GitHub Actions:
   - `VERCEL_TOKEN`
   - `VERCEL_ORG_ID`
   - `VERCEL_PROJECT_ID`

-----------------------------------------------------------------------------------------------------------

##  CI/CD Workflow

- Workflow file: `.github/workflows/ci-cd.yml`  
- Trigger: push to `main` branch or pull requests  
- Steps:
  1. Checkout code
  2. Install dependencies
  3. Run tests (`npm test --if-present`)
  4. Build Next.js app
  5. Deploy to Vercel (production environment)

------------------------------------------------------------------------------------------------------------

##  Challenges & Solutions

1. **SSL certificate errors (`SELF_SIGNED_CERT_IN_CHAIN`)**  
   - Solved by configuring npm to use system CA certificates or using `npx` instead of global install.

2. **GitHub authentication for push**  
   - Solved by using a Personal Access Token (PAT) for HTTPS authentication.

3. **Vercel Project ID / Org ID not visible**  
   - Solved by running `npx vercel projects ls` after logging in via Vercel CLI.

4. **Global npm permission errors**  
   - Solved using `sudo` or `npx` to bypass global install.

