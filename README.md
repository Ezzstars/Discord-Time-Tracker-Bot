# ==============================================
#   EZZSTAR OFFICE - TIME TRACKER BOT (README)
# ==============================================

# OVERVIEW:
# TimeTrackerBot is a Discord bot for Ezzstar Office that lets members
# check in/out, records their working hours, applies penalties for exceeding
# limits, sends DM reminders, and generates weekly Excel reports.

# ----------------------------------------------
# FEATURES
# ----------------------------------------------
# 1. Check-In / Check-Out Buttons
#    - Members click "Check In" or "Check Out" to record work sessions.
#    - Automatically logs time in the timing channel.

# 2. Automatic 5-Hour Limit
#    - Default session limit is 5 hours.
#    - After 5 hours, bot auto-checks out the user and applies a penalty.

# 3. Penalty System
#    - Example message:
#      ⚠️ Warning: auto-checked out after 5 hours.
#      💀 Penalty: 20,000 SPCA sent to burn wallet.
#      💡 Session counted: 5 h 0 m

# 4. Admin Control
#    - Admins can change limit, penalty, or reminder via command:
#      /update_limit hours:<number> penalty:<amount> reminder:<minutes_before>

# 5. DM Reminder
#    - Sent 30 minutes before auto-checkout:
#      ⏰ Hey @username!
#      You’ve been clocked in for 4 h 30 m.
#      You have 30 m left before auto-checkout applies a 20,000 SPCA penalty.
#      📍 Check-out channel: #clock-in
#      🏢 Server: Ezzstar Office
#      Please check out soon to avoid the penalty.

# 6. Weekly Reports
#    - Every Sunday, generates weekly_summary_YYYY_MM_DD.xlsx
#    - Automatically uploads to the #reports channel.

# 7. Anti-Cheat System
#    - Prevents fake or prolonged sessions.
#    - Automatically removes invalid session data.

# ----------------------------------------------
# SETUP INSTRUCTIONS
# ----------------------------------------------

# Step 1: Install Python 3.10+
# Download from https://www.python.org

# Step 2: Create project folder
cd Desktop
mkdir discord-time-bot
cd discord-time-bot

# Step 3: Create virtual environment
python -m venv .venv
.venv\Scripts\activate

# Step 4: Install dependencies
pip install discord.py python-dotenv pandas openpyxl

# Step 5: Create .env file and add your token
echo DISCORD_TOKEN=your_bot_token_here > .env

# Step 6: Edit channel IDs in time_tracker.py
# BUTTONS_CHANNEL_ID = your_button_channel_id
# TIMING_CHANNEL_ID  = your_timing_channel_id
# REPORTS_CHANNEL_ID = your_reports_channel_id

# Step 7: Run the bot
python time_tracker.py

# Expected output:
# ✅ Logged in as TimeTrackerBot | Synced 2 commands

# Step 8: Post the buttons in Discord
# Run this command inside your Discord server:
/post_buttons

# The bot will post:
# 🕒 Click below to Check In / Check Out
# 🟢 Check In
# 🔴 Check Out

# ----------------------------------------------
# EXAMPLES
# ----------------------------------------------

# Normal session:
# 🧑 Name: @Zoro
# ✅ Check in: 11:24 PM (1st Oct 2025)
# 🔴 Check out: 3:00 AM
# 💡 Session: 3 h 23 m

# Auto-checkout with penalty:
# 🧑 Name: @Zoro
# ✅ Check in: 10:42 PM (4th Nov 2025)
# ⚠️ Warning: auto-checked out after 5 hours.
# 💀 Penalty: 20,000 SPCA sent to burn wallet.
# 💡 Session counted: 5 h 0 m

# ----------------------------------------------
# ADMIN COMMANDS
# ----------------------------------------------

# /post_buttons
#   → Posts the check-in/check-out buttons

# /update_limit hours:<number> penalty:<amount> reminder:<minutes_before>
#   → Updates session limit, penalty amount, and reminder time

# Example:
# /update_limit hours:8 penalty:15000 reminder:45

# ----------------------------------------------
# WEEKLY REPORTS
# ----------------------------------------------

# Every Sunday night, bot generates a report:
# weekly_summary_YYYY_MM_DD.xlsx
# and uploads it to the #reports channel automatically.

# ----------------------------------------------
# TECH STACK
# ----------------------------------------------

# - Python 3.10+
# - discord.py
# - python-dotenv
# - pandas
# - openpyxl
# ----------------------------------------------

