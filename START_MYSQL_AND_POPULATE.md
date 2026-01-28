# Quick Guide: Start MySQL and Populate Dummy Data

## Step 1: Start MySQL Server

You have MySQL installed at `/usr/local/mysql/bin`. Start it using one of these methods:

### Option A: Using System Preferences (Easiest)
1. Open **System Preferences** (or **System Settings** on newer macOS)
2. Look for **MySQL** in the list
3. Click **Start MySQL Server**

### Option B: Using Command Line
```bash
# Source your profile to get MySQL in PATH
source ~/.zprofile

# Start MySQL server
sudo /usr/local/mysql/support-files/mysql.server start
```

### Option C: If MySQL is installed via Homebrew
```bash
brew services start mysql
```

---

## Step 2: Verify MySQL is Running

```bash
source ~/.zprofile
mysql -u root -p
# Enter your MySQL root password when prompted
# You should see: mysql> prompt
# Type: EXIT; to leave
```

---

## Step 3: Activate Virtual Environment and Run the Command

```bash
# Navigate to project directory
cd "/Users/richasawatkar/Desktop/Bandhu IIITDMJ/Bandhu"

# Activate virtual environment
source venv/bin/activate

# Run the management command to create dummy data
python manage.py create_dummy_people
```

You should see output like:
```
Creating dummy data for People's page...
Created designation: Core Team
Created: Sanjeeb Mohapatra
Created: Rajendra Badapanda
...
✅ Successfully created 9 people
```

---

## Step 4: Start Django Development Server

```bash
# Make sure you're in the project directory with venv activated
python manage.py runserver
```

---

## Step 5: View the People's Page

1. Open your browser
2. Go to: **http://127.0.0.1:8000/people/**
3. You should see all 9 people with their cards
4. Cards should be uniform in height
5. Profile images should show `man.png` placeholder (since all are male)

---

## Step 6: Access Admin Portal (Optional)

1. Go to: **http://127.0.0.1:8000/admin/**
2. Login with your superuser credentials
3. You can see/edit:
   - **Designations** → "Core Team"
   - **Profiles** → All 9 profiles
   - **Staffs** → All 9 staff members
   - **Peoples designations** → Links between staff and designations

---

## Troubleshooting

### If MySQL won't start:
```bash
# Check if MySQL process is already running
sudo /usr/local/mysql/support-files/mysql.server status

# Stop and restart
sudo /usr/local/mysql/support-files/mysql.server stop
sudo /usr/local/mysql/support-files/mysql.server start
```

### If you get "Can't connect to MySQL" error:
- Make sure MySQL server is actually running (check System Preferences)
- Verify your `.env` file has correct database credentials
- Try restarting MySQL server

### If the command says "User already exists":
- The command will skip existing users
- This is normal if you run it multiple times
- To start fresh, you can delete existing users from the admin portal

---

## What Was Created?

✅ **1 Designation**: "Core Team"  
✅ **9 Users** with email addresses  
✅ **9 Profiles** with gender, profession, contact info  
✅ **9 Staff** records linked to profiles  
✅ **9 PeoplesDesignation** records linking staff to "Core Team"

All profiles have `profile_pic=None`, so they'll automatically use `man.png` or `woman.png` from the static folder based on gender.
