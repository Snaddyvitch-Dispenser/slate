---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - json
  - shell
  - ruby
  - python
  - javascript
  - php
  
toc_footers:
  - <a href="https://getkey.steem.tools/guestposting">Get An API Key</a>

search: true
---

# Introduction

Welcome to the STEEM Guest Posting API! You can use our API to allow your users to post on the STEEM blockchain without an account.

We have limits and restrictions on our service which can be viewed at the bottom of this page.

We have language bindings in Shell, Ruby, Python, JavaScript and PHP! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Posting

## Publish A Post

Our main endpoint is */post*, which allows you to post to the STEEM blockchain. Here is the expected data format:

> POST /post

```json
{
    "body": "Content of your post....",
    "category": "first-tag",
    "title": "Title of the Post",
    "metadata": {"anything": "that is metadata"},
    "payout": "likwid",
    "beneficiaries": {"cadawg": 10000},
    "permlink": "not-the-final-permlink",
    "tags": ["first-tag", "second-tag", "third-tag", "fourth-tag", "fifth-tag", "sixth-tag"],
    "app": "GuestPosting",
    "community": "GuestPosting/v0.0.1",
    "user": "User Identifier",
    "key": "Your Key Here"
}
```

> Ruby net/http:

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.steem.tools/post")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Cache-Control"] = 'no-cache'
request.body = "{\r\n    \"body\": \"Content of your post....\",\r\n    \"category\": \"first-tag\",\r\n    \"title\": \"Title of the Post\",\r\n    \"metadata\": {\"anything\": \"that is metadata\"},\r\n    \"payout\": \"likwid\",\r\n    \"beneficiaries\": {\"cadawg\": 10000},\r\n    \"permlink\": \"not-the-final-permlink\",\r\n    \"tags\": [\"first-tag\", \"second-tag\", \"third-tag\", \"fourth-tag\", \"fifth-tag\", \"sixth-tag\"],\r\n    \"app\": \"GuestPosting\",\r\n    \"community\": \"GuestPosting/v0.0.1\",\r\n    \"user\": \"User Identifier\",\r\n    \"key\": \"Your Key Here\"\r\n}"

response = http.request(request)
puts response.read_body
```

> Python Requests

```python
import requests

url = "https://api.steem.tools/post"

