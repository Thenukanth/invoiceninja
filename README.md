## IE5042 – Software Security Assignment

### Student Security Analysis Project

This repository is used for conducting a structured security analysis
of the Invoice Ninja web application.

### Scope of Work
- Local deployment and environment configuration
- Threat modeling using STRIDE
- OWASP Top 10 security testing
- Automated and manual vulnerability analysis
- Implementation of security improvements
- Retesting and documentation

### Ethical Statement
All security testing will be conducted on a locally deployed instance.
No testing will be performed against live production systems.

## 1. Group Members
Member 1: Thenuja Jeyakanthan - MS25950540 
Member 2: Umesha Herath - MS25943092

## 2. Project Overview

This project involves performing security analysis and remediation on a web application. Both Dynamic Application Security Testing (DAST) and Static Application Security Testing (SAST) techniques were used to identify and fix vulnerabilities.

The objective was to:

Identify real-world vulnerabilities
Apply secure coding and configuration fixes
Verify mitigation effectiveness
Maintain proper version control practices

## 3. Original Project (Third-Party Source)
Project Name: Invoice Ninja
GitHub Repository: https://github.com/invoiceninja

This project was used as the base application for vulnerability analysis and remediation.

## 4. Modified Project Repository
GitHub Repository (Secured Version):
git clone https://github.com/Thenukanth/invoiceninja.git 

This repository contains:

All implemented fixes
Full commit history
Security improvements

## 5. Key Security Fixes Implemented

The following vulnerabilities were identified and resolved:

Content Security Policy (CSP) not set
Cross-Origin Resource Sharing (CORS) misconfiguration
Missing HttpOnly flag on cookies
Missing Secure flag on cookies
Missing Permissions-Policy header
Missing X-Content-Type-Options header
Information disclosure via Server and X-Powered-By headers
Timestamp disclosure
PHP Type Juggling vulnerability (authentication bypass)
DOM-based Cross-Site Scripting (XSS)
Exposure of OAuth credentials in source code

## 6. Technologies Used
Docker (Containerized Environment)
NGINX (Web Server Configuration)
PHP (Backend)
JavaScript (Frontend)
Git & GitHub (Version Control)
Semgrep (Static Analysis Tool)
Browser DevTools (Dynamic Analysis)

## 7. Commit History Requirement

The GitHub repository includes:

Multiple commits with descriptive messages
Clear tracking of each vulnerability fix
Evidence of collaborative development

This ensures transparency and validates the remediation process.

## 8. Notes
Sensitive credentials (OAuth keys) were removed from source code and securely stored in environment variables.
Some security headers (e.g., Secure cookies) may not be visible in local HTTP testing environments but will function correctly under HTTPS.
Certain server-level configurations are partially limited due to Docker container constraints.

## 9. Conclusion

The project demonstrates the successful identification, remediation, and verification of multiple security vulnerabilities using industry-standard practices. The final application is significantly more secure and adheres to modern web security standards.






<p align="center">
<a href ="https://www.youtube.com/watch?v=CxGxXiotv0I" target="_blank" title="Invoice Ninja Overview Video"><img src="https://raw.githubusercontent.com/hillelcoren/invoice-ninja/master/public/images/round_logo.png" alt="Sublime's custom image"/></a>
</p>

