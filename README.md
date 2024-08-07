# tydids-jquery-consent
**JQuery extension for TyDIDs Self-Sovereign Identity and Consent Management**

Uses [TyDIDs-Core](https://github.com/energychain/tydids-core)

## Installation

```html
<script src=""/>
```

## Usage

```javascript
$('#consentCheck').tydisConsent(); // #consentCheck is ID of checkbox field for GDPR Constent
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
