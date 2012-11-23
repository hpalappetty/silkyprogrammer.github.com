---
layout: post
title: 'Adding Google CheckOut to your App (Python + Django)'

---

Adding Google Checkout to a Django based e-commerce application is very easy. In order to help with this integration, Google has provided a good sandbox as well. The following are two important links that needs to be there in your hand in-order to complete the integration of Google Checkout.

Link 1 : https://sandbox.google.com/checkout/
Link 2 : https://developers.google.com/checkout/developer/

Steps :

1. You have a Django Application, preferably listing certain products. This means that you have a model (Product) in your project.
2. You have set up appropriates urls in (urls.py) and other configurations in settings (settings.py), please note Google checkout has nothing to do with these files, they are listed so that the developer can re-check and ensure everything is working in their respective project/app.

3. Type Link 1 into your web browser and register yourself for a seller account in Sandbox ( This is only for development purposes and it will not process the payment requests. You need to use the actual Google Checkout link for production which is <a title="Google Checkout" href="https://checkout.google.com" target="_blank">https://checkout.google.com</a>)

4. After completing the registration, select tools section and click on "Buy Now" button option, select the "Basic Button" option initially ( you can customize it later) and fill in the necessary details and click "Create button Code". This will generate the necessary <em><strong>&lt;html&gt;</strong></em> required to embed Google Checkout in your application. Copy this html into your templates ( listing template/details template based on your requirements). Replace value with appropriate Django language such as {{ object.description }} .

HTML for Google Checkout Button may look like this (after placing appropriate Django syntax) :

[sourcecode language="css"]&lt;/pre&gt;
&lt;form id=&quot;BB_BuyButtonForm&quot; action=&quot;https://sandbox.google.com/checkout/api/checkout/v2/checkoutForm/Merchant/812345597672176&quot; method=&quot;post&quot; name=&quot;BB_BuyButtonForm&quot; target=&quot;_top&quot;&gt;&lt;input type=&quot;hidden&quot; name=&quot;item_name_1&quot; value=&quot;{{ object.name }}&quot; /&gt;
&lt;input type=&quot;hidden&quot; name=&quot;item_description_1&quot; value=&quot;{{ object.description }}&quot; /&gt;
&lt;input type=&quot;hidden&quot; name=&quot;item_quantity_1&quot; value=&quot;1&quot; /&gt;
&lt;input type=&quot;hidden&quot; name=&quot;item_price_1&quot; value=&quot;{{ object.price_in_dollars }}&quot; /&gt;
&lt;input type=&quot;hidden&quot; name=&quot;item_currency_1&quot; value=&quot;GBP&quot; /&gt;
&lt;input type=&quot;hidden&quot; name=&quot;_charset_&quot; value=&quot;utf-8&quot; /&gt;
&lt;input type=&quot;image&quot; src=&quot;https://sandbox.google.com/checkout/buttons/buy.gif?merchant_id=812345597672176&amp;w=117&amp;h=48&amp;style=white&amp;variant=text&amp;loc=en_US&quot; alt=&quot;&quot; /&gt;&lt;/form&gt;
&lt;pre&gt;
[/sourcecode]

5. Restart your server by running python manage.py runserver command.

6. Go to your web-browser and type in http://localhost:8000/[your-url] to see the results. (This applies only if you are working on local, if you are deploying remotely please replace <em><strong>localhost</strong></em> with appropriate servername &amp; port address).
