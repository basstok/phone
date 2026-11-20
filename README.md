# Phone, texts and fax with Basstok

[Basstok](https://basstok.com/) can call ordinary numbers, exchange supported
texts and send or receive fax documents. The recipient can use their regular
phone or fax number. Telephone calling is in early access and uses the native
apps. Background ringing on real devices is still being verified. Use ordinary
emergency services for emergency calls.

## Choose a route

| What you want | What you need |
| --- | --- |
| Basstok-funded telephone calling | A personal Account with verified phone control, an eligible paid Monthly plan, a supported destination and available minutes. Free Accounts include zero Basstok-funded outbound telephone minutes. |
| Your own compatible calling service | Enterprise and a compatible provider account. The provider's access rules, rates and billing apply. |
| Shared business calling | An Enterprise Account with a calling line configured by a Manager. Current Team Members can use the shared line. |
| Calling another Basstok user | A Basstok audio or video Call to an eligible Member. This uses Basstok's separate in-app calling route. |

Availability and caller ID can vary by destination. Check the number, outgoing
identity and allowance shown before calling. A pending purchase or a verified
sign-in number on its own does not establish an eligible calling route.
[Current product availability](https://basstok.com/)

## Connect your service

In Account, open **Add to Basstok** and select a supported phone service when
available. You can manage an existing connection from its calling settings. A
personal line belongs to the Member who connects it. A business line belongs to
the Account. Private phone-line use does not require creating a Chat.

For a compatible SIP account, get the server hostname, TLS port, username and
password from your provider. Supply its authentication realm if required. Ask the
provider about all capabilities you intend to use:

- Credential-based SIP registration over TLS and secure audio over SRTP.
- Inbound number routing, outbound coverage, permitted caller ID and rates.
- SIP MESSAGE or cellular messaging support for the explicit text route.
- G.711 fax audio and supported T.38 negotiation for fax.

A number's portability, caller ID eligibility and costs depend on the provider.
Enter credentials only in the authorized connection form. Treat successful SIP
registration as evidence of a connection and test the exact feature separately.

## Call and text

For a deliberate test, use a destination you control and check rates first.
Verify outgoing audio and hang-up in both directions. For incoming calls, also
test background ringing, lock-screen behavior and answering on one of your
devices.

Cellular SMS and SIP MESSAGE have separate availability. Use the explicit
recipient and text action for the connected service. Ordinary Chat messages
stay in the Chat. External numbers and caller names carry no Basstok membership
or access to private Chats. Carrier acceptance does not establish delivery or
reading.

## Fax

Choose a PDF, review the prepared pages and confirm the exact recipient before
sending. A successful submission has a transmission report. If a result is
unconfirmed, check the original attempt before sending again. A second
submission can transmit and charge again.

Incoming fax requires explicitly enabled reception on a compatible dedicated
line. Enabling reception directs new calls on that line to fax and incoming
documents appear as PDFs. A managed sending allowance does not assign a
dedicated receiving number. The provider connection uses secure audio where
required. T.38 traffic itself is unencrypted.

## Integrate

The [deployed API](https://basstok.com/openapi.json) documents phone previews,
coordination, texts and fax. Telephone calling and cellular texts require the
documented human session. An App can send fax through an explicitly
owner-consented private customer line with `fax:send`, or through an eligible
shared Chat fax operation with the additional Chat permissions. Private fax
history and PDFs remain owner-only.

[Basstok API guide](https://github.com/basstok/api) ·
[Support](mailto:mail@basstok.com)

## Standards

- [SIP — RFC 3261](https://www.rfc-editor.org/rfc/rfc3261)
- [SIP MESSAGE — RFC 3428](https://www.rfc-editor.org/rfc/rfc3428)
- [Secure RTP — RFC 3711](https://www.rfc-editor.org/rfc/rfc3711)
- [Fax over IP — ITU-T T.38](https://www.itu.int/rec/T-REC-T.38)
