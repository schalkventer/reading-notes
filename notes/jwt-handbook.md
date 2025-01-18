JWT Handbook (2016)

Sebastián Peyrott

---

▪ JSON Web Token, or JWT (“jot”) for short, is a standard for safely passing claims in space constrained environments. It has found its way into all major web frameworks.

▪ A JSON Web Token looks like this (newlines inserted for readability): eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9. eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9. TJVA95OrM7E2cBab30RMHrHDcEfxjoYZgeFONFh7HgQ

▪ While this looks like gibberish, it is actually a very compact, printable representation of a series of claims, along with a signature to verify its authenticity. { "alg": "HS256", "typ": "JWT" } { "sub": "1234567890", "name": "John Doe", "admin": true }

▪ Claims are definitions or assertions made about a certain party or object. Some of these claims and their meaning are defined as part of the JWT spec. Others are user defined.

▪ The magic behind JWTs is that they standardize certain claims that are useful in the context of some common operations. For example, one of these common operations is establishing the identity of certain party. So one of the standard claims found in JWTs is the sub (from “subject”) claim. We will take a deeper look at each of the standard claims in chapter 3.

▪ Another key aspect of JWTs is the possiblity of signing them, using JSON Web Signatures (JWS, RFC 7515), and/or encrypting them, using JSON Web Encryption (JWE, RFC 7516). Together with JWS and JWE, JWTs provide a powerful, secure solution to many different problems.

▪ Although the main purpose of JWTs is to transfer claims between two parties,

▪ arguably the most important aspect of this is the standardization effort in the form of a simple, optionally validated and/or encrypted, container format. Ad hoc solutions to this same problem have been implemented both privately and publicly in the past. Older standards for establishing claims about certain parties are also available. What JWT brings to the table is a simple, useful, standard container format.

▪ The JSON Object Signing and Encryption group (JOSE) was formed in the year 2011. The group’s objective was to “standardize the mechanism for integrity protection (signature and MAC) and encryption as well as the format for keys and algorithm identifiers to support interoperability of security services for protocols that use JSON”.

▪ By year 2013 a series of drafts, including a cookbook with different examples of the use of the ideas produced by the group, were available. These drafts would later become the JWT, JWS, JWE, JWK and JWA RFCs. As of year 2016, these RFCs are in the standards track process and errata have not been found in them. The group is currently inactive.

▪ Be aware that the following demonstrations are not meant to be used in production. Test cases, logging, and security best practices are all essential for production-ready code. These samples are for educational purposes only and thus remain simple and to the point.

▪ Client-side data is subject to tampering. As such it must be handled with great care by the backend.

▪ JWTs, by virtue of JWS and JWE, can provide various types of signatures and encryption. Signatures are useful to validate the data against tampering. Encryption is useful to protect the data from being read by third parties.

▪ Most of the time sessions need only be signed. In other words, there is no security or privacy concern when data stored in them is read by third parties. A common example of a claim that can usually be safely read by third parties is the sub claim (“subject”). The subject claim usually identifies one of the parties to the other (think of user IDs or emails). It is not a requirement that this claim be unique. In other words, additional claims may be required to uniquely identify a user. This is left to the users to decide.

▪ A claim that may not be appropriately left in the open could be an “items” claim representing a user’s shopping cart. This cart might be filled with items that the user is about to purchase and thus are associated to his or her session. A third party (a client-side script) might be able to harvest these items if they are stored in an unencrypted JWT, which could raise privacy concerns.

▪ A common method for attacking a signed JWT is to simply remove the signature.

▪ Signed JWTs are constructed from three different parts: the header, the payload, and the signature. These three parts are encoded separately. As such, it is possible to remove the signature and then change the header to claim the JWT is unsigned.

▪ Careless use of certain JWT validation libraries can result in unsigned tokens being taken as valid tokens, which may allow an attacker to modify the payload at his or her discretion. This is easily solved by making sure that the application that performs the validation does not consider unsigned JWTs valid.

▪ Cross-site request forgery attacks attempt to perform requests against sites where the user is logged in by tricking the user’s browser into sending a request from a different site. To accomplish this, a specially crafted site (or item) must contain the URL to the target.

▪ A common example is an ￼ tag embedded in a malicious page with the src pointing to the attack’s target. For instance: ￼

▪ If the user had previously logged in to target.site.com and the site used a cookie to keep the session active, this cookie will be sent as well. If the target site does not implement any CSRF mitigation techniques, the request will be handled as a valid request on behalf of the user. JWTs, like any other client-side data, can be stored as cookies.

▪ Short-lived JWTs can help in this case. Common CSRF mitigation techniques include special headers that are added to requests only when they are performed from the right origin, per session cookies, and per request tokens

▪ If JWTs (and session data) are not stored as cookies, CSRF attacks are not possible. Cross-site scripting attacks are still possible, though

▪ Cross-site scripting (XSS) attacks attempt to inject JavaScript in trusted sites. Injected JavaScript can then steal tokens from cookies and local storage. If an access token is leaked before it expires, a malicious user could use it to access protected resources.

▪ Common XSS attacks are usually caused by improper validation of data passed to the backend (in similar fashion to SQL injection attacks).

▪ If the backend does not sanitize the comments, a malicious user could write a comment in such a way that it could be interpreted by the browser as a tag. So, a malicious user could insert arbitrary JavaScript code and execute it in every user’s browser, thus, stealing credentials stored as cookies and in local storage.

▪ Mitigation techniques rely on proper validation of all data passed to the backend. In particular, any data received from clients must always be sanitized. If cookies are used, it is possible to protect them from being accessed by JavaScript by setting the HttpOnly flag.

▪ The HttpOnly flag, while useful, will not protect the cookie from CSRF attacks.

▪ There are pros and cons to any approach, and client-side sessions are not an exception. Some applications may require big sessions. Sending this state back and forth for every request (or group of requests) can easily overcome the benefits of the reduced chattiness in the backend. A certain balance between client-side data and database lookups in the backend is necessary.

▪ This depends on the data model of your application. Some applications do not map well to client-side sessions. Others may depend entirely on client-side data.

