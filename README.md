# SRG- Saudi Retina Group

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


# 2-Main Topics

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

   4. the main object to create a get page gateway payment to paytabs
       ```php
       $pay = paypage::sendPaymentCode('all')
            ->sendTransaction('sale','ecom')
            ->sendCart($card_id,$card_price,$card_description)
            ->sendCustomerDetails($name, $email, $phone, $street1 = null, $city = null, $state = null, $country = null, $zip = null, $ip= null)
            ->sendShippingDetails('true', $name, $email, $phone, null, $city = null, $state = null, $country = null, $zip = null, $ip = null)
            ->sendHideShipping($on = true)
            ->sendURLs($return , $callbackApi)
            ->sendLanguage('en')
            ->sendFramed($on = false)
            ->create_pay_page(); // to initiate payment page
        return $pay ;
      ```
      - U can get details and explanations for each method from this [document](https://support.paytabs.com/en/support/solutions/articles/60000778145-step-3-laravel-package-initiating-the-payment).
      - **Note:** the method `sendTransaction()` has 2 parameters
           - **First:** takes only `sale` or `auth`
           - **Second:** Takes only `ecom` or `recurring`

- How did handle the payment functions in the project?
     - In the trait `PaymentTrait`  
     1. Function `paymentPage()` is used to get the payment page
           - called if from enroll courses `CourseController`->`enroll()` or join srs `PaymentController`->`joinSRSPayment()`.
           - **Note:** The `card_description` used for taking a string like "srs,course,2" means: srs: to join srs, course: enroll course id = 2.
     - In the `PaymentController`
     2. Function `respondMethodPaymentApi()` is a callback API (server to server)
           - Save the transaction details with all status
           -  split the description as I note and check if srs save as a join srs and if it course: enroll as a course
     3. Function `messageReturn()` is return client (server to client)
           - Just return to the message page view if it is successful or not
     4. Function `messageReturnBtn()` return to the profile page with an updated status
           - Its a button action on the message page
           - users to update user state 
     
 ****





