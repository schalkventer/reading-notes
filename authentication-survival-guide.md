▪ Authentication is a complex topic, if you think otherwise you will probably get burnt down the road. There’s a myriad of technologies, protocols, concepts and do’s and don’ts. On top of that it’s difficult to keep track of all the evolving best practices and outdated/overloaded terminology; the last one is especially troubling if you’re just getting started on the subject and start to see different things being called by the same name or the other way around

▪ On the other hand, this doesn’t try to be a definitive reference on all things authentication. There will be subjects that won’t get discussed and others that will only be briefly mentioned and not fully explained. In summary this will give you a jump start on most common scenarios and things to watch out for

▪ Use this to find out what you need to know more about and what you can safely ignore.

▪ OAuth2 proved so popular that people started using it for scenarios outside of its original intent - user authentication and identification. However, it be-came apparent that there were too many decisions left to the interpretation of the reader when this framework was applied solely to solve the authentication problems

▪ OpenID Connect can be described as an extension to OAuth2 that provides clear guidance on how to achieve a functional and secure authentication sys-tem. By focusing on solving the specific issue of user authentication the protocol formalized the gray areas of OAuth2 that were causing disparate implemen-tations. For example, where OAuth2 does not impose any format or specific requirements on the tokens used, the OpenID Connect states that an ID token uses the JWT format and it will always have a set of standard claims available

▪ Being the new kid on the block when compared to the other authentication related protocols it’s somewhat comprehensible that support for OpenID Con-nect both at a library and identity provider level is still evolving, particularly when you venture out of the core specification and move to a related specifica-tion that is optional to implement

▪ In the SAML world, both the application messages and the tokens themselves are defined in terms of XML which should be no surprise based on the time this protocol started to appear. This translates into a significant amount of overhead on the binary representation of the messages and tokens required by the protocol which among other reasons make this protocol a less than ideal candidate for usage in modern applications. If you do come across this protocol, you’ll probably do so when integrating with already existing systems. In case this occurs be aware that there are two significant versions of the protocol still in active use - the 1.1 and 2.0 versions. tion, which are still in wide use today

▪ Another interesting point about SAML that might trip you over is that SAML can be used both to refer to the protocol, but also to the token format that goes with it. This separation is actually important because as we’ll soon find out, the token format itself can be used independently of the underlying pro-tocol.

▪ WS-Federation Another standard that tackled the web browser-based SSO was WS-Federation. This was part of a big family of specifications that covered a lot of ground in the application integration field; from server-to-server interactions to rich-client applications interacting with server-side web services. The group of protocols was collectively addressed as WS-* protocols. To be honest these were signifi-cantly complex and do not invoke any kind of good memories from my part because the richness of the specified features carried a significant price tag due to the inherent implementation complexity

▪ Fortunately, for the purpose of this guide, WS-Federation was probably the saner one in the family and in a similar fashion to SAML, defined the neces-sary web interactions required between two systems in order to achieve SSO. I believe it’s also safe to say that it did so in a much simpler way than SAML and maybe for that reason is still a protocol with a substantial usage

▪ However, to the contrary of the SAML protocol, WS-Federation does not de-

▪ fine its own token format and instead makes this implementation specific. The end result is that in most scenarios you end up using the SAML - token format - alongside the WS-Federation protocol

▪ Brief look into the past (OpenID and OAuth 1.0a) Both OAuth2 and OpenID Connect share the fact that they were designed to replace existing protocols that, at least judging by their names, seem to be somewhat related. However, the relation is almost only of the names as in both cases the most recent editions are not backward compatible and can and, in my opinion, should be seen as completely different standards

▪ Token overload Although the hype around tokens is relatively new, particularly with JWT, the use of tokens for authentication is not new at all. If you think about it, the traditional cookie-based authentication systems used in Web applications for ages is a good example of the use of tokens as a way to authenticate the user.

▪ Most implementations rely on an opaque string, which at least would be randomly generated and maybe even digitally signed, that was then used on the server-side to lookup additional information about the authenticated user. This session identifier is nothing more than a token and the overall cook-ie-based authentication system, that we know so well, would be better de-scribed as a token authentication system that uses by-reference tokens instead of self-contained tokens and relies on cookies as the mechanism to store and transmit the token from the client application to the server application - re-source server

▪ Having said that, nowadays, when you mention or see someone referring to the use of a token it’s highly likely that it implies a self-contained/by-value token. I personally like the by-value terminology because it makes a good contrast with the by-reference tokens and it’s also terminology that is widely used within

▪ If there is one token format you need to absolutely know about then that format is JWT (JSON Web Token). It’s a self-contained token which means that infor-mation about the entity the token target is contained within the token value itself. This makes it an ideal choice for scenarios where you want to move au-thenticated session data from your server to the client application and achieve the so-called stateless authentication systems

▪ The JWT token format is also relatively simpler when pitted against popular predecessors like SAML, however, this simplicity is relative and you should not assume JWT is so simple that you might as well use your own logic to process them

