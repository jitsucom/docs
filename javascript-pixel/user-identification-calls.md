# User identification calls

## Understanding user identification 

A user can have a multiple identifiers: e-mail address \(if user has logged in with it\), phone number, IDFA \(mobile advertising ID\) and so on. The same person can be represented with different IDs on different platforms. kSense collects those data to be able to match user id and apply cross-device optimization / attribution.

## User id object

User ID object is a JSON structure that describes user ids. It may contain multiple IDs based on multiple identification strategies. It's important to provide as many IDs as possible in order to make matching more accurate. 

There're two ways to send user id object to kSense. Through [JavaScript pixel](./) \([Tracking Call](./#example-with-additional-info) or dedicated [User Info](./#dedicated-user_info-calls) call\) or through server-2-server real-time API.

{% hint style="info" %}
**Note on PII \(Personally Identifiable Information\).** kSense never stores any personal information such as phone or e-mail on it's servers. If such information is passed without encryption, kSense will hash it a earliest stage possible and will store only hashed version
{% endhint %}

### User id object example

```javascript
{
  'internal_id': 'djgagd'
  'email': 'md5:036e32c9556cc5979a0ec187cb3d45b8',
  'phone': 'aes:MWKrIsbDoPiMeUD2mINLbg==',
  'idfa': '6d92078a-8246-4ba4-ae5b-76104861e7dc',
  'gaid': '38400000-8cf0-11bd-b23e-10b96e40000d'
}

```

### Parameters and encryption

Following parameters can be defined in JSON object:

| Name | Value |
| :--- | :--- |
| internal\_id | Internal id |
| email | User e-mail |
| phone | User phone |
| idfa | Apple's IDFA |
| gaid | Google Advertiser ID |

### Encryption

Sometimes passing PII information \(such as e-mail or phone\) is not desirable \(despite the fact that kSense will not store unencrypted version — see above\). For that cases each parameter can be passed encrypted. We support encryption for all parameters except internal\_id. 

If the value is encrypted, the string should be prefixed with md5: or aes: \(depending on encryption type\). Other val

#### Normalizing values before encryption

{% hint style="info" %}
It's very important to encrypt values in canonical version. Otherwise matching algorithms will not work. Please, read below
{% endhint %}

Before encryption values should be normalized:

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Name</b>
      </th>
      <th style="text-align:left"><b>Format</b>
      </th>
      <th style="text-align:left"><b>Valid</b>
      </th>
      <th style="text-align:left"><b>Invalid</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">email</td>
      <td style="text-align:left">Always lowercase</td>
      <td style="text-align:left">stevejobs@apple.com</td>
      <td style="text-align:left">SteveJobs@Apple.com</td>
    </tr>
    <tr>
      <td style="text-align:left">phone</td>
      <td style="text-align:left">Must not contain spaces, brackets and so on. Must contain a country code.</td>
      <td
      style="text-align:left">+19292649175</td>
        <td style="text-align:left">
          <p>(929)2659176</p>
          <p>+1929-265-9176</p>
          <p>920.265.9176</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>idfa / gaid</b>
      </td>
      <td style="text-align:left">String value in lowercase. Dash symbol should be present after first 4,
        6, 8 and 10 bytes</td>
      <td style="text-align:left">
        <p></p>
        <p>6d92078a-8246-4ba4-ae5b-76104861e7dc</p>
      </td>
      <td style="text-align:left">
        <p>6d92078a82464ba4ae5b76104861e7dc</p>
        <p></p>
        <p>6D92078A-8246-4BA4-AE5B-76104861E7DC</p>
      </td>
    </tr>
  </tbody>
</table>#### MD5

* The value is treated as ascii string and transformed to byte array
* Byte array is hashed with standard md5 algorithm

**AES**

* The value is treated as ascii string and transformed to byte array
* Byte array is hashed with standard AES algorithm with 16-bit encryption key. Encryption key is available in dataset properties \(in user interface\)



