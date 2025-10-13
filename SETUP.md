# Setup Instructions for Animated GitHub Profile

## 🚀 Quick Setup Guide

### 1. Enable GitHub Actions
1. Go to your repository settings
2. Navigate to "Actions" > "General"
3. Make sure "Allow all actions and reusable workflows" is enabled

### 2. Repository Settings
- Make sure your repository is **public** (required for the snake animation to work)
- The repository name should be exactly your GitHub username: `Nabilaahmed2000`

### 3. Run the Workflow
1. Go to "Actions" tab in your repository
2. Find "Generate Snake Animation" workflow
3. Click "Run workflow" to trigger it manually
4. Wait for it to complete (usually takes 1-2 minutes)

### 4. Check the Output
- After the workflow completes, you should see a new branch called `output`
- This branch will contain the generated `snake.svg` file
- The snake animation will update automatically every day at midnight UTC

## 🎨 Customization Options

### Snake Animation Colors
You can customize the snake colors by modifying the workflow file:
```yaml
palette=github-light  # Light theme
palette=github-dark   # Dark theme (default)
palette=github        # Follows user preference
```

### Update Frequency
Currently set to daily. You can change the cron schedule:
```yaml
- cron: "0 0 * * *"     # Daily at midnight
- cron: "0 */12 * * *"  # Every 12 hours
- cron: "0 0 * * 1"     # Weekly on Monday
```

## 🐛 Troubleshooting

### Snake Not Showing?
1. Check if the workflow ran successfully
2. Verify the `output` branch exists
3. Make sure the repository is public
4. Check the image URL in your README

### Workflow Failed?
1. Check the Actions tab for error messages
2. Ensure you have the latest version of the workflow
3. Try running it manually again

## 📝 Additional Features

Your profile now includes:
- ✅ Animated typing header
- ✅ Animated contribution snake
- ✅ Enhanced GitHub stats with modern themes
- ✅ Professional contact badges
- ✅ Daily quote widget
- ✅ Organized project showcase
- ✅ Skill icons display

## 🔗 Useful Links

- [Snake Action Repository](https://github.com/Platane/snk)
- [GitHub README Stats](https://github.com/anuraghazra/github-readme-stats)
- [Skill Icons](https://skillicons.dev/)
- [Typing SVG](https://github.com/DenverCoder1/readme-typing-svg)

---

**Note:** After pushing these changes, wait a few minutes for GitHub to process the workflows, then check your profile!

## Permission fix applied

If your previous workflow run failed with a 403 when pushing to the `output` branch (error: "Permission to ... denied to github-actions[bot]"), we've applied two fixes in the workflows:

- The job now declares `permissions: contents: write` so the `GITHUB_TOKEN` has push rights.
- The gh-pages action now receives the token explicitly via `github_token: ${{ secrets.GITHUB_TOKEN }}`.

After this change, re-run the workflow (Actions → Generate Snake → Run workflow) or push a small commit to `main` to trigger it. Then check the `output` branch again for the generated SVG files.