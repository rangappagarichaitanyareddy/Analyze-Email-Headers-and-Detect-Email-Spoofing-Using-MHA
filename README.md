# Experiment No. 4: Analyze Email Headers and Detect Email Spoofing Using MHA

## Aim

To analyze an email header using Mail Header Analyzer (MHA) and detect possible email spoofing by examining email routing information and authentication results.

## Requirements

* Gmail / Outlook / Yahoo Mail
* Mail Header Analyzer (MHA)
* Web browser
* WHOIS / IP lookup tool
* Internet connection

## Procedure

### Step 1: Access the Email Header

**Gmail:**

1. Open the email.
2. Click the three-dot menu in the upper-right corner.
3. Select **Show original**.

**Outlook:**

1. Open the email.
2. Click **File**.
3. Select **Properties**.
4. Locate the **Internet headers** section.

**Yahoo:**

1. Open the email.
2. Click the three-dot menu.
3. Select **View raw message**.
<img width="1694" height="929" alt="image" src="https://github.com/user-attachments/assets/ead201d0-b743-4fb3-a40a-7c2c5a2a844e" />


### Step 2: Copy the Email Header

Copy the complete email header displayed by the email service.
<img width="1277" height="538" alt="image" src="https://github.com/user-attachments/assets/833950ab-0d70-44a0-a58c-ebba23a979b2" />


### Step 3: Analyze the Header Using MHA

1. Open Mail Header Analyzer.
2. Paste the copied email header into the analyzer.
3. Submit the header for analysis.
4. Examine the parsed header information.
5. Identify the `From`, `To`, `Return-Path`, `Received`, and `Message-ID` fields.
6. Check the SPF, DKIM, and DMARC authentication results.
<img width="1852" height="849" alt="image" src="https://github.com/user-attachments/assets/14152086-8755-4fd2-880a-491814427d84" />

### Step 4: Analyze the Received Fields

Examine the `Received` fields to determine:

* Sending server hostname
* Sending server IP address
* Receiving server
* Date and time of transmission
* Sequence of mail servers

The `Received` headers should be analyzed from the **bottom upward** to trace the email's path.
<img width="1883" height="835" alt="image" src="https://github.com/user-attachments/assets/2272653d-946a-44f0-93c6-d2373c5a320a" />


### Step 5: Check IP Addresses and Hostnames

Use an IP lookup or WHOIS tool to check the IP addresses found in the `Received` headers.

Verify whether:

* The IP belongs to the expected mail server.
* The hostname matches the IP address.
* The sending server appears legitimate.
* Any unexpected server or IP address is present.
<img width="1078" height="258" alt="image" src="https://github.com/user-attachments/assets/38ca86a4-b24f-4ff1-b394-6f61641fbecc" />
Step 6: Check SPF, DKIM, and DMARC
Record the authentication results.

| Check | Result    | Observation                                |
| ----- | --------- | ------------------------------------------ |
| SPF   | PASS/FAIL | Check whether the sending IP is authorized |
| DKIM  | PASS/FAIL | Check whether the DKIM signature is valid  |
| DMARC | PASS/FAIL | Check domain authentication and alignment  |
<img width="1600" height="734" alt="image" src="https://github.com/user-attachments/assets/392eb99b-d2c8-423a-bb17-012f552275d8" />
<img width="1200" height="384" alt="image" src="https://github.com/user-attachments/assets/fea5c06c-8ecb-4fef-b179-ec1d4149c60f" />
<img width="1600" height="750" alt="image" src="https://github.com/user-attachments/assets/a733a594-39ed-4dcf-bb31-d03d9a4d553d" />
<img width="1244" height="578" alt="image" src="https://github.com/user-attachments/assets/e2ada9f3-9998-406a-a8f9-751c3696d832" />
<img width="1251" height="581" alt="image" src="https://github.com/user-attachments/assets/6f185519-f6f3-413b-878f-ca543cf562a8" />

### Step 7: Analyze Message-ID

Check the domain used in the `Message-ID` and compare it with the sender's domain.
<img width="638" height="146" alt="image" src="https://github.com/user-attachments/assets/672d39b0-0239-42a1-8ac9-71dee8d02cd5" />


### Step 8: Identify Possible Spoofing Indicators

Check for:

* `From` and `Return-Path` domain mismatch
* Suspicious IP addresses
* Unexpected hostnames
* SPF failure
* DKIM failure
* DMARC failure
* Unusual timestamps
* Inconsistent mail-server routing
* Suspicious Message-ID domain
<img width="1600" height="311" alt="image" src="https://github.com/user-attachments/assets/92e7e968-0c88-42fd-8073-88b223226d40" />
<img width="1600" height="481" alt="image" src="https://github.com/user-attachments/assets/893305d7-ee08-4e8c-8bd6-4c5cf9c65fb6" />


## Observation

The email header was successfully parsed using MHA. The sender information, mail-server path, IP address, Message-ID, and email authentication results were examined for inconsistencies.

## Result

The email header was successfully analyzed using Mail Header Analyzer, and possible email spoofing indicators were identified by examining the **Received, Return-Path, Message-ID, SPF, DKIM, and DMARC** fields.

## Conclusion

Email header analysis using MHA can be used to trace the email's delivery path and identify inconsistencies that may indicate email spoofing or phishing.
