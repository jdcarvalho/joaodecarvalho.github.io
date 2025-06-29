---
layout: post
author: "jdcarvalho"
title: "Proof of Concept: 2FA in Django with TOTP"
date: 2025-06-25 14:07:00
image: /assets/img/posts/poc-django-2fa-implementation.png
thumbnail: /assets/img/posts/poc-django-2fa-implementation.png
categories: [Python, Django, 2FA]
---

# Proof of Concept: 2FA in Django with TOTP

---

### 🔒 Introduction

[The otpauth repository](https://github.com/jdcarvalho/otpauth) is a proof of concept (POC) that demonstrates how to integrate Two‑Factor Authentication (2FA) using Time‑based One‑Time Passwords (TOTP) into a Django application.

It leverages the `pyotp` library to generate and verify time-bound OTPs, providing an extra layer of security on top of the traditional username/password login flow. The project also customizes the Django admin interface to manage 2FA settings, making it easy to integrate into existing Django apps — especially admin panels or internal tools that need additional protection.

---

### 📁 Project Structure

The repository includes the following components:

- `otpauth/`: Django app containing models, views, forms, and core logic for OTP integration.
- `custom_admin/`: Admin customizations to manage OTP settings and enable 2FA per user.
- `templates/`: HTML pages for OTP enrollment, QR code display, and verification.
- `manage.py` & `requirements.txt`: Typical Django project files and dependencies.

---

### ✅ Setup Instructions

To run the POC locally:

1. Create a virtual environment (Python 3.x recommended)
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

5. Access Django Admin at `http://127.0.0.1:8000/admin/`, enable 2FA for a user, and log in to test OTP flows.

---

### 🧩 Core Components

- **pyotp Integration**: The `pyotp` library is used to generate and validate TOTP codes using a shared secret between the server and the user’s authenticator app.

- **Secret Generation & Storage**:
  - A random base32 secret is generated using `pyotp.random_base32()`
  - The secret is securely stored in the user profile or a dedicated OTP model
  - A QR code is generated and rendered via templates to simplify enrollment with apps like Google Authenticator or Authy

---

### 📈 Flow Diagram Summary

The diagram below illustrates the 2FA flow, from secret generation to OTP verification during login:

![OTP Flow]({{ site.baseurl }}/assets/img/posts/otp-flow.png)

---

### 🔧 Next Steps (Optional Enhancements)

This POC can be extended with the following improvements for real-world use:

- Add backup codes for recovery
- Enforce OTP validation across all login endpoints using middleware
- Integrate support for WebAuthn or hardware-based tokens
- Secure the QR code endpoint with permissions or CSRF protection

---

### 🛡️ Disclaimer

This implementation is intended as a learning resource and starting point. Additional hardening is required before deploying it in production environments, such as rate-limiting login attempts and encrypting stored secrets.