▪ The final word on this matter is your own! Run benchmarks, study the benefits of keeping certain state client-side. Are the JWTs too big? Does this have an impact on bandwidth? Does this added bandwidth overthrow the reduced latency in the backend? Can small requests be aggregated into a single bigger request?

▪ In this example, there are multiple JWTs present. Our shopping cart will be one of them. One JWT for the ID token, a token that carries the user’s profile information, useful for the UI. One JWT for interacting with the API backend (the access token). One JWT for our client-side state: the shopping cart.

▪ Note that the frontend does not check the signature, it simply decodes the JWT so it can display its contents. The actual checks are performed by the backend. All JWTs are verified.

▪ Here is the backend check for the validity of the cart JWT implemented as an Express middleware: function cartValidator(req, res, next) { if(!req.cookies.cart) { req.cart = { items: [] }; } else { try { req.cart = { items: jwt.verify(req.cookies.cart, process.env.AUTH0_CART_SECRET, cartVerifyJwtOptions).items }; } catch(e) { req.cart = { items: [] }; } } next(); }

▪ When items are added, the backend constructs a new JWT with the new item in it and a new signature: app.get('/protected/add_item', idValidator, cartValidator, (req, res) => { req.cart.items.push(parseInt(req.query.id)); const newCart = jwt.sign(req.cart, process.env.AUTH0_CART_SECRET, cartSignJwtOptions); res.cookie('cart', newCart, { maxAge: 1000 * 60 * 60 }); res.end(); console.log(`Item ID ${req.query.id} added to cart.`); });

▪ 2.2 Federated Identity Federated identity systems allow different, possibly unrelated, parties to share authentication and authorization services with other parties. In other words, a user’s identity is centralized. There are several solutions for federated identity management: SAML and OpenID Connect are two of the most common ones.

▪ Certain companies provide specialized products that centralize authentication and authorization. These may implement one of the standards mentioned above or use something completely different. Some of these companies use JWTs for this purpose.

▪ Common Federated Identity Flow The user attempts to access a resource controlled by a server. The user does not have the proper credentials to access the resource, so the server redirects the user to the authorization server. The authorization server is configured to let users log-in using the credentials managed by an identity provider. The user gets redirected by the authorization server to the identity’s provider log-in screen. The user logs-in successfully and gets redirected to the authorization server. The authorization server uses the credentials provided by the identity provider to access the credentials required by the resource server. The user gets redirected to the resource server by the authorization server. The request now has the correct credentials required to access the resource. The user gets access to the resource successfully.

▪ Access and refresh tokens are two types of tokens you will see a lot when analyzing different federated identity solutions. We will briefly explain what they are and how they help in the context of authentication and authorization.

▪ Both concepts are usually implemented in the context of the OAuth2 specification. The OAuth2 spec defines a series of steps necessary to provide access to resources by separating access from ownership (in other words, it allows several parties with different access levels to access the same resource). Several parts of these steps are implementation defined. That is, competing OAuth2 implementations may not be interoperable. For instance, the actual binary format of the tokens is not specified. Their purpose and functionality is.

▪ Access tokens are tokens that give those who have them access to protected resources. These tokens are usually short-lived and may have an expiration date embedded in them. They may also carry or be associated with additional information (for instance, an access token may carry the IP address from which requests are allowed). This additional data is implementation defined.

▪ Refresh tokens, on the other hand, allow clients to request new access tokens. For instance, after an access token has expired, a client may perform a request for a new access token to the authorization server. For this request to be satisfied, a refresh token is required. In contrast to access tokens, refresh tokens are usually long-lived.

▪ The key aspect of the separation between access and refresh tokens lies in the possibility of making access tokens easy to validate. An access token that carries a signature (such as a signed JWT) may be validated by the resource server on its own. There is no need to contact the authorization server for this purpose.

▪ Refresh tokens, on the other hand, require access to the authorization server. By keeping validation separate from queries to the authorization server, better latency and less complex access patterns are possible. Appropriate security in case of token leaks is achieved by making access tokens as short-lived as possible and embedding additional checks (such as client checks) into them.

▪ Refresh tokens, by virtue of being long-lived, must be protected from leaks. In the event of a leak, blacklisting may be necessary in the server (short-lived access tokens force refresh tokens to be used eventually, thus protecting the resource after it gets blacklisted and all access tokens are expired).

▪ Note: the concepts of access token and refresh token were introduced in OAuth2. OAuth 1.0 and 1.0a use the word token differently.

▪ Although OAuth2 makes no mention of the format of its tokens, JWTs are a good match for its requirements. Signed JWTs make good access tokens, as they can encode all the necessary data to differentiate access levels to a resource, can carry an expiration date, and are signed to avoid validation queries against the authorization server. Several federated identity providers issue access tokens in JWT format.

▪ JWTs may also be used for refresh tokens. There is less reason to use them for this purpose, though. As refresh tokens require access to the authorization server, most of the time a simple UUID will suffice, as there is no need for the token to carry a payload (it may be signed, though).

▪ 2.2.3 JWTs and OpenID Connect OpenID Connect is a standardization effort to bring typical use cases of OAuth2 under a common, well-defined spec. As many details behind OAuth2 are left to the choice of implementers, OpenID Connect attempts to provide proper definitions for the missing parts. Specifically, OpenID Connect defines an API and data format to perform OAuth2 authorization flows. Additionally, it provides an authentication layer built on top of this flow. The data format chosen for some of its parts is JSON Web Token. In particular, the ID token is a special type of token that carries information about the authenticated user.

▪ OpenID Connect defines several flows which return data in different ways. Some of this data may be in JWT format. 

▪ Authorization flow: the client requests an authorization code to the authorization endpoint (/authorize). This code can be used againt the token endpoint (/token) to request an ID token (in JWT format), an access token or a refresh token.

▪ Implicit flow: the client requests tokens directly from the authorization endpoint (/authorize). The tokens are specified in the request. If an ID token is requested, is is returned in JWT format.

