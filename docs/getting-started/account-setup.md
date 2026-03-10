---
title: Account Setup
description: Create your AIVA account, verify your email, log in, and configure your profile settings.
---

# Account Setup

AIVA uses Firebase Authentication to manage accounts. You can sign up with an email and password or use Google single sign-on.

---

## Creating Your Account

1. Navigate to the AIVA login page.
2. Select **Sign Up** to switch to the registration form.
3. Choose one of two methods:

    === "Email and Password"

        - Enter your full name, email address, and a strong password.
        - Click **Sign Up**.
        - A verification email will be sent to the address you provided.

    === "Google Sign-In"

        - Click the **Sign in with Google** button.
        - Select your Google account and authorize AIVA.
        - Your account is created and verified automatically.

!!! tip "Password requirements"
    Use at least 8 characters with a mix of uppercase, lowercase, numbers, and symbols. Firebase enforces minimum complexity rules and will reject weak passwords.

---

## Email Verification

If you signed up with an email and password, you must verify your address before using the platform.

1. Check your inbox (and spam folder) for an email from AIVA.
2. Click the verification link in the email. This opens a confirmation page in your browser.
3. Once verified, return to the login page and sign in with your credentials.

!!! warning "Verification link expired?"
    Verification links are valid for a limited time. If yours has expired, log in and use the **Resend Verification** option on the prompt that appears.

---

## Logging In

1. Navigate to the AIVA login page.
2. Enter your email and password, or click **Sign in with Google**.
3. After successful authentication, you are redirected to the main Chat interface.

!!! info "Password reset"
    Click **Forgot Password?** on the login page. Enter your email address and follow the instructions in the reset email to create a new password.

---

## Profile and Settings

Once logged in, access your profile settings from the user menu in the top-right corner of the header.

### User Menu Options

- **Settings** -- Opens the configuration panel where you can manage model preferences and API settings.
- **Upgrade Plan** -- Opens the payment modal to change your subscription tier. See [Subscription Tiers](subscription-tiers.md) for details.
- **Log Out** -- Signs you out and returns you to the login page.

### Model Configuration

From the Settings panel, you can:

- **Select your default AI model** -- Choose from available language models grouped by provider. This controls which model powers the AIVA assistant in your conversations.
- **Manage API keys** -- Configure your own API keys for external services if your workflow requires it.

!!! tip "Model selection is per-session"
    You can also switch models on the fly from the Chat interface without opening Settings. Your choice persists for the current session.

---

## Session Management

AIVA includes automatic inactivity detection to protect your account:

- After a period of inactivity, a warning dialog appears asking if you want to stay signed in.
- If you do not respond, the session expires and you are logged out automatically.
- Simply interact with the page or click the dismiss button to reset the inactivity timer.

---

## Next Steps

Now that your account is set up, learn how to navigate the interface:

[:octicons-arrow-right-24: Navigating the UI](navigating-the-ui.md)
