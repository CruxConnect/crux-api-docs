---
title: /organizations/subscription/
name: Get Subscription
position: 1.7
visibility:
method: get
description: Get Subscription with details for your organization
right_code: |
  ~~~ json
  {
    "plan_name": "This is a plan",
    "available_add_ons": [
      "other plan name 1",
      "other plan name 2"
    ],
    "plan_features": [
      "feature1",
      "feature2"
    ],
    "plan_add_ons": [
      "add_on1",
      "add_on2"
    ],
    "next_bill_plan": {
      "bill_date": "2017-11-06",
      "amount": "10.99",
      "start_date": "2017-11-06",
      "end_date": "2017-11-06",
      "card_last_four": "4897"
    }
  }
  ~~~
  {: title="Response" }

---
Get Subscription details for your organization including the plan name, available add-ons, plan features, and next bill plan.

To view your organization plan, you must be assigned the 'view_org_subscription_plan' permission
{: .info }

### Response Parameters:

plan_name
: (string) Plan Name is the name of the Subscription Plan

available_add_ons
: (list) Available Add-ons are the other Subscription Plans available. These are optional Subscriptions you could subscribe to. The displayed Add-ons change depending upon organization type, whether a retailer or supplier.

plan_features
: (list) Plan Features are the Features specific to your current Subscription Plan. The displayed Features change depending upon organization type, whether a retailer or supplier.

plan_addons
: (list) Plan Add-ons are Products or Services which may be added to your current Subscription Plan. These are optional Services you may subscribe to. The displayed Add-ons change depending upon the current Subscription Plan and organization type, whether a retailer or supplier.

next_bill_plan
: (object) Next Bill Plan object contains the billing date, amount to be billed, start date, end date, and last 4 digits of the credit card being billed for the Subscription

#### Next Bill Plan Object:

bill_date
: Billing Date when the account will renew

amount
: Amount is the billing amount due on the Billing Date

start_date
: Start Date is the Date when the account started on the current Subscription

end_date
: End Date is the Date when the account Subscription is complete

card_last_four
: (string) Last Four digits of the credit Card being billed for this Subscription

{% include v1/links/response_codes.md %}


~~~ bash
curl "https://api-sandbox.cruxconnect.com/organizations/subscription/" \
     -H 'Authorization: Token 47d4yfbwymedhiudj384702984nakju4hajh395d'

~~~
{: title="Curl" }

~~~ bash
http GET 'https://api-sandbox.cruxconnect.com/organizations/subscription/' \
    'Authorization':'Token 47d4yfbwymedhiudj384702984nakju4hajh395d'

~~~
{: title="HTTPie" }

~~~ python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Get Subscription
    # GET https://api-sandbox.cruxconnect.com/organizations/subscription/

    try:
        response = requests.get(
            url="https://api-sandbox.cruxconnect.com/organizations/subscription/",
            headers={
                "Authorization": "Token 47d4yfbwymedhiudj384702984nakju4hajh395d",
            },
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')

~~~
{: title="Python (requests)" }

~~~ javascript
// request Get Subscription
(function(callback) {
    'use strict';

    const httpTransport = require('https');
    const responseEncoding = 'utf8';
    const httpOptions = {
        hostname: 'api-sandbox.cruxconnect.com',
        port: '443',
        path: '/organizations/subscription/',
        method: 'GET',
        headers: {"Authorization":"Token 47d4yfbwymedhiudj384702984nakju4hajh395d"}
    };
    httpOptions.headers['User-Agent'] = 'node ' + process.version;


    const request = httpTransport.request(httpOptions, (res) => {
        let responseBufs = [];
        let responseStr = '';

        res.on('data', (chunk) => {
            if (Buffer.isBuffer(chunk)) {
                responseBufs.push(chunk);
            }
            else {
                responseStr = responseStr + chunk;
            }
        }).on('end', () => {
            responseStr = responseBufs.length > 0 ?
                Buffer.concat(responseBufs).toString(responseEncoding) : responseStr;

            callback(null, res.statusCode, res.headers, responseStr);
        });

    })
    .setTimeout(0)
    .on('error', (error) => {
        callback(error);
    });
    request.write("")
    request.end();


})((error, statusCode, headers, body) => {
    console.log('ERROR:', error);
    console.log('STATUS:', statusCode);
    console.log('HEADERS:', JSON.stringify(headers));
    console.log('BODY:', body);
});

~~~
{: title="Node.js" }