▪ Hybrid flow: the client requests both an authorization code and certain tokens from the authorization endpoint (/authorize). If an ID token is requested, it is returned in JWT format. If an ID token is not requested at this step, it may later by requested directly from the token endpoint (/token).

▪ Setting up the Auth0 library can be done as follows. We will use the same example used for the stateless sessions example: const auth0 = new window.auth0.WebAuth({ domain: domain, clientID: clientId, audience: 'app1.com/protected', scope: 'openid profile purchase', responseType: 'id_token token', redirectUri: 'http://app1.com:3000/auth/', responseMode: 'form_post' }); // (...) $('#login-button').on('click', function(event) { auth0.authorize({ prompt: 'none' }); }); Note the use of the prompt: 'none' parameter for the authorize call. The authorize call redirects the user to the authorization server. With the none parameter, if the user has already given authorization for an app to use his or her credentials for access to a protected resource, the authorization server will simply redirect back to the application. This looks to the user as if he were already logged-in in the app.

▪ In our example, there are two apps: app1.com and app2.com. Once a user has authorized both apps (which happens only once: the first time the user logs-in), any subsequent logins to any of both apps will also allow the other app to login without presenting any login screens.

▪ As described in chapter 1, all JWTs are constructed from three different elements: the header, the payload, and the signature/encryption data. The first two elements are JSON objects of a certain structure. The third is dependent on the algorithm used for signing or encryption, and, in the case of unencrypted JWTs it is omitted. JWTs can be encoded in a compact representation known as JWS/JWE Compact Serialization.

▪ The JWS and JWE specifications define a third serialization format known as JSON Serialization, a non-compact representation that allows for multiple signatures or recipients in the same JWT. Is is explained in detail in chapters 4 and 5.

▪ JWT uses a variant of Base64 encoding that is safe for URLs. This encoding basically substitutes the “+” and “/” characters for the “-” and “_" characters, respectively. Padding is removed as well. This variant is known as base64url. Note that all references to Base64 encoding in this document refer to this variant.

▪ Notice the dots separating the three elements of the JWT (in order: the header, the payload, and the signature).

▪ In this example the decoded header is: { "alg": "HS256", "typ": "JWT" } The decoded payload is: { "sub": "1234567890", "name": "John Doe", "admin": true } And the secret required for verifying the signature is secret.

▪ Every JWT carries a header (also known as the JOSE header) with claims about itself. These claims establish the algorithms used, whether the JWT is signed or encrypted, and in general, how to parse the rest of the JWT.

▪ According to the type of JWT in question, more fields may be mandatory in the header. For instance, encrypted JWTs carry information about the cryptographic algorithms used for key encryption and content encryption. These fields are not present for unencrypted JWTs. The only mandatory claim for an unencrypted JWT header is the alg claim: alg: the main algorithm in use for signing and/or decrypting this JWT.

▪ For unencrypted JWTs this claim must be set to the value none. Optional header claims include the typ and cty claims:

▪ typ: the media type of the JWT itself. This parameter is only meant to be used as a help for uses where JWTs may be mixed with other objects carrying a JOSE header. In practice, this rarely happens. When present, this claim should be set to the value JWT.

▪ cty: the content type. Most JWTs carry specific claims plus arbitrary data as part of their payload. For this case, the content type claim must not be set. For instances where the payload is a JWT itself (a nested JWT), this claim must be present and carry the value JWT. This tells the implementation that further processing of the nested JWT is required. Nested JWTs are rare, so the cty claim is rarely present in headers.

▪ So, for unencrypted JWTs, the header is simply: { "alg": "none" } which gets encoded to: eyJhbGciOiJub25lIn0

▪ It is possible to add additional, user-defined claims to the header. This is generally of limited use, unless certain user-specific metadata is required in the case of encrypted JWTs before decryption.

▪ { "sub": "1234567890", "name": "John Doe", "admin": true } The payload is the element where all the interesting user data is usually added. In addition, certain claims defined in the spec may also be present. Just like the header, the payload is a JSON object. No claims are mandatory, although specific claims have a definite meaning. The JWT spec specifies that claims that are not understood by an implementation should be ignored. The claims with specific meanings attached to them are known as registered claims.

▪ iss: from the word issuer. A case-sensitive string or URI that uniquely identifies the party that issued the JWT. Its interpretation is application specific (there is no central authority managing issuers).

▪ sub: from the word subject. A case-sensitive string or URI that uniquely identifies the party that this JWT carries information about. In other words, the claims contained in this JWT are statements about this party. The JWT spec specifies that this claim must be unique in the context of the issuer or, in cases where that is not possible, globally unique. Handling of this claim is application specific.

▪ aud: from the word audience. Either a single case-sensitive string or URI or an array of such values that uniquely identify the intended recipients of this JWT. In other words, when this claim is present, the party reading the data in this JWT must find itself in the aud claim or disregard the data contained in the JWT. As in the case of the iss and sub claims, this claim is application specific.

▪ exp: from the word expiration (time). A number representing a specific date and time in the format “seconds since epoch” as defined by POSIX. This claims sets the exact moment from which this JWT is considered invalid. Some implementations may allow for a certain skew between clocks (by considering this JWT to be valid for a few minutes after the expiration date).

▪ nbf: from not before (time). The opposite of the exp claim. A number representing a specific date and time in the format “seconds since epoch” as defined by POSIX. This claim sets the exact moment from which this JWT is considered valid. The current time and date must be equal to or later than this date and time. Some implementations may allow for a certain skew.

▪ iat: from issued at (time). A number representing a specific date and time (in the same format as exp and nbf) at which this JWT was issued.

▪ jti: from JWT ID. A string representing a unique identifier for this JWT. This claim may be used to differentiate JWTs with other similar content (preventing replays, for instance). It is up to the implementation to guarantee uniqueness.

▪ All claims that are not part of the registered claims section are either private or public claims.

▪ Private claims: are those that are defined by users (consumers and producers) of the JWTs. In other words, these are ad hoc claims used for a particular case. As such, care must be taken to prevent collisions.

