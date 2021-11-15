# PayHere React JS example demo

This is a example for integrating PayHere with ReactJS

## Steps
1) Clone the project
2) npm install


## How to perform your own ReactJs - PayHere Integration.

### 1. In your `index.html` file, include the [PayHere JavaScript SDK](https://support.payhere.lk/api-&-mobile-sdk/payhere-javascript)

```html
<!doctype html>
<html lang="en">
<head>
  ...
  <!-- Add this line -->
  <script src="https://www.payhere.lk/lib/payhere.js"></script>
</head>
...
</html>

```

### 2. In your ReactJS code import PayHere object using window global object.

```js
 window.payhere.startPayment(payment_object);
```

### 3. Use the PayHere JS SDK normally.

Example:
```js
const payment_object = {
            "sandbox": true,
            "preapprove": true,
            "merchant_id": "1213098",    // Replace your Merchant ID
            "return_url": 'return url after payment',     // Important
            "cancel_url": 'cancel url when payment cancelled',     // Important
            "notify_url": "url to notify payment status and information",
            "order_id": "ItemNo12345",
            "items": "Door bell wireles",
            "amount": "1000.00",
            "currency": "LKR",
            "first_name": "Saman",
            "last_name": "Perera",
            "email": "samanp@gmail.com",
            "phone": "0771234567",
            "address": "No.1, Galle Road",
            "city": "Colombo",
            "country": "Sri Lanka",
            "delivery_address": "No. 46, Galle road, Kalutara South",
            "delivery_city": "Kalutara",
            "delivery_country": "Sri Lanka",
            "custom_1": "",
            "custom_2": ""
        };

 window.payhere.startPayment(payment_object);

        window.payhere.onCompleted = function onCompleted(orderId) {
            console.log("Payment completed. OrderID:" + orderId);
            alert("New Payhere payment: OrderID: " + orderId)
            //Note: validate the payment and show success or failure page to the customer
        };

        // Called when user closes the payment without completing
        window.payhere.onDismissed = function onDismissed() {
            //Note: Prompt user to pay again or show an error page
            console.log("Payment dismissed");
        };

        // Called when error happens when initializing payment such as invalid parameters
        window.payhere.onError = function onError(error) {
            // Note: show an error page
            console.log("Error:" + error);
        };
```