![v5-develop phpunit](https://github.com/invoiceninja/invoiceninja/workflows/phpunit/badge.svg?branch=v5-develop)
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/d16c78aad8574466bf83232b513ef4fb)](https://www.codacy.com/gh/turbo124/invoiceninja/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=turbo124/invoiceninja&amp;utm_campaign=Badge_Grade)
<a href="https://cla-assistant.io/invoiceninja/invoiceninja"><img src="https://cla-assistant.io/readme/badge/invoiceninja/invoiceninja" alt="CLA assistant" /></a>

# Invoice Ninja 5

Invoice Ninja Version 5 is here! We've taken the best parts of version 4 and added the most requested features to create an invoicing application like no other. Check the [Invoice Ninja YouTube Channel](https://www.youtube.com/@appinvoiceninja) to get up to speed, or try the [Demo](https://react.invoicing.co/demo) now.

**Choose your setup**

- [Hosted](https://www.invoiceninja.com): Our hosted version is a Software as a Service (SaaS) solution. You're up and running in under 5 minutes, with no need to worry about hosting or server infrastructure.
- [Self-Hosted](https://www.invoiceninja.org): For those who prefer to manage their own hosting and server infrastructure. This version gives you full control and flexibility.

All Pro and Enterprise features from the hosted app are included in the source-available code. We offer a $40 per year white-label license to remove the Invoice Ninja branding from client-facing parts of the app.

#### Get social with us

* [Support Forum](https://forum.invoiceninja.com)
* [Slack](http://slack.invoiceninja.com)
* [Discord](https://discord.gg/ZwEdtfCwXA)
* [Instagram](https://www.instagram.com/appinvoiceninja)

#### Documentation

* [Invoice Ninja - API](https://api-docs.invoicing.co/)
* [Invoice Ninja - Developer Guide](https://invoiceninja.github.io/en/developer-guide/)
* [Invoice Ninja - User Guide](https://invoiceninja.github.io/en/user-guide/)
* [Invoice Ninja - Self-Hosted Installation Guide](https://invoiceninja.github.io/en/self-host-installation/)

## Installation Options and Clients

### Mobile Apps
* [iPhone](https://apps.apple.com/app/id1503970375?platform=iphone)
* [Android](https://play.google.com/store/apps/details?id=com.invoiceninja.app)
* [F-Droid](https://f-droid.org/en/packages/com.invoiceninja.app)

### Desktop Apps
* [macOS](https://apps.apple.com/app/id1503970375?platform=mac)
* [Windows](https://microsoft.com/en-us/p/invoice-ninja/9n3f2bbcfdr6)
* [Linux - Snap](https://snapcraft.io/invoiceninja)
* [Linux - Flatpak](https://flathub.org/apps/com.invoiceninja.InvoiceNinja)

### Self-Hosted Server Installation 
**Note:** The self-hosted options do support the desktop and mobile apps.

* [Server or VM](https://invoiceninja.github.io/en/self-host-installation/)
* [Docker File](https://hub.docker.com/r/invoiceninja/invoiceninja/)
* [Cloudron](https://www.cloudron.io/store/com.invoiceninja.cloudronapp2.html)
* [Softaculous](https://www.softaculous.com/apps/ecommerce/Invoice_Ninja)
* [Elestio](https://elest.io/open-source/invoiceninja)
* [YunoHost](https://apps.yunohost.org/app/invoiceninja5)

### Recommended Providers
* [Stripe](https://stripe.com/)
* [Postmark](https://postmarkapp.com/)

### SDKs available for easier API consumption
* [Go SDK](https://github.com/AshkanYarmoradi/go-invoice-ninja)

## [Advanced] Quick Hosting Setup

In addition to the official [Invoice Ninja - Self-Hosted Installation Guide](https://invoiceninja.github.io/en/self-host-installation/) we have a few commands for you.

```sh
git clone --depth 1 -b v5.11.53 https://github.com/invoiceninja/invoiceninja.git
cp .env.example .env
composer i -o --no-dev
```

**Note** replace v5.11.53 with the latest tag version, you will also want to ensure that when performing updates, you use the latest tag version rather than a particular branch, ie v5-develop. This will ensure that you are not pulling in work in progress code.

Please Note: 
Your APP_KEY in the .env file is used to encrypt data, if you lose this you will not be able to run the application.

Run if you want to load sample data, remember to configure .env
```sh
php artisan migrate:fresh --seed && php artisan db:seed && php artisan ninja:create-test-data
```

To run the web server
```sh
php artisan serve 
```

Navigate to (replace localhost with the appropriate domain)
```
http://localhost:8000/setup - To setup your configuration if you did not load sample data.
http://localhost:8000/ - For Administrator Logon

user: small@example.com
pass: password

http://localhost:8000/client/login - For Client Portal

user: user@example.com
pass: password
```
## Developers Guide

In addition to the official [Invoice Ninja - Developer Guide](https://invoiceninja.github.io/en/developer-guide/) we've got your back with some insights.

### App Design

The API and client portal have been developed using [Laravel](https://laravel.com) if you wish to contribute to this project familiarity with Laravel is essential.

When inspecting functionality of the API, the best place to start would be in the routes/api.php file which describes all of the availabe API endpoints. The controller methods then describe all the entry points into each domain of the application, ie InvoiceController / QuoteController

The average API request follows this path into the application.

* Middleware processes the request initially inspecting the domain being requested + provides the authentication layer.
* The request then passes into a Form Request (Type hinted in the controller methods) which is used to provide authorization and also validation of the request. If successful, the request is then passed into the controller method where it is digested, here is an example:

```php
public function store(StoreInvoiceRequest $request)
{

    $invoice = $this->invoice_repo->save($request->all(), InvoiceFactory::create(auth()->user()->company()->id, auth()->user()->id));

    $invoice = $invoice->service()
                        ->fillDefaults()
                        ->triggeredActions($request)
                        ->adjustInventory()
                        ->save();

    event(new InvoiceWasCreated($invoice, $invoice->company, Ninja::eventVars(auth()->user() ? auth()->user()->id : null)));

    return $this->itemResponse($invoice);

}
```

Here for example we are storing a new invoice, we pass the validated request along with a factory into the invoice repository where it is processed and saved.

The returned invoice then passes through its service class (app/Services/Invoice) where various actions are performed.

A event is then fired which notifies listeners in the application (app/Providers/EventServiceProvider) which perform non blocking sub tasks 

Finally the invoice is transformed (app/Transformers/) and returned as a response via Fractal.

### Developer environment

Using the Quick Hosting Setup describe above you can quickly get started building out your development environment. Instead of using 

```
composer i -o --no-dev
``` 

use

```
composer i -o
```

This provides the developer tools including phpunit which allows the test suite to be run.

If you are considering contributing back to the main repository, please add in any tests for new functionality / modifications. This will greatly increase the chances of your PR being accepted

Also, if you plan any additions for the main repository, you may want to discuss this with us first on Slack where we can assist with any technical information and provide advice.

## Credits
* [Hillel Coren](https://hillelcoren.com/)
* [David Bomba](https://github.com/turbo124)
* [Benjamin Beganović](https://github.com/beganovich)
* [All Contributors](https://github.com/invoiceninja/invoiceninja/graphs/contributors)


## Want More?
Checkout our other projects here!

[Event Schedule](https://www.eventschedule.com/)


## Security

If you find a security issue with this application, please send an email to contact@invoiceninja.com.
Please follow responsible disclosure procedures if you detect an issue.
For further information on responsible disclosure please read [here](https://cheatsheetseries.owasp.org/cheatsheets/Vulnerability_Disclosure_Cheat_Sheet.html).

## License
Invoice Ninja is released under the Elastic License.  
See [LICENSE](LICENSE) for details.


---

