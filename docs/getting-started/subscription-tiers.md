---
title: Subscription Tiers
description: Compare AIVA subscription plans (Free, Trial, Plus, Pro, and Enterprise) and learn how to upgrade.
hide:
  - toc
---

# Subscription Tiers

AIVA offers five subscription tiers designed to scale from individual exploration to full clinical and research workflows. Each tier unlocks progressively more features, higher limits, and advanced capabilities.

---

## Plan Comparison

| Feature | <span class="tier-badge tier-free">Free</span> | <span class="tier-badge tier-trial">Trial</span> | <span class="tier-badge tier-plus">Plus</span> | <span class="tier-badge tier-pro">Pro</span> | <span class="tier-badge tier-enterprise">Enterprise</span> |
|---------|:----:|:-----:|:----:|:---:|:----------:|
| **Price** | - | - | $20/month | $60/month | [Contact us](https://mamidi.ai/#contact) |
| **Credits per Week** | 0 | 1 | 3 | 10 | * |
| **Sample Storage** | 1 | 1 | 3 | 5 | * |
| **Max File Size** | 250 MB | 500 MB | 750 MB | 1 GB | * |
| **AI Queries per Day** | 50 | 100 | 200 | 500 | * |
| **Max API Keys** | 1 | 3 | 5 | 10 | * |
| **Secondary Analysis** | No | No | No | Yes | Yes |
| **Data Export** | No | Yes | Yes | Yes | Yes |
| **AI Auto-Fill (Reports)** | No | Yes | No | Yes | Yes |
| **Support** | - | - | Standard | Standard | Dedicated |

*\* Enterprise limits are customized to your organization's needs. [Contact us](https://mamidi.ai/#contact) for details.*

!!! info "No credit card required"
    The Free tier requires only an email-verified account. No payment information is collected.

!!! warning "Trial expiration"
    The Trial lasts 7 days. When it expires, your account reverts to the Free tier and samples are deleted after 30 days. Upgrade to a paid tier to keep your data and retain access to features like data export and AI Auto-Fill.

---

## Credit system

Credits control how many samples you can upload each week. Every upload consumes credits, and your tier determines how many credits you receive.

### Credit costs

| Upload type | Credits consumed |
|-------------|-----------------|
| VCF/CSV file upload | 1 credit per sample in the file |
| Parabricks pipeline | 3 credits (2 at pipeline completion + 1 at parsing) |

### How credits work

- Credits **reset every Sunday** on a weekly cycle.
- Credits are **checked at upload time** before the job starts. If you do not have enough credits, the upload is blocked.
- Credits are **consumed at job completion**, not when the job is submitted.
- The **Free tier cannot upload** samples. You must be on Trial or a paid tier to upload.
- The **Trial tier expires after 7 days** and reverts to Free.

!!! tip "Check your credit balance"
    Click the **usage indicator** in the header to see how many credits remain for the current week and when they reset.

---

## Upgrading your plan

You can upgrade your subscription at any time:

1. Click the **tier icon** in the top-right corner of the navbar.
2. Select **subscription limits** from the menu and select your desired tier.
3. The payment modal opens, for secure payment processing.
4. Your new tier is activated immediately upon successful payment.

!!! tip "Subscription changes take effect instantly"
    As soon as payment is confirmed, your account limits and feature access are updated. Refresh the page, if needed.

### Managing your subscription

- **View current plan**: Your active tier is displayed in the user menu and in account settings.
- **Usage tracking**: Click the usage indicator in the header to see your current consumption against plan limits (uploads used, queries remaining, etc.).
- **Cancel or downgrade**: Downgrade or cancel your subscription from the subscription management page.

---

## Frequently Asked Questions

??? question "What happens to my data if I downgrade?"
    Your samples may be deleted after a grace period when you downgrade to the free tier. For other tiers, you retain access to all previously uploaded samples and conversations. However, features tied to higher tiers (such as data export or AI Auto-Fill) will no longer be available until you upgrade again.

??? question "Can I try advanced features before paying?"
    Yes. The Trial tier gives you temporary access to advanced features. Sign up for a free account and your trial will be activated automatically.

??? question "Is payment information secure?"
    All payment processing is handled by Stripe, a PCI-DSS Level 1 certified payment processor. AIVA does not store your credit card details.

??? question "Do you offer institutional or volume pricing?"
    Yes. The Enterprise tier offers custom pricing based on your organization's needs. [Contact us](https://mamidi.ai/#contact) for details.

---

## Next Steps

Ready to start using AIVA? Head back to the guides:

- [:octicons-arrow-right-24: Upload your first sample](uploading-your-first-sample.md)
- [:octicons-arrow-right-24: Explore the AIVA assistant](../aiva-chat/index.md)
