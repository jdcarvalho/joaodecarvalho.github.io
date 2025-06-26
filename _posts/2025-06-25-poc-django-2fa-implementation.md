---
layout: post
author: "jdcarvalho"
title: "POC: Django 2FA Implementation"
date: 2025-06-25 14:07:00
categories: [Python, Django, 2FA]
---

# POC: Django 2FA Implementation

---

### 🔒 Introduction

[The otpauth repository](https://github.com/jdcarvalho/otpauth) is a proof‑of‑concept (POC) showcasing how to integrate Two‑Factor Authentication (2FA) via One‑Time Passwords (OTP) into a Django-based application. It leverages the pyotp library to generate and validate time-based OTPs (TOTP), adding an extra security layer on top of traditional username/password authentication.
It uses Django default admin for managing OTP settings and user activation, making it easy to integrate into existing Django projects.

### 📁 Project Structure

Key components of the repo include:
* Django app (otpauth/ directory): Contains models, views, forms, and templates needed for OTP management.
* custom_admin/: Admin customizations to manage OTP settings and user activation.
* templates/: HTML for OTP enrollment and verification pages.
* manage.py & requirements.txt: Typical Django scaffolding and Python dependencies, respectively.

---

### ✅ Setup Instructions

To run the POC:
1.	Create a virtual environment (e.g., Python3)
2. Install dependencies:

```bash
pip install -r requirements.txt
```
3. Run migrations and create a superuser:

```bash
./manage.py makemigrations
./manage.py migrate
./manage.py createsuperuser
```
4. Start the development server:

```bash
./manage.py runserver
```

5. Log in to Django admin, enable 2FA for a user, then test logging in to trigger OTP flows.

---

### 🧩 Core Components

- pyotp Integration
- The project imports pyotp to generate TOTP codes using a shared secret between server and user. This is core to generating time-bound OTPs.
- Secret Generation & Storage

When a user enables 2FA, the server:
- Generates a random base32 secret using pyotp.random_base32()
- Stores it securely in the user’s profile or a dedicated OTP model
- Exposes a QR code (via templates) for easy scanning by authenticator apps

---

### 📈 Flow Diagram Summary
![otp-flow.png]({{ site.baseurl }}/assets/img/posts/otp-flow.png)