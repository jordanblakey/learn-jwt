#JWT - JSON Web Token Examples

JWT - JSON Web Token
Open standard for passing claims (security information) between two parties
- Self-contained: carries all the information necessary within itself
- JSON object on its own
- Not secure for passwords and other sensitive information by default, BUT, no one can tamper with the data without invalidation of the token

Mainly used in web applications (or services)
- Can be used in Javascript, Node.js, Java, .Net, Python, PHP, Ruby, etc.
- Can be used/passed as part of URL (Query string), form body parameter, cookie or HTTP Header (x-access-token)
- Great for single sign-on context

## JWT - Structure
```
abcabcabc.mnomnomno.xyzxyzxyz
header.payload.signature
{
    "iss": "ABC Service App",
    "name": "Jag",
    "admin": false
}
```

```
iss - issuer
sub - subject
aud - audience
exp - expiration time
nbf - not before
iat - issued at
jti - JWT id
```

```
var s = base64Encode(header)
        + "."
        + base64Encode(payload);
var signature = hasAlgHs256(s, 'secret');

var jwt = s + "." + base64Encode(signature)
```

- Three sections separated with dots
  - **header**, **payload**, and **signature**
  - All are base64 encoded (NOT ECRYPTED)

- Header - usually contains 2 parts, in the form of JSON
  - typ - should be JWT
  - alg - hashing algorithm (HS256, RS512, ES384, etc.)

- Payload
  - Contains
    - The information we need to transmit
    - The information related to the token itself
    - Information is JSON representation of claims (key:value)

- Signature
  - A hash of **header** and **payload** using a **secret**