▪ Public claims: are claims that are either registered with the IANA JSON Web Token Claims registry (a registry where users can register their claims and thus prevent collisions), or named using a collision resistant name (for instance, by prepending a namespace to its name).

▪ With what we have learned so far, it is possible to construct unsecured JWTs. These are the simplest JWTs, formed by a simple (usually static) header: { "alg": "none" } and a user defined payload. For instance: { "sub": "user123", "session": "ch72gsb320000udocl363eofy", "name": "Pretty Name", "lastpage": "/views/settings" }

▪ In practice, however, unsecured JWTs are rare.

▪ To arrive at the compact representation from the JSON versions of the header and the payload, perform the following steps: Take the header as a byte array of its UTF-8 representation. The JWT spec does not require the JSON to be minified or stripped of meaningless characters (such as whitespace) before encoding. Encode the byte array using the Base64-URL algorithm, removing trailing equal signs (=). Take the payload as a byte array of its UTF-8 representation. The JWT spec does not require the JSON to be minified or stripped of meaningless characters (such as whitespace) before encoding. Encode the byte array using the Base64-URL algorithm, removing trailing equal signs (=). Concatenate the resulting strings, putting first the header, followed by a “.” character, followed by the payload.

▪ To arrive at the JSON representation from the compact serialization form, perform the following steps: Find the first period “.” character. Take the string before it (not including it.) Decode the string using the Base64-URL algorithm. The result is the JWT header. Take the string after the period from step 1. Decode the string using the Base64-URL algorithm. The result is the JWT payload.

▪ JSON Web Signatures are probably the single most useful feature of JWTs. By combining a simple data format with a well-defined series of signature algorithms, JWTs are quickly becoming the ideal format for safely sharing data between clients and intermediaries

▪ The purpose of a signature is to allow one or more parties to establish the authenticity of the JWT. Authenticity in this context means the data contained in the JWT has not been tampered with. In other words, any party that can perform a signature check can rely on the contents provided by the JWT. It is important to stress that a signature does not prevent other parties from reading the contents inside the JWT. This is what encryption is meant to do, and we will talk about that later in chapter 5.

▪ The process of checking the signature of a JWT is known as validation or validating a token. A token is considered valid when all the restrictions specified in its header and payload are satisfied.

▪ Signed JWTs are defined in the JSON Web Signature spec, RFC 7515.

▪ A signed JWT is composed of three elements: the header, the payload, and the signature (newlines inserted for readability):

▪ eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9. eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9. TJVA95OrM7E2cBab30RMHrHDcEfxjoYZgeFONFh7HgQ

▪ The process for decoding the first two elements (the header and the payload) is identical to the case of unsecured JWTs.

▪ Signed JWTs, however, carry an additional element: the signature. This element appears after the last dot (.) in the compact serialization form.

▪ There are several types of signing algorithms available according to the JWS spec, so the way these octets are interpreted varies. The JWS specification requires a single algorithm to be supported by all conforming implementations: HMAC using SHA-256, called HS256 in the JWA spec.

▪ The specification also defines a series of recommended algorithms: RSASSA PKCS1 v1.5 using SHA-256, called RS256 in the JWA spec. ECDSA using P-256 and SHA-256, called ES256 in the JWA spec.

▪ JWA is the JSON Web Algorithms spec, RFC 7518.

▪ The other algorithms supported by the spec, in optional capacity, are: HS384, HS512: SHA-384 and SHA-512 variations of the HS256 algorithm. RS384, RS512: SHA-384 and SHA-512 variations of the RS256 algorithm. ES384, ES512: SHA-384 and SHA-512 variations of the ES256 algorithm. PS256, PS384, PS512: RSASSA-PSS + MGF1 with SHA256/384/512 variants.

▪ These are, essentially, variations of the three main required and recommended algorithms. The meaning of these acronyms will become clearer in chapter 7.

▪ In order to discuss these algorithms in general, let’s first define some functions in a JavaScript 2015 environment:

▪ base64

▪ utf8

▪ JSON.stringify:

▪ sha256

▪ hmac

▪ rsassa

▪ For HMAC-based signing algorithms: const encodedHeader = base64(utf8(JSON.stringify(header))); const encodedPayload = base64(utf8(JSON.stringify(payload))); const signature = base64(hmac(`${encodedHeader}.${encodedPayload}`, secret, sha256)); const jwt = `${encodedHeader}.${encodedPayload}.${signature}`;

▪ For public-key signing algorithms: const encodedHeader = base64(utf8(JSON.stringify(header))); const encodedPayload = base64(utf8(JSON.stringify(payload))); const signature = base64(rsassa(`${encodedHeader}.${encodedPayload}`, privateKey, sha256)); const jwt = `${encodedHeader}.${encodedPayload}.${signature}`;

▪ All signing algorithms accomplish the same thing: they provide a way to establish the authenticity of the data contained in the JWT. How they do that varies.

▪ Keyed-Hash Message Authentication Code (HMAC) is an algorithm that combines a certain payload with a secret using a cryptographic hash function. The result is a code that can be used to verify a message only if both the generating and verifying parties know the secret. In other words, HMACs allow messages to be verified through shared secrets.

▪ The cryptographic hash function used in HS256, the most common signing algorithm for JWTs, is SHA-256. SHA-256 is explained in detail in chapter 7. Cryptographic hash functions take a message of arbitrary length and produce an output of fixed length. The same message will always produce the same output. The cryptographic part of a hash function makes sure that it is mathematically infeasible to recover the original message from the output of the function. In this way, cryptographic hash functions are one-way functions that can be used to identify messages without actually sharing the message.

▪ RSASSA is a variation of the RSA algorithm (explained in chapter 7) adapted for signatures. RSA is a public-key algorithm. Public-key algorithms generate split keys: one public key and one private key. In this specific variation of the algorithm, the private key can be used both to create a signed message and to verify its authenticity. The public key, in contrast, can only be used to verify the authenticity of a message. Thus, this scheme allows for the secure distribution of a one-to-many message. Receiving parties can verify the authenticity of a message by keeping a copy of the public key associated with it, but they cannot create new messages with it. This allows for different usage scenarios than shared-secret signing schemes such as HMAC. With HMAC + SHA-256, any party that can verify a message can also create new messages. For example, if a legitimate user turned malicious, he or she could modify messages without the other parties noticing. With a public-key scheme, a user who turned malicious would only have the public key in his or her possession and so could not create new signed messages with it.

