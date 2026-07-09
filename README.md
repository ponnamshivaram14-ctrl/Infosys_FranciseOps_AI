# Milestone 1 — User Authentication Module

**Infosys Springboard Internship 7.0 · Batch 1**

A Streamlit-based authentication portal with JWT session handling, email-based OTP password recovery, security-question password recovery, and separate Admin/User dashboards — built and deployed from Google Colab via ngrok.

---

## 📌 What This Milestone Covers

This milestone implements a complete authentication module with three public-facing pages (Login, Signup, Forgot Password) and two role-based dashboards (User and Admin), all running as a single Streamlit app inside Google Colab and exposed publicly through an ngrok tunnel.

The goal was to build a hallucination-free, secure login flow — no plaintext passwords, no hardcoded secrets, no ambiguous error messages that leak whether a username or password was wrong, and no way to reach a dashboard without a valid signed session token.

---

## ✅ Features Built

| Feature | Description |
|---|---|
| **Login Page** | Email + password, both mandatory. Issues a signed JWT on success. Shows one generic error on failure (never reveals whether the email or password was wrong). |
| **Signup Page** | Username, Email, Password, Confirm Password, Security Question (fixed list), Security Answer — all mandatory. Username/email uniqueness enforced at the database level. Routes back to Login after account creation (no auto-login). |
| **Forgot Password — Security Question route** | Verify identity by answering the security question set at signup, then set a new password. |
| **Forgot Password — OTP route** | Enter the registered email, receive a 6-digit OTP by Gmail (5-minute expiry, signed inside a short-lived JWT so the server never stores the OTP in plaintext), verify it, then set a new password. |
| **Field Validation** | No form submits with an empty required field. Email must match `ab@cd.ef` shape (≥2 letters before `@`, ≥2 letters between `@` and the dot, ≥2 letters after the final dot). Passwords require 8+ characters with at least one uppercase, one lowercase, one digit, and one special symbol, and Confirm Password must match exactly. |
| **JWT Session Handling** | A session JWT is issued only at successful Login (never at Signup or password reset — those route back to Login instead). The Dashboard route checks the token is present and valid before rendering. |
| **User Dashboard** | Welcome banner with the logged-in username/email, analytics-style summary cards, a system health gauge, and a Logout action that clears the session and returns to Login. |
| **Admin Dashboard** | Separate login using an admin email/password defined directly in code (not created via Signup). Lists every registered user's username and email — password data is never displayed. |
| **Secrets Management** | `JWT_SECRET`, `NGROK_AUTHTOKEN`, `EMAIL_ADDRESS`, `EMAIL_PASSWORD` are all read from Google Colab Secrets at runtime — nothing is hardcoded in the notebook. |

---

## 🛠️ Tech Stack

- **Frontend / App framework:** Streamlit
- **Session auth:** PyJWT (HS256-signed tokens)
- **Password hashing:** bcrypt
- **Database:** SQLite (local file, `infosys_portal.db`)
- **Email delivery (OTP):** Gmail SMTP (`smtplib`) with a Gmail App Password
- **Public tunnel:** pyngrok
- **Charts:** Plotly (dashboard gauge)
- **Runtime:** Google Colab (Python 3)

---

## 📂 Repository Structure

Infosys_FranciseOps_AI/
├── README.md                     ← this file (repo root)
├── Milestone1/
│   ├── Milestone1_Merged.ipynb   ← the notebook (install → app.py → launch)
│   └── app.py                    ← exported copy of the Streamlit app (for reference)
└── Images/
├── Login Page.png
├── Signup Page.png
├── Forgot Password - Security Question.png
├── Forgot Password - Security Question1.png
├── Forgot Password - OTP.png
├── Forgot Password - OTP1.png
├── User Dashboard.png
└── Admin Dashboard.png



---

## ⚙️ Setup — Before You Run

1. **ngrok account:** Sign up free at ngrok.com, copy your Authtoken from the dashboard.
2. **Gmail App Password:** Turn on 2-Step Verification on the sender Gmail account, then generate an App Password (Google Account → search "App Passwords"). Copy the 16-character password immediately — Google only shows it once.
3. **Colab Secrets:** In your Colab notebook, click the 🔑 key icon in the left sidebar and add:

   | Secret Name | Value |
   |---|---|
   | `JWT_SECRET` | Any long random string (e.g. generate with `secrets.token_hex(32)`) |
   | `NGROK_AUTHTOKEN` | Your ngrok Authtoken |
   | `EMAIL_ADDRESS` | The Gmail address that sends OTP emails |
   | `EMAIL_PASSWORD` | The 16-character Gmail App Password |
   | `ADMIN_PASSWORD` *(optional)* | Custom admin password — defaults to `admin@123` if omitted |

   Toggle **notebook access ON** for each secret.

---

## ▶️ How to Run

1. Open `Milestone1_Merged.ipynb` in Google Colab.
2. Run **Cell 1** — installs `streamlit`, `streamlit-option-menu`, `pyngrok`, `pyjwt`, `bcrypt`, `plotly`.
3. Run **Cell 2** — writes out `app.py` (the full Streamlit app).
4. Run **Cell 3** — loads secrets from Colab into the environment, starts Streamlit on port 8501, opens an ngrok tunnel, and prints a public URL.
5. Open the printed URL in your browser. Log in as admin with the email/password from your `ADMIN_PASSWORD` secret (email defaults to `infosys@ai`), or sign up as a new user to see the User Dashboard.
6. Press **Ctrl+C** or the Colab Stop button on Cell 3 to shut the server and tunnel down cleanly.

---

## 📸 Screenshots

### 1. Login Page
![Login Page](Images/Login%20Page.png)

### 2. Signup / Create Account
![Signup Page](Images/Signup%20Page.png)

### 3. Forgot Password — Security Question Route
**Step 1 — Enter email & choose route:**
![Forgot Password - Security Question](Images/Forgot%20Password%20-%20Security%20Question.png)

**Step 2 — Answer question & set new password:**
![Forgot Password - Security Question Step 2](Images/Forgot%20Password%20-%20Security%20Question1.png)

### 4. Forgot Password — OTP Route
**Step 1 — Enter email & request OTP:**
![Forgot Password - OTP](Images/Forgot%20Password%20-%20OTP.png)

**Step 2 — Verify OTP & set new password:**
![Forgot Password - OTP Step 2](Images/Forgot%20Password%20-%20OTP1.png)

### 5. User Dashboard
![User Dashboard](Images/User%20Dashboard.png)

### 6. Admin Dashboard
![Admin Dashboard](Images/Admin%20Dashboard.png)

---

## 🔒 Security Notes

- All passwords are hashed with bcrypt before storage — plaintext passwords are never saved.
- Login failures return one generic error message regardless of whether the email or password was incorrect.
- The OTP is never stored in the database in plaintext; it's hashed and embedded inside a short-lived (5-minute) signed JWT.
- No secrets (JWT signing key, ngrok token, Gmail address, Gmail App Password, admin password) are hardcoded anywhere in this notebook — all are pulled from Colab Secrets at runtime.

---

## ✅ Final Checklist

- [x] `Milestone1` folder created inside the Infosys Repository
- [x] README.md added and explains the milestone
- [x] Login, Signup, Forgot Password (security question + OTP) all working
- [x] JWT used for session handling
- [x] User Dashboard and Admin Dashboard both working
- [x] ngrok, Gmail App Password, and all secrets set up via Colab Secrets
- [x] Mandatory-field, email, and password validation implemented
- [x] Screenshots captured and linked in README.md
- [x] All personal secrets removed from the notebook before upload
