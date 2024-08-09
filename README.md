# tydids-jquery-consent
**jQuery extension for TyDIDs Self-Sovereign Identity and Consent Management**

A jQuery extension that simplifies the process of adding GDPR compliance to existing webforms. It allows web developers to easily integrate GDPR compliance into their existing forms using decentralized and self-sovereign identities. This extension solves the problem of allowing data providers (web users) to revoke consent given at a later time.

Uses [TyDIDs-Core](https://github.com/energychain/tydids-core)

Try on [JSFiddle](https://jsfiddle.net/stromdao/84gxfkts/1/)

## Features
- Easy to Use: tydids-jquery-consent provides a simple and intuitive API for adding GDPR compliance to your webforms.
- Transparent Implementation: The extension generates a Self-Sovereign Identity (SSI) for each user who checks the GDPR compliance box. This SSI allows the user to revoke consent at any time.
- No Third-Party Dependencies: tydids-jquery-consent is designed to be a standalone solution. It does not rely on any third-party frameworks or service providers.
- Backend Compatibility: The value of the GDPR compliance checkbox is changed to the Identity of the SSI. This allows the consent to be easily validated on the backend.

## Installation

```html
<script src="https://energychain.github.io/tydids-jquery-consent/dist/tydids-jquery-consent.js"/>
```

## Usage

### Getting Consent

```javascript
$('#consentCheck').tydisConsent(); // #consentCheck is ID of checkbox field for GDPR Constent
```

This will add the necessary functionality to the checkbox. When the user checks the box, an SSI will be generated and downloaded. The value of the checkbox will be changed to the Identity of the SSI.

### Checking revocation

#### CLI
```bash
npx tydids-core isgranted <identity>
```

#### Node JS 
```javascript
 const provider = new ethers.providers.JsonRpcProvider(env._RPC_URL);
  const bn = (await provider.getBlockNumber()).toString() * 1;
  let sc = new ethers.Contract(env._revokeContract, env._revokeAbi, provider);      
  let rcp = await sc.revocations(identity);
  let ts =  rcp.toString() * 1;   
  console.log("isGranted("+identity+")@Consensus:"+bn); 
  if(ts > 0) {
    console.log("Revoked at "+new Date(ts*1000).toISOString());
    process.exit(1);
  } else {
    sc = new ethers.Contract(env._publishContract, env._publishAbi, provider);      
    rcp = await sc.publishs(identity);
    ts =  rcp.toString() * 1;    
    console.log("Granted at "+new Date(ts*1000).toISOString());
    process.exit(0);
  }
```

For details check [TyDIDs-Core](https://github.com/energychain/tydids-core)

#### Rest API
```
https://api.corrently.io/v2.0/tydids/status?identity=<identity>
```

## Configuration

### Basic Usage
```html
<input class="form-check-input" type="checkbox" id="consentCheck" name="consentCheck" required="">
```

### Additional Attributes
```html
<input class="form-check-input" type="checkbox" id="consentCheck" name="consentCheck" required=""
       signature="signature" 
       payload="payload" 
       identity="identity" 
       submit="submit" >
```
`signature`, `payload` and `identity` might be the id of a hidden input field which will be filled after consent.
`submit` is the id of a button which will be "disabled" during consent creation.


## [License: Apache-2.0](./LICENSE)

## Maintainer / Impressum

<addr>
STROMDAO GmbH  <br/>
Gerhard Weiser Ring 29  <br/>
69256 Mauer  <br/>
Germany  <br/>
  <br/>
+49 6226 968 009 0  <br/>
  <br/>
dev@stromdao.com  <br/>
  <br/>
Handelsregister: HRB 728691 (Amtsgericht Mannheim)<br/>
  <br/>
https://stromdao.de/<br/>
</addr>