▪ For instance, using a variation of the same RSA algorithm, it is possible to encrypt messages by using the public key. These messages can only be decrypted using the private key. This allows a many-to-one secure communications channel to be constructed. This variation is used for encrypted JWTs, which are discussed in 

▪ Elliptic Curve Digital Signature Algorithm (ECDSA) is an alternative to RSA. This algorithm also generates a public and private key pair, but the mathematics behind it are different. This difference allows for lesser hardware requirements than RSA for similar security guarantees

▪ What follows is the list of registered header claims available for JWS tokens. All of these claims are in addition to those available for unsecured JWTs, and are optional depending on how the signed JWT is meant to be used.

▪ jku: JSON Web Key (JWK) Set URL. A URI pointing to a set of JSON-encoded public keys used to sign this JWT. Transport security (such as TLS for HTTP) must be used to retrieve the keys. The format of the keys is a JWK Set (see chapter 6).

▪ jwk: JSON Web Key. The key used to sign this JWT in JSON Web Key format (see chapter 6).

▪ kid: Key ID. A user-defined string representing a single key used to sign this JWT. This claim is used to signal key signature changes to recipients (when multiple keys are used).

▪ x5u

▪ x5c

▪ x5t

▪ x5t#S256

▪ typ

▪ crit

▪ The JWS spec defines a different type of serialization format that is not compact. This representation allows for multiple signatures in the same signed JWT. It is known as JWS JSON Serialization.

▪ In JWS JSON Serialization form, signed JWTs are represented as printable text with JSON format (i.e., what you would get from calling JSON.stringify in a browser). A topmost JSON object that carries the following key-value pairs is required: payload: a Base64 encoded string of the actual JWT payload object. signatures: an array of JSON objects carrying the signatures. These objects are defined below.

▪ In turn, each JSON object inside the signatures array must contain the following key-value pairs:

▪ protected: a Base64 encoded string of the JWS header. Claims contained in this header are protected by the signature. This header is required only if there are no unprotected headers. If unprotected headers are present, then this header may or may not be present.

▪ header: a JSON object containing header claims. This header is unprotected by the signature. If no protected header is present, then this element is mandatory. If a protected header is present, then this element is optional.

▪ signature: A Base64 encoded string of the JWS signature.

▪ In contrast to compact serialization form (where only a protected header is present), JSON serialization admits two types of headers: protected and unprotected. The protected header is validated by the signature. The unprotected header is not validated by it. It is up to the implementation or user to pick which claims to put in either of them. At least one of these headers must be present. Both may be present at the same time as well.

▪ When both protected and unprotected headers are present, the actual JOSE header is built from the union of the elements in both headers. No duplicate claims may be present.

▪ JWS JSON serialization defines a simplified form for JWTs with only a single signature. This form is known as flattened JWS JSON serialization. Flattened serialization removes the signatures array and puts the elements of a single signature at the same level as the payload element.

▪ Using signed JWTs is simple enough in practice that you could apply the concepts explained so far to use them effectively. Furthermore, there are good libraries you can use to implement them conveniently.

▪ The following examples all make use of the popular jsonwebtoken JavaScript library.

