## Question

What is the most important initial information for cash register manufacturers (PosCreator) in AT

## Metadata tags

lang-en, market-at, middleware, portal-sandbox, architecture, cashbox management, portal, PosCreator, consultant

## Answer

Initial information and various FAQ for the connection of the fiskaltrust.Middleware as well as for registration and configuration in [https://portal.fiskaltrust.at](https://portal.fiskaltrust.at/).

**General, business model**

- The fiskaltrust.Middleware is a free and standardized technical implementation of fiscalization (signature, QR code, data acquisition protocol, ...) for AT, DE and FR
- The optional carefree package costs the end customer EUR 360 per year for local application and EUR 288 per year for cloud application
  - Product overview: https://www.fiskaltrust.at/entgeltblatt (in DE)
  - For these products there are bulk prices for cash register dealers.
  - The fiskaltrust.Middleware can be used by the customer however also free of charge!
  - Any necessary local hardware such as a chip card with reader is not included free of charge.
  - All products are available through https://portal.fiskaltrust.at/shop

**Developer documentation**

- The current documentation for our iPOS-interface can be found at [https://docs.fiskaltrust.cloud](https://docs.fiskaltrust.cloud/).
- The communication between the POS software and the middleware works in such a way that the receipt data is sent from the POS software to the iPos-interface, where it is processed (total counter, data acquisition protocol, QR code, ...) and then the original receipt data is printed with the response of the middleware on the (now RKSV compliant) receipt.
- The documentation also contains a github-repository with examples of how our security system is addressed by the cash register, for different programming languages. Test installations can be generated free of charge at in [https://portal-sandbox.fiskaltrust.at](https://portal-sandbox.fiskaltrust.at/).
- Nuget packages are also available for download.
- Various tutorials are available as videos at https://youtube.com/c/fiskaltrust

**Registration** 

- For our partnership the free registration as well as the completion of the role as cash register manufacturer under [https://portal.fiskaltrust.at](https://portal.fiskaltrust.at/) is necessary.

**FAQ - AT** 

- Legal basis and links to the relevant laws: https://www.fiskaltrust.at/rechtsgrundlagen
- Information is also available for registered partners at https://portal.fiskaltrust.at/ - "Download" and "Questions and Answers".

* https://www.fiskaltrust.at/faq/
* https://www.fiskaltrust.at/checklist/

Contact us: [info@fiskaltrust.at](mailto:info@fiskaltrust.at) 
