# Putting Open Door on Hugging Face: step by step

**Time:** about 30–45 minutes. **Cost:** free.
**What you'll end up with:**
1. A **private dataset** (the locked filing cabinet) where the logs are saved every 5 minutes.
2. A **public Space** (the loading dock door): the live notice page that agents can visit.

**Golden rule:** never paste a token, password, or secret into a chat with any AI, including this one. You'll paste them
only into Hugging Face's own settings pages, and keep a copy in your password manager or Notes.

Wherever you see `YOURNAME`, use your Hugging Face username exactly as it appears in your profile URL.

---

## Step 1: Create a Hugging Face account (skip if you have one)

1. Go to **https://huggingface.co/join** and sign up.
2. Confirm your email (Hugging Face sends a link).
3. Note your **username**. It's in your profile URL: `https://huggingface.co/YOURNAME`.
4. Optional but recommended: turn on two-factor login under **Settings → Authentication**.

## Step 2: Make two secret values on your Mac

Open **Terminal**, paste this line, and press Return:

```
python3 -c "import secrets; print('ADMIN_TOKEN =', secrets.token_urlsafe(24)); print('IP_SALT     =', secrets.token_hex(16))"
```

It prints two random strings. Copy both into your password manager or Notes:
- **ADMIN_TOKEN** is the password for your private admin page. You'll need it to read confessions.
- **IP_SALT** is the secret ingredient that scrambles visitor addresses. You only paste it once, in Step 5.

## Step 3: Create the private log dataset (the filing cabinet)

1. Go to **https://huggingface.co/new-dataset**.
2. **Owner:** you. **Dataset name:** `open-door-logs`.
3. **Visibility: Private.** This matters: the logs must not be public.
4. Click **Create dataset**. It's fine that it's empty.

## Step 4: Create an access token for the Space (a key that opens only that cabinet)

1. Go to **https://huggingface.co/settings/tokens** and click **Create new token**.
2. **Token type: Fine-grained.** **Name:** `open-door-space`.
3. Under **Repositories permissions**, search for and select `YOURNAME/open-door-logs`.
   Tick **"Write access to contents/settings of selected repos"**.
4. Leave **everything else unticked.**
5. Click **Create token**, then **copy it now**. Hugging Face shows it only once. Keep it in Notes for Step 5.

## Step 5: Create the Space (the loading dock door)

1. Go to **https://huggingface.co/new-space**.
2. **Owner:** you. **Space name:** `open-door`. **License:** `mit` is fine.
3. **Select the Space SDK: Docker**, then the **Blank** template.
4. **Space hardware: CPU basic (free).** **Visibility: Public.**
5. Click **Create Space**.

Then, inside the new Space, open the **Settings** tab and scroll to **Variables and secrets**.

**Add 3 secrets** (click **New secret** for each). Secrets are hidden once saved:

| Name | Value |
|---|---|
| `HF_TOKEN` | the token from Step 4 |
| `ADMIN_TOKEN` | the ADMIN_TOKEN from Step 2 |
| `IP_SALT` | the IP_SALT from Step 2 |

**Add 6 variables** (click **New variable** for each). Variables are visible, which is fine for these:

| Name | Value |
|---|---|
| `LOG_DATASET` | `YOURNAME/open-door-logs` |
| `PUBLIC_BASE_URL` | `https://YOURNAME-open-door.hf.space` (all lowercase; any `_` or `.` in your username becomes `-`) |
| `TRUST_PROXY` | `1` |
| `LIVE_VARIANTS` | `0,B,P,E` |
| `DEFAULT_VARIANT` | `B` |
| `SHOW_FOOTER` | `1` |

Names must match exactly, including capitals.

## Step 6: Upload the five files

1. In the Space, open the **Files** tab, then **+ Add file → Upload files**.
2. In Finder, open the project folder, then the **`space`** folder inside it:
   `/Users/andrewtrimble/hackathons/AgentSwarm October 2026/space/`
3. Select all **five** files (`Dockerfile`, `README.md`, `app.py`, `notices.py`, `requirements.txt`) and drag them in.
   It's fine that `README.md` replaces the one Hugging Face made.
4. Commit message: `Deploy Open Door`. Click **Commit changes to main**.

## Step 7: Watch it build

1. Open the **App** tab. It will say **Building**. Click **Logs** to watch, if you like.
2. After 2–5 minutes it should say **Running**.
3. If it says **Build error** or **Runtime error**, copy the last 30 or so lines of the log into a text file and tell Claude where it
   is. The logs don't contain your secrets, but check for any `hf_...` token before sharing, just in case.

## Step 8: Check it works (4 quick checks)

**a. The page.** Open **`https://YOURNAME-open-door.hf.space/`** *directly*.
Don't use the `huggingface.co/spaces/...` address: it wraps the page in a frame that agents may not see.
You should see the dock dataset card, the notice titled **"An open door"**, and a short footer that starts "About this page".

**b. The admin page.** Open **`https://YOURNAME-open-door.hf.space/admin?token=YOUR_ADMIN_TOKEN`**.
A private browser window is best, so the password doesn't stay in your history.
The box at the top should start **"Saving: ON"**. If it says **FAILED**, stop and tell Claude the message. It contains no secrets.

**c. The address check.** On the same admin page, find the line **"Your X-Forwarded-For: …"**. It lists one or more addresses.
In another tab, open **https://api.ipify.org** to see your own public address. Tell Claude **which position** your address
is in, counting from the end (for example, "it's the last one" or "second from the end"). You don't need to share the address itself.
This tells the app which entry to trust.

**d. The filing cabinet.** About 10 minutes later, open **`https://huggingface.co/datasets/YOURNAME/open-door-logs`** → **Files**.
You should see a `logs/` folder containing a `run-…` folder with `visits.jsonl` inside. That means saving works.

## Step 9: Tell Claude

Send something like: *"Space is up at https://YOURNAME-open-door.hf.space. Saving is ON, and my address is last from the end."*
Claude will then check it from outside and walk you through placing the pointers.

---

## After the hackathon is judged: takedown checklist

1. Download the logs for your records: on the dataset's **Files** tab, use the download icon next to each file.
2. Space → **Settings** → **Delete this Space**.
3. **https://huggingface.co/settings/tokens** → delete `open-door-space`.
4. When you no longer need the logs, delete the `open-door-logs` dataset (Settings → Delete).