▪ HMAC signatures require a shared secret. Any string will do: const secret = 'my-secret'; const signed = jwt.sign(payload, secret, { algorithm: 'HS256', expiresIn: '5s' // if ommited, the token will not expire }); Verifying the token is just as easy: const decoded = jwt.verify(signed, secret, { // Never forget to make this explicit to prevent // signature stripping attacks algorithms: ['HS256'], }); 

▪ The jsonwebtoken library checks the validity of the token based on the signature and the expiration date. In this case, if the token were to be checked after 5 seconds of being created, it would be considered invalid and an exception would be thrown.

▪ Signing and verifying RS256 signed tokens is just as easy. The only difference lies in the use of a private/public key pair rather than a shared secret. There are many ways to create RSA keys. OpenSSL is one of the most popular libraries for key creation and management:

▪ // You can get this from private_key.pem above. const privateRsaKey = `<YOUR-PRIVATE-RSA-KEY>`; const signed = jwt.sign(payload, privateRsaKey, { algorithm: 'RS256', expiresIn: '5s' }); // You can get this from public_key.pem above. const publicRsaKey = `<YOUR-PUBLIC-RSA-KEY>`; const decoded = jwt.verify(signed, publicRsaKey, { // Never forget to make this explicit to prevent // signature stripping attacks. algorithms: ['RS256'], });

▪ ECDSA algorithms also make use of public keys. The math behind the algorithm is different, though, so the steps to generate the keys are different as well. The “P-256” in the name of this algorithm tells us exactly which version of the algorithm to use (more details about this in chapter 7). We can use OpenSSL to generate the key as well:

▪ If you open these files you will note that there is much less data in them. This is one of the benefits of ECDSA over RSA (more about this in chapter 7). The generated files are in PEM format as well, so simply pasting them in your source will suffice.

▪ // You can get this from private_key.pem above. const privateEcdsaKey = `<YOUR-PRIVATE-ECDSA-KEY>`; const signed = jwt.sign(payload, privateEcdsaKey, { algorithm: 'ES256', expiresIn: '5s' }); // You can get this from public_key.pem above. const publicEcdsaKey = `<YOUR-PUBLIC-ECDSA-KEY>`; const decoded = jwt.verify(signed, publicEcdsaKey, { // Never forget to make this explicit to prevent // signature stripping attacks. algorithms: ['ES256'], });

▪ While JSON Web Signature (JWS) provides a means to validate data, JSON Web Encryption (JWE) provides a way to keep data opaque to third parties.

▪ Opaque in this case means unreadable. Encrypted tokens cannot be inspected by third parties. This allows for additional interesting use cases.

▪ The shared secret scheme works by having all parties know a shared secret. Each party that holds the shared secret can both encrypt and decrypt information. This is analogous to the case of a shared secret in JWS: parties holding the secret can both verify and generate signed tokens.

▪ The public/private-key scheme, however, works differently. While in JWS the party holding the private key can sign and verify tokens, and the parties holding the public key can only verify those tokens, in JWE the party holding the private key is the only party that can decrypt the token. In other words, public-key holders can encrypt data, but only the party holding the private-key can decrypt (and encrypt) that data. In practice, this means that in JWE, parties holding the public key can introduce new data into an exchange.

▪ In contrast, in JWS, parties holding the public-key can only verify data but not introduce new data. In straightforward terms, JWE does not provide the same guarantees as JWS and, therefore, does not replace the role of JWS in a token exchange. JWS and JWE are complementary when public/private key schemes are being used.

▪ The following examples show how to perform encryption using the popular node-jose library. This library is a bit more complex than jsonwebtoken (used for the JWS examples), as it covers much more ground.

▪ For the purposes of the following examples, we will need to use encryption keys in various forms. This is managed by node-jose through a keystore. A keystore is an object that manages keys. We will generate and add a few keys to our keystore so that we can use them later in the examples. You might recall from JWS examples that such an abstraction was not required for the jsonwebtoken library. The keystore abstraction is an implementation detail of node-jose. You may find other similar abstractions in other languages and libraries.

▪ To create an empty keystore and add a few keys of different types: // Create an empty keystore const keystore = jose.JWK.createKeyStore(); // Generate a few keys. You may also import keys generated from external // sources. const promises = [ keystore.generate('oct', 128, { kid: 'example-1' }), keystore.generate('RSA', 2048, { kid: 'example-2' }), keystore.generate('EC', 'P-256', { kid: 'example-3' }), ];

▪ With node-jose, key generation is a rather simple matter. All key types usable with JWE and JWS are supported. In this example we create three different keys: a simple AES 128-bit key, a RSA 2048-bit key, and an Elliptic Curve key using curve P-256. These keys can be used both for encryption and signatures. In the case of keys that support public/private-key pairs, the generated key is the private key. To obtain the public keys, simply call: var publicKey = key.toJSON();

▪ You have probably noted that there are many references to this chapter throughout this handbook. The reason is that a big part of the magic behind JWTs lies in the algorithms employed with it. Structure is important, but the many interesting uses described so far are only possible due to the algorithms in play.

▪ The following algorithms have many different applications inside the JWT, JWS, and JWE specs. Some algorithms, like Base64-URL, are used for compact and non-compact serialization forms. Others, such as SHA-256, are used for signatures, encryption, and key fingerprints.

▪ The Secure Hash Algorithm (SHA) used in the JWT specs is defined in FIPS-180. It is not to be confused with the SHA-1 family of algorithms, which have been deprecated since 2010. To differentiate this family from the previous one, this family is sometimes called SHA-2.

▪ The algorithms in RFC 4634 are SHA-224, SHA-256, SHA-384, and SHA-512. Of importance for JWT are SHA-256 and SHA-512. We will focus on the SHA-256 variant and explain its differences with regard to the other variants.

▪ The SHA family of algorithms were designed to avoid collisions and produce radically different output even when the input is only slightly changed. It is for this reason they are considered secure: it is computationally infeasible to find collisions for different inputs, or to compute the original input from the produced digest.

▪ Other variants of the SHA-2 family (such as SHA-512) simply change the size of the block processed in each iteration and alter the constants and their size. In particular, SHA-512 requires 64-bit math to be available. In other words, to turn the sample implementation above into SHA-512, a separate library for 64-bit math is required (as JavaScript only supports 32-bit bitwise operations and 64-bit floating-point math).

▪ HMAC Hash-based Message Authentication Codes (HMAC) make use of a cryptographic hash function (such as the SHA family discussed above) and a key to create an authentication code for a specific message. In other words, a HMAC-based authentication scheme takes a hash function, a message, and a secret-key as inputs and produces an authentication code as output. The strength of the cryptographic hash function ensures that the message cannot be modified without the secret key. Thus, HMACs serve both purposes of authentication and data integrity.

▪ Weak hash functions may allow malicious users to compromise the validity of the authentication code. Therefore, for HMACs to be of use, a strong hash function must be chosen. The SHA-2 family of functions is still strong enough for today’s standards, but this may change in the future. MD5, a different cryptographic hash function used extensively in the past, can be used for HMACs. However, it can be vulnerable to collision and prefix attacks. 

▪ Although these attacks do not necessarily make MD5 unsuitable for use with HMACs, stronger algorithms are readily available and should be considered.

▪ To verify a message against an HMAC, one simply computes the HMAC and compares the result with the HMAC that came with the message. This requires knowledge of the secret-key by all parties: those who produce the message, and those who only want to verify it.

▪ Understanding Base64-URL, SHA-256, and HMAC are all that is needed to implement the HS256 signing algorithm from the JWS specification. With this is mind, we can now combine all the sample code developed so far and construct a fully signed JWT.

▪ export default function jwtEncode(header, payload, secret) { if(typeof header !== 'object' || typeof payload !== 'object') { throw new Error('header and payload must be objects'); } if(typeof secret !== 'string') { throw new Error("secret must be a string"); } header.alg = 'HS256'; const encHeader = b64(JSON.stringify(header)); const encPayload = b64(JSON.stringify(payload)); const jwtUnprotected = `${encHeader}.${encPayload}`; const signature = b64(uint32ArrayToUint8Array( hmac(sha256, 512, secret, stringToUtf8(jwtUnprotected), true))); return `${jwtUnprotected}.${signature}`; }

▪ Note that this function performs no validation of the header or payload (other than checking to see if they are objects). You can call this function like this: console.log(jwtEncode({}, {sub: "test@test.com"}, 'secret')); Paste the generated JWT in JWT.io’s debugger and see how it gets decoded and validated.

▪ const encodedHeader = base64(utf8(JSON.stringify(header))); const encodedPayload = base64(utf8(JSON.stringify(payload))); const signature = base64(hmac(`${encodedHeader}.${encodedPayload}`, secret, sha256)); const jwt = `${encodedHeader}.${encodedPayload}.${signature}`; Verification is just as easy: export function jwtVerifyAndDecode(jwt, secret) { if(!isString(jwt) || !isString(secret)) { throw new TypeError('jwt and secret must be strings'); } const split = jwt.split('.'); if(split.length !== 3) { throw new Error('Invalid JWT format'); } const header = JSON.parse(unb64(split[0])); if(header.alg !== 'HS256') { throw new Error(`Wrong algorithm: ${header.alg}`); } const jwtUnprotected = `${split[0]}.${split[1]}`; const signature = b64(hmac(sha256, 512, secret, stringToUtf8(jwtUnprotected), true)); return { header: header, payload: JSON.parse(unb64(split[1])), valid: signature == split[2] };

▪ The signature is split from the JWT and a new signature is computed. If the new signature matches the one included in the JWT, then the signature is valid.

▪ RSA is one of the most widely used cryptosystems today. It was developed in 1977 by Ron Rivest, Adi Shamir and Leonard Adleman, whose initials were used to name the algorithm

▪ The key aspect of RSA lies in its asymmetry: the key used to encrypt something is not the key used to decrypt it. This scheme is known as public-key encryption (PKI), were the public key is the encryption key and the private key is the decryption key.

▪ Shor’s algorithm is a special kind of factoring algorithm that could change things drastically in the future. While most factoring algorithms are classical in nature (that is, they operate on classical computers), Shor’s algorithm relies on quantum computers. Quantum computers take advantage of the nature of certain quantum phenomena to speed up several classical operations. In particular, Shor’s algorithm could speed up factorization, bringing its complexity into the realm of polynomial time complexity (rather than exponential). This is much more efficient than any of the current classical algorithms. It is speculated that if such algorithm were to be runnable on a quantum computer, current RSA keys would become useless. A practical quantum computer as required by Shor’s algorithm has not been developed yet, but this is an acive area of research at the moment.

▪ Although currently integer factorization is computationally infeasible for large semiprimes, there is no mathematical proof that this should be the case. In other words, in the future there might appear algorithms that solve integer factorization in reasonable timeframes. The same can be said of RSA.

▪ OpenSSL can also be used to generate a RSA key from scratch:

▪ Since their release, JWTs have been used in many different places. This has exposed JWTs, and library implementations, to a number of attacks. We have mentioned some of them in the preceding chapters. In this section we will take a look at the current best practices for working with JWTs.

▪ This section is based on the draft for JWT Best Current Practices from the IETF OAuth Working Group. The version of the draft used in this section is 00, dated July 19, 2017.

▪ Before taking a look at the first attack, it is important to note that many of these attacks are related to the implementation, rather than the design, of JSON Web Tokens. This does not make them less critical. It is arguable whether some of these attacks could be mitigated, or removed, by changing the underlying design.

▪ For the moment, the JWT specification and format is set in stone, so most changes happen in the implementation space (changes to libraries, APIs, programming practices and conventions).

▪ It is also important to have a basic idea of the most common representation for JWTs: the JWS Compact Serialization format. Unserialized JWTs have two main JSON objects in them: the header and the payload.

▪ The header object contains information about the JWT itself: the type of token, the signature or encryption algorithm used, the key id, etc.

▪ The payload object contains all the relevant information carried by the token. There are several standard claims, like sub (subject) or iat (issued at), but any custom claims can be included as part of the payload.

▪ These objects are encoded using the JWS Compact Serialization format to produce something like this: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9. eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ. XbPfbIHMI6arZ3Y922BhjWgQzWXcXNrz0ogtVhfEd2o

▪ This is a signed JWT. Signed JWTs in compact format are simply the header and payload objects encoded using Base64-URL encoding and separated by a dot (.). The last part of the compact representation is the signature. In other words, the format is: [Base64-URL encoded header].[Base64-URL encoded payload].[Signature]

▪ This only applies to signed tokens. Encrypted tokens have a different serialized compact format that also relies on Base64-URL encoding and dot-separated fields.

▪ Signed JWTs sign both the header and the payload, while encrypted JWTs only encrypt the payload (the header must always be readable).

▪ Now, since this is a signed token, we are free to read it. This also means we could construct a similar token with slightly changed data in it, although in that case we would not be able to sign it unless we knew the signing key.

▪ In the past, many libraries relied on this claim to pick the verification algorithm, and, as you may have guessed, in our malicious token the alg claim is none. That means that there’s no verification algorithm, and the verification step always succeeds.

▪ For this reason, many libraries today report "alg": "none" tokens as invalid, even though there’s no signature in place. There are other possible mitigations for this type of attack, the most important one being to always check the algorithm specified in the header before attempting to verify a token. Another one is to use libraries that require the verification algorithm as an input to the verification function, rather than rely on the alg claim.

▪ This attack is similar to the "alg": "none" attack and also relies on ambiguity in the API of certain JWT libraries.

▪ We can now clearly see the problem, the token will be considered valid! The public key will get passed to the jwtDecode function as the second argument, but rather than being used as a public key for the RS256 algorithm, it will be used as a shared secret for the HS256 algorithm. This is caused by the jwtDecode function relying on the alg claim from the header to pick the verification algorithm for the JWT. And the attacker changed that: header: { "alg": "HS256", // <-- changed by the attacker from RS256 "typ": "JWT" } Just like in the "alg": "none" case, relying on the alg claim combined with a bad or confusing API can result in a successful attack by a malicious user.

▪ Mitigations against this attack include passing an explicit algorithm to the jwtDecode function, checking the alg claim, or using APIs that separate public-key algorithms from shared secret algorithms.

▪ Some people assume that shared secrets are similar to passwords, and in a sense, they are: they should be kept secret. However, that is where the similarities end. For passwords, although the length is an important property, the minimum required length is relatively small compared to other types of secrets. This is a consequence of the hashing algorithms that are used to store passwords (along with a salt) that prevent brute force attacks in reasonable timeframes.

▪ On the other hand, HMAC shared secrets, as used by JWTs, are optimized for speed. This allows many sign/verify operations to be performed efficiently but make brute force attacks easier. So, the length of the shared secret for HS256/384/512 is of the utmost importance. In fact, JSON Web Algorithms defines the minimum key length to be equal to the size in bits of the hash function used along with the HMAC algorithm: “A key of the same size as the hash output (for instance, 256 bits for”HS256“) or larger MUST be used with this algorithm.” - JSON Web Algorithms (RFC 7518), 3.2 HMAC with SHA-2 Functions

▪ Another good option is to switch to RS256 or other public-key algorithms, which are much more robust and flexible. This is not simply a hypothetical attack, it has been shown that brute force attacks for HS256 are simple enough to perform if the shared secret is too short.

▪ Signatures provide protection against tampering. That is, although they don’t protect data from being readable, they make it immutable: any changes to the data result in an invalid signature.

▪ Encryption, on the other hand, makes data unreadable unless you know the shared key or private key.

▪ For this reason, JSON Web Algorithms only defines encryption algorithms that also include data integrity verification. In other words, as long as the encryption algorithm is one of the algorithms sanctioned by JWA, it may not be necessary for your application to stack an encrypted JWT on top of a signed JWT. However, if you encrypt a JWT using a non-standard algorithm, you must either make sure that data integrity is provided by that algorithm, or you will need to nest JWTs, using a signed JWT as the innermost JWT to ensure data integrity.

▪ A common mistake in these scenarios is related to the validation of the nested JWT. To make sure that data integrity is preserved, and that data is properly decoded, all layers of JWTs must pass all validations related to the algorithms defined in their headers. In other words, even if the outermost JWT can be decrypted and validated, it is also necessary to validate (or decrypt) all the innermost JWTs. Failing to do so, especially in the case of an outermost encrypted JWT carrying an innermost signed JWT, can result in the use of unverified data, with all the associated security issues related to that. ￼ Validation of Nested JWT

▪ Different recipient attacks work by sending a token intended for one recipient to a different recipient. Let’s say there is an authorization server that issues tokens for a third party service. The authorization token is a signed JWT with the following payload: { "sub": "joe", "role": "admin" }

▪ To prevent these attacks, token validation must rely on either unique, per-service keys or secrets, or specific claims. For instance, this token could include an aud claim specifying the intended audience. This way, even if the signature is valid, the token cannot be used on other services that share the same secret or signing key.

▪ However, cool-company has other public services. One of these services, the cool-company/item-database service, has recently been upgraded to check claims along with the token signature. However, during the upgrades, the team in charge of selecting the claims that would be validated made a mistake: they did not validate the aud claim correctly. Rather than checking for an exact match, they decided to check for the presence of the cool-company string. It turns out that the other service, the hypothetical cool-company/user-database service, emits tokens that also pass this check. In other words, an attacker could use the token intended for the user-database service in place for the token for the item-database service. This would grant the attacker write permissions to the item database when he or she should only have write permissions for the user database!

▪ The "alg": "none" attack and the “RS256 public-key as HS256 shared secret” attack can be prevented by this mitigation. Every time a JWT is to be validated, the algorithm must be explicitly selected to prevent giving attackers control.

▪ Libraries used to rely on the header alg claim to select the algorithm for validation. From the moment attacks like these were seen in the wild, libraries have switched to at least providing the option of explicitly specifying the selected algorithms for validation, disregarding what is specified in the header. Still, some libraries provide the option of using whatever is specified in the header, so developers must take care to always use explicit algorithm selection.

▪ In the case of nested tokens, it is necessary to always perform all validation steps as declared in the headers of each token. In other words, it is not sufficient to decrypt or validate the outermost token and then skip validation for the inner ones. Even in the case of only having signed JWTs, it is necessary to validate all signatures. This is a source of common mistakes in applications that use JWTs to carry other JWTs issued by external parties.

▪ Although this recommendation applies to any cryptographic key, it is still ignored many times. As we have shown above, the minimum necessary length for HMAC shared secrets is often overlooked. But even if the shared secret were long enough, it must also be fully random. A long key with a bad level of randomness (a.k.a. “entropy”) can still be brute-forced or guessed. To ensure this is not the case, key generating libraries should rely on cryptographic-quality pseudo-random number generators (PRNGs) properly seeded during initialization. At best, a hardware number generator may be used.

▪ This recommendation applies to both shared-key algorithms and public-key algorithms. Furthermore, in the case of shared key algorithms, human-readable passwords are not considered good enough and are vulnerable to dictionary attacks.

▪ Some attackers may get access to correctly signed or encrypted tokens that can be used for malicious purposes, usually by using them in unexpected contexts. The right way to prevent these attacks is to only consider a token valid when both the signature and the content are valid. For this reason, claims such as sub (subject), exp (expiration time), iat (issued at), aud (audience), iss (issuer), nbf (not valid before) are of the utmost importance and should always be validated when present. If you are creating tokens, consider adding as many claims as necessary to prevent its use in different contexts. In general, sub, iss, aud, and exp are always useful and should be present.

▪ Although most of the time the typ claim has a single value (JWT), it can also be used to separate different types of application specific JWTs. This can be useful in case your system must handle many different types of tokens. This claim can also prevent misuse of a token in a different context by means of an additional claim check. The JWS standard explicitly allows for application-specific values of the typ claim.

▪ In other words, rather than using the same private key for signing all kinds of tokens, consider using different private keys for each subsystem of your architecture. You can also make claims more specific by specifying a certain internal format for them. The iss claim, for instance, could be an URL of the subsystem that issued that token, rather than the name of the company, making it harder to be reused.

▪ JSON Web Tokens are a tool that makes use of cryptography. Like all tools that do so, and especially those that are used to handle sensitive information, they should be used with care.

▪ Auth0 is one such provider. If you cannot do this, consider these recommendations carefully, and remember: don’t roll your own crypto, rely on tried and tested code
