# SRSG- Saudi Retina Group

Saudi Retina Group (SRG) is a scientific retina-specialized group under the umbrella of the Saudi Ophthalmology Society (SOS).

## Key Features:

- dashboard (managing tool) for the website, managed by admin 7 website dashboard (for users) to get them info.
- **User Authentication and Authorization:** Securely control access to the forum with user authentication and authorization.
   - There are 2 different authentications:
      1. User: has 2 types -> (SRS): Whose only went to the symposium, (SRG): Whose became a member in SRG and went to the symposium.
           - The user has access to the website dashboard to get his Profile, QR, certificate, and blogs(if he SRG member), and give feedback.
      3. Admin: has 4 types with different access -> 'moderator', 'Chairman', 'deputy', 'validator
  
- **Dynamic symposium which has:**
  1. **Details:** Like title, description, start and the end of the symposium, register, and abstract.
  2. **Abstract submission:** Easily create from the website and delete or manage the status from the dashboard.  
  3. **Schedule and Programs:** View from a website and manage it from the dashboard.
  4. **Manage Guest Speaker:** Add by a single page and manage from dashboard(edit,delete,accept,send certificate), And view in website.

- **Payment Gateway Integration:**
  1. Symposium features a secure and seamless payment gateway with **Paytabs** for users to join and also for enroll in courses.
  2.  **Subscription Management:** Admin can view all payment transactions.

-****

- [Installation](#2-installation)
- [Configuration](#3-configuration)
- [Usage](#4-usage)
- [Database](#5-database)
- [Models](#6-models)
- [Controllers](#7-controllers)
- [Views](#8-views)
- [Routes](#9-routes)
- [Middleware](#10-middleware)
- [Testing](#11-testing)
- [Troubleshooting](#12-troubleshooting)
- [Contributing](#13-contributing)
- [License](#14-license)
   

# 2-Package uses

### **First:** Laravel UI
Laravel provided bootstrap scaffolding located in the `laravel/ui` Composer package, which may be installed using Composer. Now we have to install laravel/ui package using the following command.
```bash
composer require laravel/ui
```
Once the laravel/ui package has been installed, you may install the frontend scaffolding using the ui Artisan command.

Run the bellow command to generate login / register scaffolding.

```bash
php artisan ui bootstrap --auth
```

****
### **Secound:** QR Code Package
Get into the command prompt, type the given command, and begin installing the [simplesoftwareio/simple-qrcode](https://github.com/Bacon/BaconQrCode) package; it profoundly helps create various kinds of QR codes in the Laravel app.

****
### **third:** Excel Extract
- use to extract all abstracts as a file Excel, [Laravel-excel-documentation](https://docs.laravel-excel.com/3.1/getting-started/).

****
### **4th:** JWT authentication
- use to make authentication Api, [Laravel-JWT-Authentication](https://www.positronx.io/laravel-jwt-authentication-tutorial-user-login-signup-api/).

****
### **5th:** Payment gateway (Paytabs)
- Start by looking forward to [Laravel Package Integration Manual](https://support.paytabs.com/en/support/solutions/articles/60000710700-laravel-package).
-  first get a paytabs account to integrate it with SRS project and follow the steps:
   1. Open the account from Developers -> key management -> Add new key
        - Create a new key with type standard API key
        - Then made the integration key that u created into **set as default signature key**
        - now u have **Server Key** and **Client Key**
   3. To manage the configuration you should look forward to `.env`
      ```shell
      paytabs_profile_id=Your-Profile-id
      paytabs_server_key=Server-key
      paytabs_currency=The-currency-you-registered-in-with-PayTabs-account---example:SAR
      paytabs_region=The-region-you-registered-in-with-PayTabs-account---example:SAU
      PAYTABS_MERCHANT_ID=from-profile
      PAYTABS_SECRET_KEY=Client-Key
      ```
 ****