▪ 21 mon implementations of authentication systems using JWT’s, mostly because both OAuth2 and OpenID Connect mandate that TLS must be used when transmitting tokens on the wire and the actual contents of the tokens do not include sensitive information. Before JWT, the SAML token format would be the one you most typically en-counter when working with authentication systems aimed at solving authen-tication issues that crossed domain boundaries like, for example, achieving single sign on. This token format also supports signing and encryption, however, you could claim that it does it with an increased implementation complexity when com-pared to JWT; hence the decline in its usage

▪ The reason for this is mostly be-cause while JWT is based on the JSON format, SAML relies on XML instead and this difference alone causes a significant increase in the overall complexity of any feature that the token format decides to support. Additionally, SAML was born in a time that web services and SOAP were kings; a time where XML was everywhere. Nowadays, the focus is on making things simpler; HTTP over SOAP, JSON over XML and, to what authentication is concerned, JWT over SAML

▪ The format of the token is just one small aspect of it, one important distinction to be made is the role of each token in your authentication system. Within the realms of OAuth2 and OpenID connect there are three types of token in com-mon use: Access token Refresh token ID token

▪ An access token is defined within the OAuth2 specification as credentials used by a client application to access a protected resource made available on a giv-en resource server. Although the client application makes use of the token to perform this authorized request the access token itself should be considered opaque to the client; this purely means that a client application is granted the token after completing an authorization grant where the resource owner con-sents to delegate access to their resources and then treats it as a black-box. It’s an artifact that the client application knows it can use to perform autho-rized requests on a given resource server, but without any knowledge of the actual contents of the token. Access tokens will have an associated expiration date which is implementation specific, but it’s usually fairly short ranging from minutes to hours. The reason for this short expiration is that since these access tokens are typically used as bearer tokens the short lifetime will reduce the

▪ impact of possible leaks. There is no requirement in the format used for an access token; it can vary from a self-contained token like a JWT to randomly generated value that is used as a by-reference token

▪ The most common approach it to go with self-contained tokens because the consumption of the tokens does not require a resource server to make an additional call to the authorization server in order to obtain the information associated with the token

▪ Having said that, there are still scenarios where by-reference tokens may pro-vide better characteristics, for example, in cases where the authorization server and resource server roles are played by the same entity this type of token may prove more lightweight on the wire without the extra lookup to obtain the in-formation causing significant overhead

▪ One final note on access tokens; ideally, they should not be used as means to authenticate users. The reason for this is that they are issued for use against an API and if you use them for authentication you may leave your application vulnerable, for example if an access token was issued for API X of vendor A and an application Y of vendor B decides to use the access token also for user authentication in the application itself, the application can’t ensure the access token was issued in an authorization flow initiated by itself or if it was issued to a completely unrelated application under the control of an attacker which is

▪ now trying to impersonate a user using the access token. Any token used for user authentication must have a way to ensure that the token was issued for authentication with a specific application so that the ap-plication can reject tokens with a different audience

▪ Remember that an access token is is-sued by an authorization server and then used against a resource server. If this token is self-contained, the authorization server won’t ever be called again

▪ However, a refresh token is issued and consumed by authorization servers which means that token revocation policies for refresh tokens can be imple-mented by the authorization server because it knows for sure that client appli-

▪ Even though they are better than storing passwords, client applications need to ensure proper storage of refresh tokens in order to mitigate against the possi-bility of leaks while the token is in storage. This is another point of confusion because not all client application types can ensure proper storage for long-lived credentials and as such the usage of refresh tokens must be avoided in those situations. The most common example of applications that fail to provide ade-

▪ quate means of storage is browser-based applications

▪ The last token type that we’ll cover is the one most important when speaking of user authentication; the ID token. This token was introduced with the OpenID Connect specification and is, as the protocol, tailor-made to solve authentica-tion problems. In contrary to what happens with the two previously mentioned token types which can have an implementation-specific representation, the OpenID Con-nect protocol mandates that compliant implementations use JWT as the means to represent this token type

▪ As mentioned before the proper storage of tokens is a must have requirement in token-based authentication systems - particularly on ones that use them as bearer tokens

▪ The situation is a bit trickier with browser-based applications; you do have a few options to consider as possible storage, but all come with their specif-ic shortcomings

▪ Choosing the storage for a browser-based application it’s a pick your poison kind of game where the best choice highly depends on your exact scenario.

▪ Web Storage (local Storage or session Storage) 27 possibility, you must ensure that you strictly follow the rules for ID token vali-dation included in section 3.1.3.7 of the OpenID Connect specification.

▪ The pros: The browser will not automatically include anything from Web stor-age into HTTP requests making it not vulnerable to CSRF Can only be accessed by Javascript running in the exact same domain that created the data Allows to use the most semantically correct approach to pass token authentication credentials in HTTP (the Authorization header with a Bearer scheme) It’s very easy to cherry pick the requests that should contain authen-tication

