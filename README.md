# Phone, texts and fax with Basstok

Your phone service. The free [Basstok](https://basstok.com/) app.
Call ordinary numbers, exchange supported provider texts and send or receive fax
documents. The person at the other end does not need Basstok.

**Early access.** A compatible service is required. Carrier charges apply.
Background ringing on physical devices and wider carrier interoperability are
still being verified. Do not rely on this early-access connection for emergency
calls. This guide does not place calls, purchase numbers or change your service.

## Choose how to connect

| Bring your own service | Prefer Basstok to simplify setup? |
| --- | --- |
| Use the free app with a compatible calling account. Follow the steps below and keep your carrier account and billing. | **Basstok Pro — planned.** A paid option for guided phone setup and connection checks. Not available to purchase yet. [Ask about Basstok Pro](mailto:mail@basstok.com?subject=Basstok%20Pro). |

There is no paid plan, bundled number, included calling allowance or price being
offered by this guide. Future setup assistance must still respect your carrier's
account, identity checks, consent and charges. You do not need Pro to bring a
compatible service.

## What connects to what?

| What you want | Connection | Where you use it |
| --- | --- | --- |
| Ordinary phone calls | SIP registration and INVITE over TLS, with SRTP audio | Basstok's iOS and Android apps |
| Calling-account texts | SIP MESSAGE, if your calling service supports it | The connected private Chat |
| Cellular SMS | A separately supported messaging connection; not every SIP service provides it | The connected private Chat |
| Send a fax | Compatible SIP service; G.711 fax audio over SRTP with supported T.38 negotiation | Select a PDF on Web, iOS or Android |
| Receive a fax | Explicitly enable fax reception on a compatible dedicated calling account | Incoming PDF in the private Chat |
| Call another Basstok user | Basstok audio/video calling | Web and native apps; no carrier connection required |

SIP INVITE sets up a call; it is not itself a background-push service. A service
supporting calls may still lack SIP MESSAGE, cellular SMS or fax support. T.38
is not encrypted, and secure audio to a provider does not make a telephone call
end-to-end encrypted through the public telephone network.

## 1. Check your calling account

Ask your provider for **credential-based SIP registration over TLS** and **SRTP
audio**. You need its server hostname, TLS port, username and password, plus an
authentication realm only if it specifies one. An account that only supports
unencrypted calling is not compatible.

Check these before buying anything:

- Permission to use an independent SIP client rather than only the provider's app.
- Incoming number routing to that calling account.
- Outbound calling, allowed destinations, approved caller ID and actual rates.
- SIP MESSAGE support if you want calling-account texts.
- G.711 fax support and compatible T.38 negotiation if you want fax.

Your provider may offer a new number or support bringing an existing one. That
does not make every SIM number portable or usable as caller ID. Verifying a phone
number in Basstok is not permission to originate calls from it.

## 2. Connect it in Basstok

1. Start or open your Basstok account. You can start without an email, password
   or passkey; save a login method later so losing a session does not lose access.
2. Activate Admin access with verified recovery email when requested. Connecting
   a calling service needs an Admin who participates in the destination Chat.
3. Open a private Chat's calling settings. For personal use, a Chat with yourself
   keeps the service private; adding participants gives them the Chat's permitted
   calling and message access.
4. Enter your own provider-issued values. A fictional example server is
   `sip.example.com`; it is not a usable service. The usual TLS port is `5061`,
   but use the value supplied by your provider. Never paste a password into an
   issue, public example or support screenshot.
5. Save and check the connection status. Registration means the account connected,
   not that every calling, texting or fax capability has passed a live test.

For telephone audio, use a native app and allow the device permissions it asks
for when needed. The browser can manage settings, but does not place telephone
calls. A provider password belongs only in the authenticated connection form.

## 3. Make the first real exchange

Use destinations you control or have permission to contact, and check your
provider's cost first. Never use emergency numbers as a test.

- **Outgoing call:** select the recipient's full international number. Confirm
  two-way audio, caller ID and hang-up from both ends.
- **Incoming call:** call your connected number from another phone. Check answer,
  caller cancellation and timeout. Then test with the app backgrounded and the
  screen locked. A notification without answerable audio is not a successful test.
- **More than one device:** answer on one; the others must stop ringing. Repeat
  with cancellation and no answer. A foreground test does not prove this works
  when the app is suspended.
- **Calling-account text:** explicitly select a number or SIP address and send
  a short message only if your provider supports SIP MESSAGE. Provider acceptance
  is not proof of delivery or reading. It does not automatically become SMS.
- **Cellular SMS:** use the separate supported messaging connection and its
  explicit recipient action. Sending an ordinary Chat message never silently
  sends a paid external text.

External caller and sender details remain external information, not a Basstok
login. Receiving a call or message does not let that person read your Chat.

## 4. Add fax when you need it

**Send:** choose a PDF, review the prepared monochrome pages, enter the recipient's
fax number and deliberately send. The resulting document and status stay in the
Chat. If delivery is unconfirmed, inspect that attempt before sending again;
another attempt may transmit and charge again.

**Receive:** use a dedicated fax number or calling account. Enabling fax reception
directs that account's new incoming calls to fax instead of ringing your phone.
Received documents appear as PDFs with sender details and page counts. A regular
phone destination is not automatically capable of receiving a fax.

Test with a compatible fax destination you control. A successful phone call,
registration or accepted transmission is not proof of delivered fax pages.

## If something does not work

| What you see | What to check |
| --- | --- |
| Cannot connect | Correct hostname, TLS port, credentials and realm; provider allows an independent client |
| Connected but cannot call | Outbound service, destination permissions, caller ID, balance and secure-audio support |
| Outgoing works, incoming does not | The number actually routes to this calling account; fax receiving has not redirected it |
| Rings but cannot answer | Device permissions and actual background audio behavior; do not treat a notification as readiness |
| Calls work, texts do not | SIP MESSAGE or the separate cellular messaging capability must be supported and configured |
| Fax is unconfirmed | Recipient supports fax, provider supports the negotiated media, and the existing attempt's result has been checked |

Do not disable transport security to work around a connection failure. Share only
non-secret status, app version and the failed action with
[Basstok support](mailto:mail@basstok.com); omit passwords, tokens and private messages.

## Integrate with the API

The [public API](https://github.com/basstok/api) describes calling-account setup,
call coordination, explicit text actions, fax documents and their authorization.
It is a control interface, not a telephone audio stream.

Phone setup and external sends require the documented human-session authority.
An App's OAuth grant does not authorize telephone, provider-text or fax sends.
Use scoped Apps for permitted posts, comments and Chat workflows instead; do not
pass a human session to an integration to evade that boundary.

## Standards and references

- [SIP, including REGISTER and INVITE — RFC 3261](https://www.rfc-editor.org/rfc/rfc3261)
- [SIP MESSAGE — RFC 3428](https://www.rfc-editor.org/rfc/rfc3428)
- [Secure RTP — RFC 3711](https://www.rfc-editor.org/rfc/rfc3711)
- [Fax over IP — ITU-T T.38](https://www.itu.int/rec/T-REC-T.38)
- [Basstok API and current contract](https://github.com/basstok/api)

This repository is a user-facing connection guide, not an implementation,
provider endorsement or universal compatibility list.
