
# GPCB Pay — Card Payments for WooCommerce

**PayPal-hosted debit and credit card payment experiences for eligible WooCommerce merchants.**

GPCB Pay (General PayPal Card Bridge) is an independently developed WooCommerce payment integration combining a lightweight, open-source WordPress Connector with an external, managed SaaS Payment Core.

Designed for WooCommerce Checkout Blocks, GPCB Pay focuses on secure integration, server-verified payment capture, reliable payment state, and merchant onboarding.

[**Install Plugin**](https://wordpress.org/plugins/gpcb-pay-card-payments-for-woocommerce/) · [**Official Website**](https://gpcbpay.com/) · [**Documentation**](https://gpcbpay.com/documentation/) · [**Merchant Dashboard**](https://app.gpcbpay.com/)

**Current WordPress Plugin Version: `0.1.0`**

---

## Overview

GPCB Pay consists of three components:

| Component | Purpose |
|---|---|
| WooCommerce Connector | Checkout Blocks integration, gateway configuration, and authenticated SaaS communication |
| Private SaaS Payment Core | PayPal Order and Capture operations, server verification, durable state, and recovery |
| Merchant Dashboard | Merchant onboarding, store verification, PayPal configuration, and subscription management |

The WordPress Connector is free and open-source under **GPLv2 or later**.

The required external GPCB Pay SaaS is a separate managed service that may require an eligible trial or paid subscription. PayPal processing fees are separate.

**The Connector cannot process payments without its SaaS dependency.**

## Supported Payment Modes

### Guest Card

Eligible PayPal-hosted guest card checkout that may allow buyers to pay with debit or credit cards.

Availability depends on PayPal merchant, country, account, and checkout-context eligibility.

### Advanced Card

PayPal-hosted Advanced Card Fields integrated into WooCommerce Checkout Blocks.

Available only when PayPal grants the merchant the necessary capabilities and approval.

Supported Advanced Card layouts:

- Clean
- Compact
- Premium

### Important Limitations

- Version `0.1.0` supports WooCommerce Checkout Blocks only.
- Classic shortcode checkout is not supported.
- Guest or Advanced must be explicitly selected.
- Automatic mode switching is not implemented.
- PayPal determines card-payment eligibility and availability.
- A successful PayPal API connection does not guarantee access to every payment experience.

---

## Main Features

### Checkout Integration

- WooCommerce Checkout Blocks integration.
- Eligible Guest Card and Advanced Card experiences.
- PayPal JavaScript SDK v6 integration.
- PayPal-hosted card entry.
- Sandbox and Live configuration.
- Browser-safe PayPal initialization.
- Advanced Card presentation layouts.

### Payment Reliability

- SaaS-controlled PayPal Order creation.
- Server-verified PayPal Capture.
- Server-derived WooCommerce amounts and currencies.
- Commercial fingerprint verification.
- Idempotency safeguards.
- Duplicate-Capture protection.
- Durable payment records.
- Payment recovery and reconciliation.

### Merchant Security

- HMAC-authenticated Connector communication.
- Merchant, store, and subscription authorization boundaries.
- DNS TXT domain ownership verification.
- Provisioning-store Connector proof.
- Active-store connection diagnostics.
- Protected merchant PayPal credentials managed through the private SaaS.

## Payment Security Architecture

GPCB Pay separates browser interactions from authoritative server-side payment verification.

**Browser approval is not proof of payment.**

**Creating a PayPal Order is not proof of payment.**

Only a successful server-verified Capture allows the corresponding WooCommerce order to be completed.

WooCommerce remains responsible for its order totals, currency, and order-completion operations.

The private SaaS coordinates PayPal payment operations, verifies Capture results, and maintains durable payment evidence.

When a payment outcome is uncertain, the original attempt may require verification or reconciliation.

Blind duplicate Capture attempts must be avoided.

### Card Data Handling

Card details are entered using PayPal-hosted components.

The Connector is not designed to collect or store raw card numbers, CVV, or complete card expiry details.

Merchant PayPal Client Secrets belong in the secure Merchant Dashboard workflow, not in WordPress Connector settings.

Merchants remain responsible for applicable privacy, security, and regulatory obligations.

---

## System Requirements

| Requirement | Minimum or condition |
|---|---|
| WordPress | 7.1 or later |
| PHP | 8.2 or later |
| WooCommerce | 11.1.2 or later; verify compatibility before upgrades |
| Checkout | WooCommerce Checkout Blocks |
| Website | HTTPS |
| Merchant | Verified GPCB Pay account |
| Store | Verified and activated SaaS store |
| PayPal | Appropriate merchant eligibility |
| Service | Valid GPCB Pay SaaS authorization |

## Getting Started

### 1. Install the Plugin

Install and activate GPCB Pay from the official WordPress Plugin Directory.

**Official Plugin:**

https://wordpress.org/plugins/gpcb-pay-card-payments-for-woocommerce/

Open:

`WooCommerce > Settings > Payments`

Locate the GPCB Pay payment gateway.

### 2. Create Your Merchant Account

Register or sign in through the Merchant Dashboard:

https://app.gpcbpay.com/

Complete merchant email verification.

Registration alone does not activate a store, start the trial, or authorize payment processing.

### 3. Add Your WooCommerce Store

Create a store in the Merchant Dashboard.

Securely save the issued:

- Connector Key ID
- Connector Signing Secret

The Signing Secret may only be displayed once.

Never publish sensitive Connector credentials.

### 4. Configure the WooCommerce Connector

Enter the Connector Key ID and Signing Secret in WooCommerce gateway settings.

Choose the appropriate environment:

- Sandbox
- Live

Select Guest Card or Advanced Card explicitly.

Save the settings.

### 5. Verify Domain Ownership

Generate a DNS TXT verification challenge through the Merchant Dashboard.

Add the exact TXT record supplied by the SaaS through your DNS provider.

Complete SaaS domain verification after DNS propagation.

### 6. Verify Your New Store Connection

In WooCommerce gateway settings, use:

`Verify New Store Connection`

This creates an authenticated proof of possession of the saved Connector credentials.

The provisioning-store proof expires within 15 minutes.

DNS ownership verification and Connector proof are separate requirements.

### 7. Activate the Store

Return to the Merchant Dashboard.

Confirm the required verification checks and complete the authorized store activation workflow.

Store activation does not automatically begin a trial or subscription.

### 8. Test the Active SaaS Connection

After store activation, use:

`Test SaaS Connection`

This verifies active-store communication.

A successful diagnostic is not proof of PayPal eligibility or successful payment Capture.

### 9. Configure PayPal

Configure the appropriate PayPal Business API credentials through the Merchant Dashboard.

Sandbox and Live credentials must remain separate.

The Connector does not require PayPal Client Secrets in WordPress settings.

### 10. Confirm Payment Readiness

Before accepting customer-facing Live payments:

- Confirm store activation.
- Confirm the payment environment.
- Confirm PayPal eligibility.
- Confirm applicable SaaS service authorization.
- Perform the appropriate Sandbox testing.
- Verify server-side Capture and the corresponding WooCommerce order state.

Sandbox success does not establish Live eligibility.

For the complete onboarding instructions, see the [official plugin documentation](https://wordpress.org/plugins/gpcb-pay-card-payments-for-woocommerce/).

---

## Video Setup Tutorials

Learn how to configure GPCB Pay with real product interfaces.

### English — Full Setup Tutorial

[![GPCB Pay English Setup Tutorial](https://img.youtube.com/vi/NWdg48OdxGM/hqdefault.jpg)](https://www.youtube.com/watch?v=NWdg48OdxGM)

[Watch English Tutorial on YouTube](https://www.youtube.com/watch?v=NWdg48OdxGM)

### Moroccan Darija — Full Setup Tutorial

[![GPCB Pay Moroccan Darija Setup Tutorial](https://img.youtube.com/vi/S33seR3CDX0/hqdefault.jpg)](https://www.youtube.com/watch?v=S33seR3CDX0)

[Watch Moroccan Darija Tutorial on YouTube](https://www.youtube.com/watch?v=S33seR3CDX0)

The tutorials demonstrate merchant onboarding, WooCommerce configuration, DNS ownership verification, Connector setup, PayPal Sandbox and Live configuration, and eligible Guest Card and Advanced Card experiences.

Follow the current documentation if interfaces or requirements have changed.

---

## SaaS Subscription and Pricing

The WordPress Connector is free and open-source.

The external GPCB Pay SaaS provides managed payment infrastructure and is a separate service.

### Initial Pro Offering

| Plan | Price |
|---|---|
| Pro Monthly | USD $19 |
| Pro Yearly | USD $190 |
| Eligible Trial | 7 consecutive days (168 hours) |
| Website Allowance | One authorized WooCommerce website |
| Renewal | Manual |

Additional conditions:

- The eligible trial is available once per authorized merchant.
- Trial activation is separate from merchant registration and store activation.
- Automatic recurring billing is not included in version `0.1.0`.
- The initial Pro plan does not include a three-store tier.
- PayPal processing fees are additional.
- Service entitlement and PayPal merchant eligibility are separate checks.

[**View Current Pricing**](https://gpcbpay.com/pricing/)

---

## Open Source and Distribution

### WordPress Connector

GPCB Pay — Card Payments for WooCommerce is distributed under **GPLv2 or later** through the official WordPress Plugin Directory.

**Official Plugin and Source Distribution:**

https://wordpress.org/plugins/gpcb-pay-card-payments-for-woocommerce/

### About This GitHub Repository

This repository is the **public GPCB Pay information and project showcase**.

It provides official product information, documentation links, installation resources, and tutorials.

It is not the development source repository for the private GPCB Pay SaaS Payment Core or Merchant Dashboard.

The published WooCommerce Connector source is available through WordPress.org.

For official plugin releases and updates, use the WordPress Plugin Directory.

---

## Documentation and Support

| Resource | Link |
|---|---|
| Official Website | [gpcbpay.com](https://gpcbpay.com/) |
| WordPress Plugin | [Plugin Directory](https://wordpress.org/plugins/gpcb-pay-card-payments-for-woocommerce/) |
| Documentation | [Setup Guide](https://gpcbpay.com/documentation/) |
| Merchant Dashboard | [app.gpcbpay.com](https://app.gpcbpay.com/) |
| Pricing | [Plans and Trial](https://gpcbpay.com/pricing/) |
| Privacy Policy | [Privacy Policy](https://gpcbpay.com/privacy-policy/) |
| Terms of Service | [Terms](https://gpcbpay.com/terms-of-service/) |
| Email Support | support@gpcbpay.com |

Do not share passwords, Connector Signing Secrets, PayPal Client Secrets, OAuth tokens, or cardholder information in public issues or support requests.

## Disclaimer

GPCB Pay is independently developed.

It is not affiliated with, sponsored by, or endorsed by PayPal or WooCommerce.

PayPal determines merchant eligibility, available capabilities, and payment-method availability.

---

**GPCB Pay — Card Payments for WooCommerce**

*Built independently with a focus on secure integration, payment verification, and reliability.*