payload = "{\r\n    \"body\": \"Content of your post....\",\r\n    \"category\": \"first-tag\",\r\n    \"title\": \"Title of the Post\",\r\n    \"metadata\": {\"anything\": \"that is metadata\"},\r\n    \"payout\": \"likwid\",\r\n    \"beneficiaries\": {\"cadawg\": 10000},\r\n    \"permlink\": \"not-the-final-permlink\",\r\n    \"tags\": [\"first-tag\", \"second-tag\", \"third-tag\", \"fourth-tag\", \"fifth-tag\", \"sixth-tag\"],\r\n    \"app\": \"GuestPosting\",\r\n    \"community\": \"GuestPosting/v0.0.1\",\r\n    \"user\": \"User Identifier\",\r\n    \"key\": \"Your Key Here\"\r\n}"
headers = {
    'Content-Type': "application/json",
    'Cache-Control': "no-cache"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Shell wget

```shell
wget --quiet \
  --method POST \
  --header 'Content-Type: application/json' \
  --header 'Cache-Control: no-cache' \
  --body-data '{\r\n    "body": "Content of your post....",\r\n    "category": "first-tag",\r\n    "title": "Title of the Post",\r\n    "metadata": {"anything": "that is metadata"},\r\n    "payout": "likwid",\r\n    "beneficiaries": {"cadawg": 10000},\r\n    "permlink": "not-the-final-permlink",\r\n    "tags": ["first-tag", "second-tag", "third-tag", "fourth-tag", "fifth-tag", "sixth-tag"],\r\n    "app": "GuestPosting",\r\n    "community": "GuestPosting/v0.0.1",\r\n    "user": "User Identifier",\r\n    "key": "Your Key Here"\r\n}' \
  --output-document \
  - https://api.steem.tools/post
```

> Javascript Requests

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.steem.tools/post',
  headers: 
   { 'Cache-Control': 'no-cache',
     'Content-Type': 'application/json' },
  body: 
   { body: 'Content of your post....',
     category: 'first-tag',
     title: 'Title of the Post',
     metadata: { anything: 'that is metadata' },
     payout: 'likwid',
     beneficiaries: { cadawg: 10000 },
     permlink: 'not-the-final-permlink',
     tags: 
      [ 'first-tag',
        'second-tag',
        'third-tag',
        'fourth-tag',
        'fifth-tag',
        'sixth-tag' ],
     app: 'GuestPosting',
     community: 'GuestPosting/v0.0.1',
     user: 'User Identifier',
     key: 'Your Key Here' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> PHP With cUrl

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.steem.tools/post",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => json_encode([
    "body"=> "Content of your post....",
    "category"=> "first-tag",
    "title"=> "Title of the Post",
    "metadata"=> ["anything"=> "that is metadata"],
    "payout"=> "likwid",
    "beneficiaries"=> ["cadawg"=> 10000],
    "permlink"=> "not-the-final-permlink",
    "tags"=> ["first-tag", "second-tag", "third-tag", "fourth-tag", "fifth-tag", "sixth-tag"],
    "app"=> "GuestPosting",
    "community"=> "GuestPosting/v0.0.1",
    "user"=> "User Identifier",
    "key"=> "Your Key Here"
]),
  CURLOPT_HTTPHEADER => array(
    "Cache-Control: no-cache",
    "Content-Type: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```


Parameter | Description
--- | ---
body | The content of your post in MarkDown/HTML/Text
category | Category (First Tag) of the post
title | Title of the post
metadata | Any custom metadata (tags, app, community will be overwritten by later values)
payout | The Payout method (always a string) - see below
beneficiaries | A dictionary of {"name": value}, where value includes 2 decimals as integers (100% = 10000)
permlink | Your part of the permalink that can be custom, we'll add the time and date of processing to make it unique (so make sure to use the link we return)
tags | An array of tags
app | The name of your app
community | Typically App and version, separated by `/`, but can be any value.
user (PRO Only) | A username/id for the guest who is posting to keep track of them and all their posts
key (PRO Only) | The API Key that you obtained as described below (PRO keys are free and offer reduced fees, in exchange for linking an account to be responsible)

<aside class="warning">
If the API is busy, you may recieve an error due to all our accounts being in use. This is due to the fact that accounts can only post every 5 minuites.
</aside>

### Payout Methods:
- 5050: Default Payout (50% STEEM & SBD, 50% SP)
- powerup: 100% Powerup
- likwid: Use likwid (1.5% fee) to recieve 100% liquid payout (100% STEEM/SBD)
- decline: Decline Curation Rewards, Send your share to null
- donate: 100% to our service as 5050
- null: Allow curation rewards, your share of post rewards to null
- steem.dao: Allow curation rewards, your share of post rewards to steem.dao

<aside class="warning">
If you want to do a custom payout between you and null or steem.dao, use the beneficiaries feature instead and choose your preferred payout above. Note: decline, donate, null and steem.dao all disable the "Beneficiaries" feature!
</aside>

### Pro Mode:

To obtain a pro key, visit the [web portal](https://getkey.steem.tools/guestposting), login with SteemConnect/Keychain as specified

Click "New Key" as arrowed below.

![Link of new key](https://i.imgur.com/DUxGmze.png)

Wait a few seconds, then the page will refresh. Copy the long string from a box (like the ones that are blurred out in the image above - you can have more than 1 key) and use that for the key field. And then you can use the key and user fields (both must be set for it to work).

# Terms of Service

Welcome to Guest Posting. These Terms of Service ("Terms") are a legal agreement between you and Steem Tools and related companies (the "Company", "us", "our", or "we") and you ("you" or "your"). By using this API, located at https://api.steem.tools/, which is collectively reffered to as the "Service" ("Service" or "Software"), You agree that you are over the age of majority in your judristriction or over, that you have read, understood and accept to be bound by the Terms.

1. THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

2. YOUR CONTENT - Any data, text, graphics, photographs and their selection and arrangement, and any other materials uploaded to the Service by you is “Your Content.” You represent and warrant that Your Content is original to you and that you exclusively own the rights to such content, including the right to grant all of the rights and licenses in these Terms without the Company incurring any third party obligations or liability arising out of its exercise of such rights and licenses. All of Your Content is your sole responsibility and the Company is not responsible for any material that you upload, post, or otherwise make available. By uploading, distributing, transmitting or otherwise using Your Content with the Service, you grant to us a perpetual, nonexclusive, transferable, royalty-free, sublicensable, and worldwide license to use, host, reproduce, modify, adapt, publish, translate, create derivative works from, distribute, perform, and display Your Content in connection with operating and providing the Service. The Company does not guarantee the accuracy, quality, or integrity of any user content posted. By using the Service, you acknowledge and accept that you may be exposed to material you find offensive or objectionable. You agree that the Company will not under any circumstances be liable for any user content, including, but not limited to, errors in any user content, or any loss or damage incurred by use of user content. The Company reserves the right to remove and permanently delete Your Content from the Service with or without notice for any reason or no reason. You may notify the Company of any user content that you believe violates these Terms, or other inappropriate user behavior, by emailing steem.abuse@steem.tools.

3.  The Service provides communication channels such as posts and comments on the STEEM Blockchain ("Communication Channels") designed to enable you to communicate with other STEEM users. The Company has no obligation to monitor these communication channels but it may do so in connection with providing the Service. The Company may also terminate or suspend your access to any Communication Channels at any time, without notice, for any reason. You acknowledge that any user content (including without limitation chats, postings, or materials posted by users) on the Communication Channels is neither endorsed nor controlled by us. The Company will not under any circumstances be liable for any activity within Communication Channels. The Company is not responsible for information that you choose to share on the Communication Channels, or for the actions of other users. As a condition of your use of the Service, and without limiting your other obligations under these Terms, you agree to comply with the restrictions and rules of use set forth in these Terms and our Community Guidelines as well as any additional restrictions or rules (such as application-specific rules) set forth in the Service. As an example, you agree not to use the Service in order to:

  - post, upload, transmit or otherwise disseminate information that is objectionable;
  - defame, libel, ridicule, mock, stalk, threaten, harass, intimidate or abuse anyone;
  - engage in conduct that is fraudulent or illegal or otherwise harmful to Steem Tools or any other user;
    upload or transmit (or attempt to upload or transmit) files that contain viruses, Trojan horses, worms, time bombs, cancelbots, corrupted files or data, or any other similar software or programs or engage in any other activity that may damage the operation of the Service or other users' computers;
  - violate the contractual, personal, intellectual property or other rights of any party including using, uploading, transmitting, distributing, or otherwise making available any information made available through the Service in any manner that infringes any copyright, trademark, patent, trade secret, or other right of any party (including rights of privacy or publicity);
  - attempt to obtain passwords or other private information from other members;
    improperly use support channels or complaint buttons to make false reports to us;
    develop, distribute, or publicly inform other members of "auto" software programs, "macro" software programs or other "cheat utility" software program or applications in violation of the applicable license agreements; or
  - exploit, distribute or publicly inform other members of any game error, miscue or bug which gives an unintended advantage; violate any applicable laws or regulations; or promote or encourage illegal activity including, but not limited to, hacking, cracking or distribution of counterfeit software, compromised accounts, or cheats or hacks for the Service.

4. These rules of use are not meant to be exhaustive, and we reserve the right to determine what conduct we consider to be a violation of the Terms, Community Guidelines or improper use of the Service and to take action including termination of your Account and exclusion from further participation in the Service.

5. You are solely responsible for your interaction with other users of the Service and other parties that you come in contact with through the Service. The Company hereby disclaims any and all liability to you or any third party relating to your use of the Service. The Company reserves the right, but has no obligation, to manage disputes between you and other users of the Service.

6. We may adjust the cut we take of a post at any time for any reason on either Anonymous or Pro accounts. Generally notice will be given for increases via the @guestaccounts account or any other means of contact, but they are not necessary. Examples of reasons we may change it include: Increased Operation Fees, Increased Spam/Low Quality Posts or Lower Post Rewards.

7. We will log the following data upon a successful request: the input you provided, the output generated, the requester's ip address, (pro: the app's name, the username provided) and the time of the successful finished request! You agree we can store this data for an unlimited amount of time (due to the fact that STEEM posts are around forever, and can't be truly deleted).
