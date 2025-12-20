---
name: deploy
description: Deploy the application to staging or production
allowed-tools: Bash, Read, Glob, Grep, TodoWrite
---

# Deployment Assistant

You are helping the user deploy their application safely.

## Pre-Deployment Checklist

Before deploying, verify:

### 1. Code Quality
- [ ] All tests passing (`npm test` or equivalent)
- [ ] No linting errors (`npm run lint`)
- [ ] TypeScript compiles without errors (if applicable)
- [ ] Build succeeds (`npm run build`)

### 2. Git Status
- [ ] Working directory is clean (no uncommitted changes)
- [ ] On correct branch (main/master for production)
- [ ] Branch is up to date with remote

### 3. Environment
- [ ] Environment variables are set
- [ ] Secrets are configured in deployment platform
- [ ] Database migrations are ready (if any)

## Deployment Targets

### Vercel
```bash
# Preview deployment
vercel

# Production deployment
vercel --prod
```

### Railway
```bash
railway up
```

### Docker
```bash
# Build image
docker build -t [app-name]:latest .

# Push to registry
docker push [registry]/[app-name]:latest
```

### AWS (via CDK/SAM)
```bash
# Deploy to AWS
cdk deploy
# or
sam deploy
```

### Custom Script
```bash
# If deploy script exists
npm run deploy
# or
./scripts/deploy.sh
```

## Process

### Step 1: Pre-flight Checks
Run all checks from the checklist above. Stop if any fail.

### Step 2: Confirm Target
Ask user to confirm:
- Deployment target (staging/production)
- Expected changes

### Step 3: Deploy
Execute the appropriate deployment command.

### Step 4: Verify
After deployment:
- Check deployment logs for errors
- Verify the app is accessible
- Run smoke tests if available

### Step 5: Report
```
DEPLOYMENT COMPLETE
===================
Target:      [staging/production]
URL:         [deployment URL]
Commit:      [git SHA]
Duration:    [time]
Status:      ✓ Success

Post-deploy:
- [ ] Verify app loads correctly
- [ ] Check critical user flows
- [ ] Monitor error tracking (Sentry, etc.)
```

## Options

- `/deploy` - Deploy to default environment
- `/deploy staging` - Deploy to staging
- `/deploy production` - Deploy to production (with extra confirmations)
- `/deploy --dry-run` - Show what would be deployed without deploying

## Safety Features

- Always runs tests before production deployment
- Requires explicit confirmation for production
- Shows diff of changes being deployed
- Provides rollback instructions if deployment fails
