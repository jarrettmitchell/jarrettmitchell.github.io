---
title: RIS Data Submission
tags: [featured]
---

When submitting data to RIS, it is recommended to send as much data as possible. As part of the RIS post there are required fields and if not populated an error will be returned in the RIS response. Please refer to the SDK documentation with details on how to submit the data for both optional and required fields.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;border-color:#ccc;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#ccc;color:#333;background-color:#fff;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#ccc;color:#333;background-color:#f0f0f0;}
.tg .tg-oq6y{background-color:#193d68;color:#ffffff;border-color:#000000;text-align:center;vertical-align:top}
.tg .tg-aa13{background-color:#f9f9f9;border-color:#000000;text-align:center;vertical-align:top}
.tg .tg-kcxh{background-color:#008699;color:#ffffff;border-color:#000000;text-align:left;vertical-align:middle}
.tg .tg-wp8o{border-color:#000000;text-align:center;vertical-align:top}
.tg .tg-ksh9{background-color:#193d68;color:#ffffff;border-color:#000000;text-align:center;vertical-align:top}
.tg .tg-i817{background-color:#f9f9f9;border-color:#000000;text-align:left;vertical-align:top}
.tg .tg-73oq{border-color:#000000;text-align:left;vertical-align:top}
.tg .tg-ret9{background-color:#008699;color:#ffffff;border-color:#000000;text-align:center;vertical-align:middle}
</style>
<table class="tg">
  <tr>
    <th class="tg-oq6y">﻿RIS Required Inquiry Key</th>
    <th class="tg-oq6y">Description</th>
    <th class="tg-oq6y">Max Field Length</th>
    <th class="tg-oq6y">Source</th>
    <th class="tg-oq6y">Required</th>
  </tr>
  <tr>
    <td class="tg-aa13">ANID</td>
    <td class="tg-i817">Automatic Number Identification (ANI) submitted with order. If the ANI cannot be determined, merchant must pass 0123456789 as the ANID. This field is only valid for MODE=P RIS submissions.</td>
    <td class="tg-aa13">32</td>
    <td class="tg-aa13">Merchant</td>
    <td class="tg-i817">MODE=P</td>
  </tr>
  <tr>
    <td class="tg-wp8o">AUTH</td>
    <td class="tg-73oq">Authorization Status returned to merchant from processor. Acceptable values for the AUTH field are ’A’ for Authorized or ’D’ for Decline. In orders where AUTH=A will aggregate towards order velocity of the persona while orders where AUTH=D will decrement the velocity of the persona.</td>
    <td class="tg-wp8o">1</td>
    <td class="tg-wp8o">Merchant</td>
    <td class="tg-73oq">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-aa13">CURR</td>
    <td class="tg-i817">Country of currency submitted on order</td>
    <td class="tg-aa13">3</td>
    <td class="tg-aa13">Merchant</td>
    <td class="tg-i817">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-wp8o">EMAL</td>
    <td class="tg-73oq">Email address submitted by customer. If a call center is accepting orders on behalf of customers and the customer does not provide an email address, noemail@Kount.com must be submitted. Kount currently supports 2 bit character sets. Unicode character sets are not supported at this time.</td>
    <td class="tg-wp8o">64</td>
    <td class="tg-wp8o">Merchant</td>
    <td class="tg-73oq">MODE=Q</td>
  </tr>
  <tr>
    <td class="tg-aa13">IPAD</td>
    <td class="tg-i817">Dotted Decimal IPv4 address that the merchant sees coming from the customer. If MODE=P or the Phone to Web exclusion is used, the IPAD field should be hard coded to be 10.0.0.1. Other than MODE=P or Phone to Web, the IPAD field should never be an anonymous IP address (i.e. 10.X.X.X or 192.168.X.X). IPv6 Addresses are not currently supported. Please use the IPv4 dual stack equivalent or pass 10.0.0.1 in the IPAD field if an IPv4 address is not available.</td>
    <td class="tg-aa13">16</td>
    <td class="tg-aa13">Merchant</td>
    <td class="tg-i817">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-wp8o">MACK</td>
    <td class="tg-73oq">Merchants acknowledgement to ship/process the order. The MACK field must be set as ’Y’ if persona data is to be collected to strengthen the score.</td>
    <td class="tg-wp8o">1</td>
    <td class="tg-wp8o">Merchant</td>
    <td class="tg-73oq">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-aa13">MERC</td>
    <td class="tg-i817">Merchant ID assigned to the merchant by Kount.</td>
    <td class="tg-aa13">6</td>
    <td class="tg-aa13">Merchant</td>
    <td class="tg-i817">MODE=Q MODE=P MODE=X MODE=U</td>
  </tr>
  <tr>
    <td class="tg-wp8o">MODE</td>
    <td class="tg-73oq">Specifies what mode type the RIS post is: -MODE - Q-MODE - P-MODE -U-MODE - X</td>
    <td class="tg-wp8o">1</td>
    <td class="tg-wp8o">Merchant</td>
    <td class="tg-73oq">MODE=Q MODE=P MODE=X MODE=U</td>
  </tr>
  <tr>
    <td class="tg-aa13">PROD_DESC</td>
    <td class="tg-i817">Shopping cart data array attribute for specific description of the item being purchased.-NOTE: Product description should not contain any markup or uniocode values. Non-alpha numeric characters will increment the character count exponetially depending on the special character used. RIS Post limits: There is a 40,960 character/byte limit that makes up an entire RIS post. Should the RIS post exceed the 40,960 byte limit, an HTTP standard error will be returned, typically an error code: 413 - Request Entity Too Large</td>
    <td class="tg-aa13">256</td>
    <td class="tg-aa13">Merchant</td>
    <td class="tg-i817">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-wp8o">PROD_ITEM</td>
    <td class="tg-73oq">Shopping cart data array attribute typically the SKU for an item; this value should be free from any markup or Unicode values. This value should be passed as plain text.</td>
    <td class="tg-wp8o">256</td>
    <td class="tg-wp8o">Merchant</td>
    <td class="tg-73oq">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-aa13">PROD_PRICE</td>
    <td class="tg-i817">Shopping cart data array attribute for the price of the single item. Must be a natural number including 0.</td>
    <td class="tg-aa13">no max</td>
    <td class="tg-aa13">Merchant</td>
    <td class="tg-i817">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-wp8o">PROD_QUANT</td>
    <td class="tg-73oq">Shopping cart data array attribute signifying the quantity of the item being purchased</td>
    <td class="tg-wp8o">no max</td>
    <td class="tg-wp8o">Merchant</td>
    <td class="tg-73oq">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-aa13">PROD_TYPE</td>
    <td class="tg-i817">Shopping cart data array attribute high level or generalized description of the item added to the shopping cart; this value should be free from any markup or Unicode values. This value should be passed as plain text.</td>
    <td class="tg-aa13">256</td>
    <td class="tg-aa13">Merchant</td>
    <td class="tg-i817">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-wp8o">PTOK</td>
    <td class="tg-73oq">Payment token submitted by merchant for order (credit card, payer ID, routing/transit, MICR, and account number). When using KHASH the BIN is extracted from the PTOK value, Last4 may be passed independently - it is lost during KHASH.</td>
    <td class="tg-wp8o">32</td>
    <td class="tg-wp8o">Merchant</td>
    <td class="tg-73oq">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-aa13">PTYP</td>
    <td class="tg-i817">Payment Type submitted by merchant - See below PTYP VALUES</td>
    <td class="tg-aa13">varies</td>
    <td class="tg-aa13">Merchant</td>
    <td class="tg-i817">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-ret9">PTYP VALUE</td>
    <td class="tg-kcxh" colspan="4">Description</td>
  </tr>
  <tr>
    <td class="tg-aa13">APAY</td>
    <td class="tg-i817">Apple Pay</td>
    <td class="tg-aa13" colspan="3" rowspan="20"></td>
  </tr>
  <tr>
    <td class="tg-wp8o">CARD</td>
    <td class="tg-73oq">Credit Card</td>
  </tr>
  <tr>
    <td class="tg-aa13">PYPL</td>
    <td class="tg-i817">PayPal</td>
  </tr>
  <tr>
    <td class="tg-wp8o">CHEK</td>
    <td class="tg-73oq">Check</td>
  </tr>
  <tr>
    <td class="tg-aa13">NONE</td>
    <td class="tg-i817">None</td>
  </tr>
  <tr>
    <td class="tg-wp8o">GDMP</td>
    <td class="tg-73oq">Green Dot Money Pack</td>
  </tr>
  <tr>
    <td class="tg-aa13">GOOG</td>
    <td class="tg-i817">Google Checkout</td>
  </tr>
  <tr>
    <td class="tg-wp8o">BLML</td>
    <td class="tg-73oq">Bill Me Later</td>
  </tr>
  <tr>
    <td class="tg-aa13">GIFT</td>
    <td class="tg-i817">Gift Card</td>
  </tr>
  <tr>
    <td class="tg-wp8o">BPAY</td>
    <td class="tg-73oq">Bpay</td>
  </tr>
  <tr>
    <td class="tg-aa13">NETELLER</td>
    <td class="tg-i817">Neteller</td>
  </tr>
  <tr>
    <td class="tg-wp8o">GIROPAY</td>
    <td class="tg-73oq">GiroPay</td>
  </tr>
  <tr>
    <td class="tg-aa13">ELV</td>
    <td class="tg-i817">ELV</td>
  </tr>
  <tr>
    <td class="tg-wp8o">MERCADE_PAGO</td>
    <td class="tg-73oq">Mercade Pago</td>
  </tr>
  <tr>
    <td class="tg-aa13">SEPA </td>
    <td class="tg-i817">Single Euro Payments Area</td>
  </tr>
  <tr>
    <td class="tg-wp8o">INTERAC</td>
    <td class="tg-73oq">Interac</td>
  </tr>
  <tr>
    <td class="tg-aa13">POLI</td>
    <td class="tg-i817">POLI</td>
  </tr>
  <tr>
    <td class="tg-wp8o">SKRILL</td>
    <td class="tg-73oq">Srkill/Moneybookers</td>
  </tr>
  <tr>
    <td class="tg-aa13">SOFORT</td>
    <td class="tg-i817">Sofort</td>
  </tr>
  <tr>
    <td class="tg-wp8o">TOKEN</td>
    <td class="tg-73oq">Token</td>
  </tr>
  <tr>
    <td class="tg-ksh9">RIS Required Inquiry Key</td>
    <td class="tg-ksh9">Description</td>
    <td class="tg-ksh9">Max Field Length</td>
    <td class="tg-ksh9">Source</td>
    <td class="tg-ksh9">Required</td>
  </tr>
  <tr>
    <td class="tg-wp8o">SESS</td>
    <td class="tg-73oq">Unique Session ID</td>
    <td class="tg-wp8o">32</td>
    <td class="tg-wp8o">Merchant</td>
    <td class="tg-73oq">MODE=Q MODE=P MODE=X MODE=U</td>
  </tr>
  <tr>
    <td class="tg-aa13">SITE</td>
    <td class="tg-i817">Website identifier of where order originated. Value must exist inside of the Agent Web Console prior to post.</td>
    <td class="tg-aa13">8</td>
    <td class="tg-aa13">Merchant</td>
    <td class="tg-i817">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-wp8o">TOTL</td>
    <td class="tg-73oq">Total amount in currency submitted in lowest currency factor. e.g. USD= pennies ($1.00 = 100). TOTL must be a natural number including 0.</td>
    <td class="tg-wp8o">15</td>
    <td class="tg-wp8o">Merchant</td>
    <td class="tg-73oq">MODE=Q MODE=P</td>
  </tr>
  <tr>
    <td class="tg-aa13">TRAN</td>
    <td class="tg-i817">Transaction ID required for update calls to Kount. MODE=U and MODE=X</td>
    <td class="tg-aa13"></td>
    <td class="tg-aa13">Kount</td>
    <td class="tg-i817">MODE=U MODE=X</td>
  </tr>
  <tr>
    <td class="tg-wp8o">VERS</td>
    <td class="tg-73oq">Specifies the version of Kount built into SDK, must be supplied by merchant if not using the SDK</td>
    <td class="tg-wp8o">4</td>
    <td class="tg-wp8o">Kount-Merchant</td>
    <td class="tg-73oq">MODE=Q MODE=P MODE=X MODE=U</td>
  </tr>
</table>

<table>
 <tr valign="bottom">
  <td><strong>RIS Required Inquiry Key</strong></td>
  <td><strong>Description</strong></td>
  <td><strong>Max Field Length</strong></td>
  <td><strong>Source</strong></td>
  <td><strong>Required</strong></td>
 </tr>
 <tr valign="top">
  <td>ANID</td>
  <td>Automatic Number Identification (ANI) submitted with order. If the ANI cannot be determined, merchant must pass 0123456789 as the ANID. This field is only valid for MODE=P RIS submissions.</td>
  <td>32</td>
  <td>Merchant</td>
  <td>MODE=P</td>
 </tr>
 <tr valign="top">
  <td>AUTH</td>
  <td>Authorization Status returned to merchant from processor. Acceptable values for the AUTH field are ’A’ for Authorized or ’D’ for Decline. In orders where AUTH=A will aggregate towards order velocity of the persona while orders where AUTH=D will decrement the velocity of the persona.</td>
  <td>1</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>CURR</td>
  <td>Country of currency submitted on order</td>
  <td>3</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>EMAL</td>
  <td>Email address submitted by customer. If a call center is accepting orders on behalf of customers and the customer does not provide an email address, <a href="mailto:noemail@Kount.com">noemail@kount.com</a> must be submitted. Kount currently supports 2-bit character sets. Unicode character sets are not supported at this time.</td>
  <td>64</td>
  <td>Merchant</td>
  <td>MODE=Q</td>
 </tr>
 <tr valign="top">
  <td>IPAD</td>
  <td>Dotted Decimal IPv4 address that the merchant sees coming from the customer. If MODE=P or the Phone to Web exclusion is used, the IPAD field should be hard coded to be 10.0.0.1. Other than MODE=P or Phone to Web, the IPAD field should never be an anonymous IP address (i.e. 10.X.X.X or 192.168.X.X). IPv6 Addresses are not currently supported. Please use the IPv4 dual stack equivalent or pass 10.0.0.1 in the IPAD field if an IPv4 address is not available.</td>
  <td>16</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>MACK</td>
  <td>Merchants acknowledgement to ship/process the order. The MACK field must be set as ’Y’ if persona data is to be collected to strengthen the score.</td>
  <td>1</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>MERC</td>
  <td>Merchant ID assigned to the merchant by Kount.</td>
  <td>6</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P<br />MODE=X<br />MODE=U</td>
 </tr>
 <tr valign="top">
  <td>MODE</td>
  <td>Specifies what mode type the RIS post is:<br />
      MODE=Q<br />
      MODE=P<br />
      MODE=X<br />
      MODE=U</td>
  <td>1</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P<br />MODE=X<br />MODE=U</td>
 </tr>
 <tr valign="top">
  <td>PROD_DESC</td>
  <td>Shopping cart data array attribute for specific description of the item being purchased.<br /><br /> Note: Product Descriptions should not contain any markup or unicode values. Non-alpha numeric characters will increment the character count exponentially depending on the special character used. RIS Post Limits: There is a 40,960 character/byte limit that makes up an entire RIS post. Should the RIS post exceed the 40,960 byte limit, an HTTP standard error will be returned, typically an error code: 413 - Request Entity Too Large.</td>
  <td>256</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>PROD_ITEM</td>
  <td>Shopping cart data array attribute typically the SKU for an item; this value should be free from any markup or Unicode values. This value should be passed as plain text.</td>
  <td>256</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>PROD_PRICE</td>
  <td>Shopping cart data array attribute for the price of the single item. Must be a natural number including 0.</td>
  <td>no max</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>PROD_QUANT</td>
  <td>Shopping cart array attribute signifying the quantity of the item being purchased.</td>
  <td>no max</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>PROD_TYPE</td>
  <td>Shopping cart data array attribute high level or generalized description of the item added to the shopping cart; this value should be free from any markup or Unicode values. This value should be passed as plain text.</td>
  <td>256</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>PTOK</td>
  <td>Payment token submitted by merchant for order (credit card, payer ID, routing/transit, MICR, and account number). When using KHASH the BIN is extracted from the PTOK value, Last4 may be passed independently - it is lost during KHASH.</td>
  <td>32</td>
  <td>Merchant</td>
  <td>MODE=Q<br />MODE=P</td>
 </tr>
 <tr valign="top">
  <td>PTYP</td>
  <td>Payment type submitted by merchant:<br />
      <table>
       <tr>
        <td><strong>PTYP Value</strong></td>
        <td><strong>Description</strong></td>
       </tr>
       <tr>
        <td>APAY</td>
        <td>Apple Pay</td>
       </tr>
       <tr>
        <td>CARD</td>
        <td>Credit card</td>
       </tr>
       <tr>
        <td>PYPL</td>
        <td>Paypal</td>
       </tr>
       <tr>
        <td>CHEK</td>
        <td>Check</td>
       </tr>
       <tr>
        <td>NONE</td>
        <td>None</td>
       </tr>
       <tr>
        <td>GDMP</td>
        <td>Green Dot Money Pack</td>
       </tr>
       <tr>
        <td>GOOG</td>
        <td>Google Checkout</td>
       </tr>
       <tr>
        <td>BLML</td>
        <td>Bill Me Later</td>
       </tr>
       <tr>
        <td>GIFT</td>
        <td>Gift card</td>
       </tr>
       <tr>
        <td>BPAY</td>
        <td>BPAY</td>
       </tr>
       <tr>
        <td>NETELLAR</td>
        <td>Netellar</td>
       </tr>
       <tr>
        <td>GIROPAY</td>
        <td>GiroPay</td>
       </tr>
       <tr>
        <td>ELV</td>
        <td>ELV</td>
       </tr>
       <tr>
        <td>MERCADE_PAGO</td>
        <td>Mercade Pago</td>
       </tr>
       <tr>
        <td>SEPA</td>
        <td>Single Euro Payments Area</td>
       </tr>
       <tr>
        <td>INTERAC</td>
        <td>Interac</td>
       </tr>
       <tr>
        <td>POLI</td>
        <td>POLi</td>
       </tr>
       <tr>
        <td>SKRILL</td>
        <td>Skrill/Moneybookers</td>
       </tr>
       <tr>
        <td>SOFORT</td>
        <td>Sofort</td>
       </tr>
       <tr>
        <td>TOKEN</td>
        <td>Token</td>
       </tr>
      </table>
     </td>
     <td>varies</td>
     <td>Merchant</td>
     <td>MODE=Q<br />MODE=P</td>
    </tr>
    <tr valign="top">
     <td>SESS</td>
     <td>Unique Session ID</td>
     <td>32</td>
     <td>Merchant</td>
     <td>MODE=Q<br />MODE=P<br />MODE=X<br />MODE=U</td>
    </tr>
    <tr valign="top">
     <td>SITE</td>
     <td>Website identifier of where order originated. Value must exist inside of the Agent Web Console prior to post.</td>
     <td>8</td>
     <td>Merchant</td>
     <td>MODE=Q<br />MODE=P</td>
    </tr>
    <tr valign="top">
     <td>TOTL</td>
     <td>Total amount in currency submitted in lowest currency factor. e.g. USD = pennies ($1.00 = 100). TOTL must be a natural number including 0.</td>
     <td>15</td>
     <td>Merchant</td>
     <td>MODE=Q<br />MODE=P</td>
    </tr>
    <tr valign="top">
     <td>TRAN</td>
     <td>Transaction ID required for update calls to Kount.</td>
     <td>&nbsp;</td>
     <td>Kount</td>
     <td>MODE=U<br />MODE=X</td>
    </tr>
    <tr valign="top">
     <td>VERS</td>
     <td>Specifies the version of Kount built into SDK; must be supplied by merchant if not using the SDK.</td>
     <td>4</td>
     <td>Kount-Merchant</td>
     <td>MODE=Q<br />MODE=P<br />MODE=X<br />MODE=U</td>
    </tr>
   </table>
