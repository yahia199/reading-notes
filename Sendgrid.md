# Sendgrid

## Create an Azure Subscription
To get started with Twilio SendGrid and Azure
 You will need to sign in or create a Microsoft account if you do not already have one.

Once logged in, select the Subscriptions icon under the Azure services menu.

Azure services menu with the Subscriptions icon highlighted
A new page will load, listing your current subscriptions. You can add Twilio SendGrid to an existing Subscription or Select +Add to create a new subscription. For more information about Subscriptions and billing, see the Azure docs for how to "Create an additional Azure subscription."

For this guide, we will create a new Subscription.

---

## Create a Twilio SendGrid account

From the Azure portal home page, select Marketplace under Azure services. If you do not see the Marketplace icon, you can search for it by selecting More services.

The Azure portal home page with the Marketplace icon highlighted
The Azure Marketplace provides many services, including the Twilio SendGrid email service. You can find it by searching for "Twilio SendGrid." You will also find it under Software as a Service (SaaS).

Click the Twilio SendGrid resource to load a page where you can select your account tier. You can start with a free account and upgrade as your sending needs change. See the Twilio SendGrid pricing page to understand what's included with each plan.

The Twilio SendGrid integration listed in the Azure Marketplace
The Twilio SendGrid integration detail page with a "Setup + Subscripe" link
Select Set up + subscribe. You will be taken to a page where you can assign your Twilio SendGrid account to an Azure Subscription and Resource Group. Once you have completed the required fields, select Review + subscribe.

The Twilio SendGrid integration configuration basics
You will be asked to agree to Azure's term of services. You can now review your order and click Subscribe.

It takes a few moments to establish your account. You will be shown a progress screen. When the setup is complete, you will be able to click the Configure account now button to be taken to the Twilio SendGrid App. You will also receive an email when the subscription setup is complete.

---

## Twilio SendGrid account setup
Before sending your first email, you will need to complete the following Twilio SendGrid account setup. These requirements help secure your account and keep your messages from landing in spam folders.

- Configure Two-factor authentication
- Create an API key
- Complete Sender Authentication

---

## Two-factor authentication
Twilio SendGrid uses Two-factor authentication (2FA) to help protect your account. To enable 2FA, Navigate to Two-Factor Authentication in the Twilio SendGrid Settings menu, and click Add Two-Factor Authentication.

The Twilio SendGrid App's Two-factor authentication menu
A modal will open where you can complete the 2FA setup. Click Ok, Got it to continue.

If you have previously configured services to authenticate with Twilio SendGrid APIs using Basic Authentication, enabling 2FA will break those integrations. You must use API keys to authenticate with Twilio SendGrid APIs.

A modal asking to confirm 2FA setup
Twilio SendGrid supports 2FA using either SMS or the Authy App. Select your preferred 2FA method, and click Next.

You will need to enter a phone number to complete the 2FA process. SMS users will be sent a confirmation code at the number they entered. Authy users will be sent instructions for downloading and completing the 2FA setup using the Authy app.

---

## API keys
API Keys authenticate your application, mail client, or website with Twilio SendGrid services. Unlike a username and password, API keys are scoped to provide access only to the services you select. You can also delete and create API keys without impacting your other account credentials. For these reasons, Twilio SendGrid requires you to connect to its services using API keys.

Create an API key
In the Twilio SendGrid App, navigate to API Keys in the Settings menu, and select Create API Key.

A modal will open where you can create your key. You must name the API key — we recommend something that will clearly differentiate the key from others you may create in the future.

A modal where you can name configure and configure an API key
You must also select the type of key you want to create. Twilio SendGrid provides three types of API key:

- Full Access
- Restricted Access
- Billing Access
To keep your account secure, you should give each key the least privilege necessary. You can limit a key's capabilities by creating a Restricted Access key and selecting a subset of all the possible permissions. 