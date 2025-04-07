# 🤖 SupportBot | Your Modern Telegram Support Bridge 🌉

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-nd/4.0/)
[![Python Version](https://img.shields.io/badge/Python-3.6%2B-blue?logo=python)](https://www.python.org/)
[![Telegram Bot API](https://img.shields.io/badge/Telegram%20API-pyTelegramBotAPI-blue.svg)](https://github.com/eternnoir/pyTelegramBotAPI)
[![Repo Status](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![Made by MasterShayan](https://img.shields.io/badge/Made%20by-%40MasterShayan-success?style=flat-square)](https://github.com/MasterShayan)
[![GitHub repo size](https://img.shields.io/github/repo-size/MasterShayan/SupportBot?style=flat-square)](https://github.com/MasterShayan/SupportBot)
[![GitHub last commit](https://img.shields.io/github/last-commit/MasterShayan/SupportBot?style=flat-square)](https://github.com/MasterShayan/SupportBot/commits/main)

**A modern and efficient communication bridge between your Telegram users and your support team!**

This project provides a feature-rich Telegram bot designed to handle support requests seamlessly. Built with Python and the `pyTelegramBotAPI` library, it allows users to easily send messages, which are then forwarded to administrators. Admins can reply directly through the bot, manage users, broadcast messages, and much more.

---

## ✨ Key Features

* **Effortless User Communication:** Users simply send their messages to the bot, and they get instantly forwarded to the admin(s).
* **Admin Reply System:**
    * Direct replies by using Telegram's native reply feature on the forwarded message.
    * Use the "📝 Quick Reply" inline button for a streamlined response flow.
* **Advanced Admin Panel (`/admin`):**
    * 📬 **Broadcast Message:** Send messages to all active bot users.
    * ⚡️ **Bot Status:** Toggle the bot On/Off for regular users.
    * 📊 **Bot Stats:** View total user count and the number of blocked users.
    * 🗄️ **User Management:** View a list of users, their status (Active/Blocked), and manage them individually (Block/Unblock) using interactive inline keyboards.
* **User Blocking:** Admins can block problematic users. Blocked users cannot interact with the bot.
* **Persistent Storage:** Utilizes simple text files (`.txt`) to store the user list, blocked users, bot status, and reply modes (no external database needed).
* **Automatic File Setup:** Required data files are automatically created on the first run if they don't exist.
* **User-Friendly Design:** Leverages Telegram's Reply and Inline keyboards for an intuitive admin experience.

---

## 🚀 Installation & Setup

Follow these steps to get your SupportBot up and running:

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/MasterShayan/SupportBot.git
    cd SupportBot
    ```

2.  **Install Dependencies:**
    Ensure you have Python 3.6+ installed. Then, install the required library:
    ```bash
    pip install pyTelegramBotAPI
    ```
    *(Optional but recommended: Use a Python virtual environment (`venv`))*
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    pip install pyTelegramBotAPI
    ```

3.  **Configure the Bot:**
    * Open the `bot.py` file (or your main script file).
    * **Bot Token:** Talk to [BotFather](https://t.me/BotFather) on Telegram, create a new bot, and get its API token. Replace `'token'` in the `API_KEY = 'token'` line with your actual bot token.
    * **Admin ID(s):** Find the numeric Telegram User ID(s) for the admin account(s). You can use bots like [@userinfobot](https://t.me/userinfobot). Place the numeric ID(s) inside the `{}` in the `ADMIN_IDS = {123}` line. For multiple admins, separate the IDs with commas (e.g., `ADMIN_IDS = {12345678, 98765432}`).

    ```python
    # Example configuration in bot.py
    API_KEY = '1111111111:AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA' # Replace with your bot token
    ADMIN_IDS = {123456789} # Replace with your admin numeric ID(s)
    ```
    
4.  **Run the Bot:**
    Start the bot script using:
    ```bash
    python bot.py
    ```
    Your bot should now be online and responding to messages!

---

## 🛠️ How to Use

### 👤 For Regular Users:

* **`/start`**: Initiates interaction with the bot and displays a welcome message. Adds the user to the users list if not already present.
* **`/help`**: Shows a brief guide on how to contact support.
* **Sending Messages:** Users just need to send any text message. It will be forwarded to the admin(s), and the user will receive a confirmation.

### 👑 For Admins:

* **`/admin`**: Accesses the main admin panel with core functions (Broadcast, Bot Status, Stats, User Management) via a reply keyboard.
* **Replying to Users:** Simply use Telegram's "Reply" feature on the message forwarded from the user. Your reply will be sent directly back to them.
* **Broadcasting:** Tap the "📬 Broadcast Message" button, then send the message you want to broadcast to all users.
* **Changing Bot Status:** Tap the "⚡️ Bot Status: ..." button to toggle the bot between On and Off for regular users.
* **Viewing Stats:** Tap the "📊 Bot Stats" button.
* **Managing Users:** Tap the "🗄️ User Management" button. You'll see a list of users and their status. Clicking on a user reveals Block/Unblock buttons.
* **Using Inline Buttons:**
    * **📝 Quick Reply:** Appears below a forwarded user message. Click it to enter reply mode specifically for that user without needing to use Telegram's native reply.
    * **🚫 Block User / ✅ Unblock User:** Quickly block or unblock a user directly from their forwarded message or within the User Management section.
* **Canceling Actions:** If you're in broadcast or quick reply mode, you can usually cancel by tapping the "Cancel Reply" button (if available in the reply keyboard for that mode) or sometimes by sending another command.

---

## 📁 File Structure

The bot uses simple text files for data persistence, created automatically in the same directory as the script:

* `bot_status.txt`: Stores the current status of the bot (`on` or `off`).
* `reply_mode.txt`: Manages the admin's current reply context (e.g., 'broadcast' or the user ID for a 'quick reply').
* `users.txt`: Contains a list of numeric user IDs of everyone who has started the bot (one ID per line).
* `blocked_users.txt`: Contains a list of numeric user IDs for users who have been blocked by an admin.

---

## 📜 License

This project is licensed under the **Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International (CC BY-NC-ND 4.0)** License.

[![License: CC BY-NC-ND 4.0](https://licensebuttons.net/l/by-nc-nd/4.0/88x31.png)](https://creativecommons.org/licenses/by-nc-nd/4.0/)

* **Attribution (BY):** You must give appropriate credit to the original creator (@MasterShayan).
* **NonCommercial (NC):** You may not use the material for commercial purposes.
* **NoDerivatives (ND):** If you remix, transform, or build upon the material, you may not distribute the modified material.

---

## 🙏 Acknowledgements

Developed with  ❤️ by **[@MasterShayan](https://github.com/MasterShayan)**

This bot has been crafted with care to streamline the support process, making communication efficient and manageable.

---

**Happy supporting!** ✨
