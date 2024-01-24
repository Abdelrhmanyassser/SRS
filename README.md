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
  1. Symposium features a secure and seamless payment gateway for users to join and also for enroll in courses.
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
### **third:** JWT authentication
- use to extract all abstracts as a file Excel, [Laravel-excel-documentation](https://docs.laravel-excel.com/3.1/getting-started/).