▪ The cons: Cannot be accessed by Javascript running in a sub-domain of the one that created the data (a value written by example.com cannot be read by sub.example.com) Is vulnerable to XSS In order to perform authenticated requests you can only use brows-er/library API’s that allow for you to customize the request (pass the token in the Authorization header

▪ HTTP-only cookie The pros: It’s not vulnerable to XSS The browser automatically includes the token in any request that meets the cookie specification (domain, path and lifetime) The cookie can be created at a top-level domain and used in requests performed by sub-domains

▪ The cons: It’s vulnerable to CSRF You need to be aware and always consider the possible usage of the cookies in sub-domains Cherry picking the requests that should include the cookie is doable but messier You may (still) hit some issues with small differences in how browsers deal with cookies If you’re not careful you may implement a CSRF mitigation strategy that is vulnerable to XSS The server-side needs to validate a cookie for authentication instead of the more appropriate Authorization header

▪ Javascript accessible cookie (ignored by server-side) The pros:

▪ It’s not vulnerable to CSRF (because it’s ignored by the server) The cookie can be created at a top-level domain and used in requests performed by sub-domains Allows to use the most semantically correct approach to pass token authentication credentials in HTTP (the Authorization header with a Bearer scheme) It’s easy to cherry pick the requests that should contain authentication

▪ The cons: It’s vulnerable to XSS If you’re not careful with the path where you set the cookie then the cookie is included automatically by the browser in requests which will add unnecessary overhead In order to perform authenticated requests you can only use browser/library API’s that allow for you to customize the request (pass the to-ken in the Authorization header) This may seem a weird option, but it does has the nice benefit that you can have storage available to a top-level domain and all sub-domains which is something Web storage won’t give you. However, it’s more complex to implement

▪ My recommendation for most common scenarios would be to go with the Web 

▪ storage option, mostly because: If you create a Web application you need to deal with XSS; always, independently of where you store your tokens If you don’t use cookie-based authentication CSRF should not even pop up on your radar so it’s one less thing to worry about

▪ None of the cookie-based options mention it, but use of HTTPS is mandatory of course, which would mean cookies should be created appropriately to take that in consideration.

▪ Although tokens, particularly self-contained formats like JWT are all the rage right now, cookies are not obsolete. This is not surprising from the perspective that cookies are just a mechanism for state management within HTTP and as

▪ If you think cookies help simplify your use case, don’t reject them purely be-cause they aren’t the new shiny thing available or because someone throws the stateless argument into the mix.

▪ The big downside with cookies is that since they are automatically in-cluded in requests made by user agents you need to ensure proper mitigation for CSRF attacks

▪ One of the big benefits of modern authentication systems is that they are ap-plied to solve authentication problems for application systems that rely heav-ily on HTTP communications

▪ My recommendation would be for you to spend some time on learning the details around the following areas: HTTP request/response semantics HTTP redirects HTTP authentication (the Authorization header) HTTP state management (cookies) With this knowledge on your hands and a couple of tools on your toolbelt you’ll find it very easy to analyse and troubleshoot modern authentication flows

▪ There are of course variations, but in the general case debugging these flows consists of checking at each step the issued HTTP re-quest and response and validate if the contained payload (query parameters, headers, cookies and request/response body) matches what you would expect to find according to the specific protocol requirements. Another important point to make is that by relying on the HTTP Archive file format (HAR) you can easily troubleshoot the problem after the fact and/or in another machine. This is also ideal for hard to reproduce issues that may occur in a very specific environment. This format is supported by major brows-ers which can export HTTP network traces which you can then inspect using HAR viewers. Be advised that capturing the HTTP requests associated with an authentication transaction will contain sensitive information, including user passwords

▪ Additionally, since most authentication flows involve redirects the first thing you should do is to ensure your browser is configured to preserve the network trace upon navigation as most time the root cause of the issue is a few request down the line in relation to where your browser ultimately gets redirected to. Another must-have tool when it comes to HTTP debugging is Fiddler, now Telerik Fiddler. This is a standalone tool which acts as a proxy and allows for the analysis of the HTTP traffic that passes through it. Depending on your browser of choice you may need to configure it in order to work with the Fid-dler proxy. Additionally, by default you won’t be able to see decrypted HTTPS traffic unless you explicitly enable that functionality.

▪ Finally two other good additions for your toolbelt when it comes with working with the tokens themselves are the online tools: http://samltool.io/ - Lets you decode SAML tokens and quickly re-view the most significant attributes https://jwt.io/ - Lets you quickly decode and verify signatures for JWTs using HS256 and RS256 signature algorithms. In the former case you can even edit the payload

▪ There is already a lot of awareness on this one and both the OAuth2 and the OpenID Connect specification extensively call your attention to this, but it’s something so essential that it’s never too much to repeat; the usage of these heavily based HTTP protocols imply that the communication between the in-volved parties happens through TLS (HTTPS). This is not optional as not do-ing this severely compromises the security of the system.

▪ Access token A string accepted as credentials to access protected resources. It imposes no requirement on the format, structure or process in which it’s used

▪ Bearer token A more specific type of access token that implies that the only mechanism used to validate the access to a protected resource is the token itself. The nam ing stems from the fact that anyone in possession of the token - the bearer - can access the protected resource as long as the token remains valid
