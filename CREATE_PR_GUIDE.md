# Guide: Creating a Pull Request

## Current Status
✅ You're on branch: `setup-documentation-and-improvements`  
✅ You have 5 commits already  
⚠️  One file needs to be committed: `START_MYSQL_AND_POPULATE.md`  
⚠️  Remote points to original repo (not your fork)

---

## Step-by-Step Instructions

### Step 1: Commit the Remaining File

```bash
cd "/Users/richasawatkar/Desktop/Bandhu IIITDMJ/Bandhu"
git add START_MYSQL_AND_POPULATE.md
git commit -m "Add MySQL startup and data population guide"
```

---

### Step 2: Fork the Repository on GitHub

1. Go to: **https://github.com/bandhu-odisha/Bandhu**
2. Click the **"Fork"** button (top right)
3. Wait for GitHub to create your fork
4. Your fork will be at: `https://github.com/YOUR_USERNAME/Bandhu`

**Note:** Replace `YOUR_USERNAME` with your actual GitHub username.

---

### Step 3: Add Your Fork as a Remote

After forking, add your fork as a remote (replace `YOUR_USERNAME`):

```bash
git remote add fork https://github.com/YOUR_USERNAME/Bandhu.git
```

Verify it was added:
```bash
git remote -v
```

You should see:
- `origin` → points to `bandhu-odisha/Bandhu` (original)
- `fork` → points to `YOUR_USERNAME/Bandhu` (your fork)

---

### Step 4: Push Your Branch to Your Fork

```bash
git push fork setup-documentation-and-improvements
```

If this is the first push, GitHub might ask you to set upstream:
```bash
git push -u fork setup-documentation-and-improvements
```

---

### Step 5: Create Pull Request on GitHub

1. Go to your fork: `https://github.com/YOUR_USERNAME/Bandhu`
2. You'll see a yellow banner saying: **"setup-documentation-and-improvements had recent pushes"**
3. Click the **"Compare & pull request"** button
4. **OR** go directly to: `https://github.com/bandhu-odisha/Bandhu/compare/master...YOUR_USERNAME:setup-documentation-and-improvements`

5. Fill in the PR details:
   - **Title:** `Add setup documentation, People page improvements, and dummy data management`
   - **Description:** 
     ```
     ## Changes Made
     
     - Added comprehensive setup guide (SETUP_GUIDE.md) with Windows and macOS instructions
     - Created MySQL startup and data population guide (START_MYSQL_AND_POPULATE.md)
     - Improved People page design with:
       - Better spacing between cards
       - Hover effects (cards pop out on hover)
       - Active state highlighting for viewed profiles
       - Modern card design with smooth transitions
     - Added management command to create dummy data for People page
       - Supports 8 people with mix of males and females
       - Gender-based placeholder images (man.png/woman.png)
     - Updated templates to use gender-based placeholders
     
     ## Testing
     - Tested People page design improvements
     - Verified dummy data creation command works
     ```

6. Click **"Create pull request"**

---

## Quick Command Summary

```bash
# 1. Commit remaining file
git add START_MYSQL_AND_POPULATE.md
git commit -m "Add MySQL startup and data population guide"

# 2. Add your fork as remote (replace YOUR_USERNAME)
git remote add fork https://github.com/YOUR_USERNAME/Bandhu.git

# 3. Push to your fork
git push -u fork setup-documentation-and-improvements

# 4. Then create PR on GitHub (see Step 5 above)
```

---

## After Creating the PR

Once you create the PR, you'll get a link like:
**https://github.com/bandhu-odisha/Bandhu/pull/XXX**

Share this link with your seniors for review!

---

## Troubleshooting

### If you get "remote fork already exists":
```bash
git remote remove fork
git remote add fork https://github.com/YOUR_USERNAME/Bandhu.git
```

### If push is rejected:
```bash
# Make sure you're pushing to your fork, not origin
git push fork setup-documentation-and-improvements --force
# (Only use --force if you're sure, and only on your fork)
```

### If you need to update the PR later:
```bash
# Make changes, commit, then push again
git add .
git commit -m "Update description"
git push fork setup-documentation-and-improvements
# The PR will automatically update
```
