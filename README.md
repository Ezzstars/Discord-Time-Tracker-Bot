🕒 Ezzstar Office — Time Tracker Bot
📘 Overview

TimeTrackerBot is a custom Discord bot built for the Ezzstar Office server to help team members record their daily work sessions.
Members simply Check In and Check Out using interactive buttons. The bot logs their working hours, applies penalties for exceeding limits, sends automatic reminders via DM, and even generates weekly Excel reports.

🚀 Features

✅ Check-In / Check-Out Buttons

Members click 🟢 Check In or 🔴 Check Out directly in Discord.

Automatically records timestamps and calculates total working hours.

✅ Automatic 5-Hour Limit

Default max session length is 5 hours.

If a user forgets to check out, the bot automatically ends the session and applies a penalty.

✅ Penalty System

Exceeding the limit results in:

⚠️ Warning: auto-checked out after 5 hours.  
💀 Penalty: 20,000 SPCA sent to burn wallet.  
💡 Session counted: 5 h 0 m


✅ Admin Commands

Server admins can adjust the session limit, penalty amount, or reminder time using:

/update_limit hours:<number> penalty:<amount> reminder:<minutes_before>


✅ DM Reminders

Members receive a private reminder 30 minutes before auto-checkout:

⏰ Hey @username!
You’ve been clocked in for 4 h 30 m.
You have 30 m left before auto-checkout applies a 20,000 SPCA penalty.
📍 Check-out channel: #clock-in
🏢 Server: Ezzstar Office
Please check out soon to avoid the penalty.


✅ Weekly Reports (Excel)

Every Sunday night, the bot automatically uploads a .xlsx report summarizing all sessions for the week.

✅ Anti-Cheat System

Prevents fake time entries.

Auto-removes sessions exceeding the configured limit.

⚙️ Setup Guide
1️⃣ Prerequisites

Python 3.10+

Discord Bot Token (from Discord Developer Portal
)

Discord.py library

2️⃣ Installation

Clone or copy the repository:

cd Desktop
mkdir discord-time-bot
cd discord-time-bot


Create a virtual environment:

python -m venv .venv
.venv\Scripts\activate


Install dependencies:

pip install discord.py python-dotenv pandas openpyxl

3️⃣ Environment Setup

Create a .env file inside the folder:

DISCORD_TOKEN=your_bot_token_here

4️⃣ Channel Configuration

Open the time_tracker.py file and update these constants:

BUTTONS_CHANNEL_ID = 111111111111111111   # Channel with Check In / Check Out buttons
TIMING_CHANNEL_ID = 222222222222222222   # Channel where time logs appear
REPORTS_CHANNEL_ID = 333333333333333333  # Channel for weekly Excel reports

5️⃣ Run the Bot
python time_tracker.py


If successful, you’ll see:

✅ Logged in as TimeTrackerBot | Synced 2 commands

6️⃣ Post the Buttons

In your Discord server, run:

/post_buttons


This will post a message with:

🟢 Check In
🔴 Check Out

🧠 Example Log Messages

✅ Normal Session:

🧑 Name: @Zoro  
✅ Check in: 11:24 PM (1st Oct 2025)  
🔴 Check out: 3:00 AM  
💡 Session: 3 h 23 m


⚠️ Auto-Checkout (Penalty):

🧑 Name: @Zoro  
✅ Check in: 10:42 PM (4th Nov 2025)  
⚠️ Warning: auto-checked out after 5 hours.  
💀 Penalty: 20,000 SPCA sent to burn wallet.  
💡 Session counted: 5 h 0 m

🛠 Admin Command Reference
Command	Description	Example
/post_buttons	Posts the check-in/out buttons	/post_buttons
/update_limit	Updates session limit, penalty, reminder	/update_limit hours:8 penalty:15000 reminder:45
📅 Auto Report Example

The bot creates weekly reports like:
weekly_summary_2025_11_09.xlsx
and automatically uploads them to your #reports channel.

🧩 Tech Stack

Language: Python

Libraries: discord.py, python-dotenv, pandas, openpyxl

Data Storage: Local JSON for sessions

Output: Excel reports (.xlsx)
