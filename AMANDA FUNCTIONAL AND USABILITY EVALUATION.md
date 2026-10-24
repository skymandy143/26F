# CampusShare Functional Testing and Usability Evaluation Report

**Author:** Amanda Nancy Skaikay  
**Group:** Group F  
**Project:** CampusShare  
**Report type:** Functional testing and usability evaluation  

---

## 1. Executive Summary

CampusShare is a prototype peer-to-peer equipment rental and sharing platform for university students. Students can list equipment, browse and search listings, request rentals (by the day or by the hour), pay a rental fee through a demonstration payment page, track rental status, rate each other, and receive in-app notifications.

My contribution to the project is documentation, manual functional retesting, usability evaluation, and recommendations. I earlier tested a previous version of the site and found several problems. After the developers made improvements, I revisited the affected features and captured screenshots of the updated interface.

**Improvements I manually retested (worked for me):**

- Equipment image upload
- Hourly rentals
- Borrower and owner ratings
- Password-related behavior (improved when retested; see the limits in Section 5)

**Remaining usability problems I observed:**

1. New notifications are hard to notice. I have to open the Notifications page and check manually.
2. Starting a direct conversation with another user is inconvenient because I have to search for the person.
3. Real email delivery has not been established. The team is still using a test email setup rather than a verified, working one.

**Main recommendations:** add a visible notification indicator, add "Message Owner" / "Message Borrower" actions, configure and verify real email delivery, validate the full rental workflow end to end, and verify authentication and authorization behavior.

**What this report is and is not.** It is a manual evaluation based on my own retesting and on 29 screenshots. It is not an automated test run and not a source-code security review. The Group F project progress presentation reports that 36 automated tests passed in the latest full local run. That is a team-reported result: I did not run the automated suite, I have not verified the count, and the presentation states that supporting test output had not yet been attached (see Section 4). Screenshots show what the interface displayed; they do not prove that every backend operation is correct. The payment feature is a demonstration only and no real money is processed.

---

## 2. Project Overview

CampusShare addresses a common student problem: many students own equipment they rarely use (cameras, tripods, calculators, laptops, books), while others need such items only briefly. The platform lets students share equipment with each other on a free or paid basis.

Functionality visible in the interface includes:

- User accounts, login, "Forgot Password", and a "Resend verification email" link
- A student dashboard with quick actions
- Equipment listings with photo upload, condition, pricing (per day or per hour), security deposit, availability dates, and a campus pickup location
- Browse, keyword search, category filter, and status filter
- Rental requests and an owner-side "Requests" page
- Payment and deposit status, return restrictions, late fee and damage status fields
- Notifications with an email-preference setting
- A Messages link in the main navigation
- Borrower and owner ratings, and a "My Reviews" link

**Project links**

| Resource | Link |
|---|---|
| Group repository (`joe-work` branch) | https://github.com/bhsei/26F/tree/joe-work |
| Developer repository (`joe-work` branch) | https://github.com/Jiggyboy97/CampusShare/tree/joe-work |
| Live demo | https://lyrics-tribesman-scallion.ngrok-free.dev |

**Access limitations while preparing this report.** The two GitHub pages could not be opened by the tool used to prepare the report (automated access was refused). The live demo returned only an ngrok landing page, not the application. As a result, I did **not** inspect the source code, README, technology stack, or any automated tests, and I did not re-run the live site while writing. All technical statements below come from my own testing and the screenshots. The live demo is hosted through ngrok and may expire or become unavailable.

**Demo-payment limitation.** The payment pages state "Demo payment only — no real money is processed." The QR code and "Confirm Demo Payment" button simulate payment for demonstration. They must not be read as real payment processing.

CampusShare is described here as a prototype / MVP. I have no repository evidence for a different maturity level.

---

## 3. Evaluation Objectives and Scope

**Objectives**

- Assess key user-facing workflows.
- Retest features that previously did not work for me.
- Identify usability barriers.
- Record remaining issues.
- Recommend improvements that can guide future development.

**Features reviewed (through use and/or screenshots)**

- Login screen and password-related behavior; Forgot Password screen
- Student dashboard and navigation
- Equipment listing form, image upload, per-day and per-hour pricing options
- Browse, search, category filter, status filter, equipment detail page
- Hourly booking form and estimated price
- My Rentals, owner Requests page, rental and deposit status, return restriction message
- Demo QR payment pages
- Borrower rating and owner rating
- Notifications page and email-preference setting

**Out of scope / not evaluated**

- Source-code review, database inspection, deployment configuration
- Execution of the team's automated tests
- Password hashing, session handling, and other security internals
- Real email delivery (account verification, password reset, notification emails)
- Real payment processing (none exists in the demo)
- Mobile and tablet layouts, accessibility compliance, performance, load behavior
- Data persistence across application restarts
- The Messages and "Students" pages in detail (I did not capture screenshots of them)

---

## 4. Testing Approach and Evidence

My approach was **manual functional retesting** of features that previously failed for me, combined with **screenshot-based interface evaluation** of the updated site.

This report uses four distinct kinds of statements, and each is labeled so they are not confused:

| Kind of evidence | Meaning in this report |
|---|---|
| **Manually retested successfully** | I personally retested the feature in the updated version and it worked for me. This is the only basis for "Passed — manually retested". |
| **Visible interface state** | A screenshot shows a screen, message, or status. It shows what was displayed, not necessarily that the backend operation is correct. |
| **Team-reported item** | Information from the Group F project progress presentation, including the automated-test result and the follow-up items listed in Section 10. These are attributed to the presentation. I did not test or independently verify them. |
| **Recommendation needing verification** | A suggested test or improvement. It is not a confirmed defect. |

**Team-reported automated tests.** The Group F project progress presentation reports that **36 automated tests passed in the latest full local run**, and also states that supporting test output had not yet been attached. In this report that figure is treated as a *reported result pending supporting evidence*. It is the team's result, not mine: I did not personally execute the automated test suite, I have not seen the test output, and I have not independently verified the count or the outcome. The supporting output should be attached to the repository or reviewed by the team before the figure is relied on. My manual findings are separate from, and do not confirm or contradict, that result.

**Not recorded.** I have not recorded the dates of my retests, browser versions, operating system, device details, test logs, or the number of tests executed, and none are claimed. The password prompt in screenshot S01 is Google Password Manager's, which indicates the Chrome browser was used for that capture. The screenshot file names carry a capture date and time of 25 October 2026; dates shown inside the application (for example 26 October 2026) are test data entered in the demo.

Screenshots are referenced as S01–S29. The full index, with what each shows and what it does not prove, is in Appendix A.

---

## 5. Earlier Problems and Improvements Observed

| Feature | Earlier observation | Updated result | Evidence or limitation |
|---|---|---|---|
| Equipment image uploads | I could not upload images successfully. | Manually retested; worked for me. | Personal retest. S09 shows the upload field (JPG, PNG or WebP; max 5 MB); S13, S16, S17 show an uploaded photo on a listing. Not every format, size, or failure case was tested. |
| Hourly rental | Hourly rental did not work as expected. | Manually retested; worked for me. | Personal retest. S12 (hourly listing option), S18 (booking form), S22/S26 (hourly rental in My Rentals). Edge cases not tested. |
| Borrower ratings | Rating was not working as expected. | Manually retested; worked for me. | Personal retest. S04, S05 show the Rate Borrower form. |
| Owner ratings | I could not rate owners as expected. | Manually retested; worked for me. | Personal retest. S25 shows the Rate Owner form; S26 shows "You have reviewed the owner." |
| Password-related behavior | Password protection and browser password saving needed improvement. | Relevant behavior improved when retested. | S01 shows a browser "Save password?" prompt and S14 a browser autofill suggestion. These show browser behavior only. They are **not** evidence of secure server-side storage, hashing, or secure authentication. |
| Rental workflow screens | Earlier version had less complete or working flows. | Updated screens show more structured rental states. | S03, S22, S26 show status, payment, deposit, due-date, and rating elements. Screenshots alone do not establish full end-to-end success. |

**Observed pricing examples (not a confirmed pricing policy).** The screenshots allow some arithmetic checks:

- Hourly: 09:00–14:30 is 5.5 hours; the form shows "¥120 (6 hours × ¥20)" (S18). The same ¥120 appears as Total Price in My Rentals (S22) and as the amount on the payment page (S23). This is consistent with partial hours being rounded up, but I have no documentation that this is the intended rule.
- Daily: ¥240 for 26–28 Oct at ¥80/day, and ¥560 for 26 Oct–1 Nov at ¥80/day (S22). Both match counting the start and end dates inclusively (3 days and 7 days). Again, this is an observation, not a documented rule.

---

## 6. Functional Test Cases

**Status key:** *Passed — manually retested* is used only where I confirmed I retested the feature and it worked. TC-19 is a team-reported item and is not one of my results. *Visible in screenshots* means a screen or state was displayed. *Needs further testing* and *Not established by available evidence* mean the result is unknown.

| Test ID | Feature | Test description | Expected result | Observed result | Status |
|---|---|---|---|---|---|
| TC-01 | Equipment image upload | Upload a photo while listing equipment (S09). | Photo is accepted and shown on the listing. | Upload worked for me. A photo appears on the listing in Browse, details and My Listings (S13, S16, S17). Formats, size limit, and failure cases not tested. | Passed — manually retested (limited scope) |
| TC-02 | Hourly rental booking | Book an hourly item for 26 Oct, 09:00–14:30 (S18). | Request is accepted and appears in rental records. | Worked for me. Rental appears with "09:00" and "14:30" times (S22). | Passed — manually retested |
| TC-03 | Hourly price estimate | Check the displayed cost for a 5.5-hour booking at ¥20/hour. | Estimate matches the intended pricing rule. | Form shows ¥120 (6 hours × ¥20); recorded total and payment page also show ¥120 (S18, S22, S23). Rounding policy not confirmed. | Observed example; needs further testing |
| TC-04 | Borrower rating | Rate a borrower after a completed rental (S03–S05). | Rating can be submitted. | Worked for me. Form offers Excellent to Poor (S05). | Passed — manually retested |
| TC-05 | Owner rating | Rate an owner after a completed rental (S25, S26). | Rating can be submitted and recorded. | Worked for me. My Rentals shows "You have reviewed the owner." (S26). | Passed — manually retested |
| TC-06 | Rating validation | Submit the Rate Owner form without choosing a rating (S25). | A validation message is shown. | Message "Please select an item in the list." is displayed. Eligibility, duplicates, and unauthorized submission not tested. | Visible in screenshots; needs further testing |
| TC-07 | Password-related behavior | Log in and observe password handling (S01, S14). | Password behavior works as intended and is secure. | Behavior improved when I retested. Browser offered to save a password (S01) and showed a saved-login suggestion (S14). Hashing, sessions, and server-side security not verified. | Improved — manually retested (scope limited) |
| TC-08 | Equipment search | Search Browse for "tripod" (S29). | Matching listing is returned. | One tripod listing is shown (S29). | Visible in screenshots; formal retest not confirmed |
| TC-09 | Category and status filters | Use the category and status dropdowns (S27, S28). | Results are filtered correctly; combined filters work. | Dropdown options are visible (categories: Calculator, Camera, Other, Tripod; statuses: Available, Pending, Booked). Filtered results were not captured. | Not established by available evidence |
| TC-10 | Rental requests and status tracking | Follow a request through My Rentals and Requests (S03, S22, S26). | Status, payment, and deposit information is shown and updated correctly. | Cards show Approved / Completed, Paid / Unpaid, deposit status, and due-date messages. Correctness of every transition not verified. | Visible in screenshots; needs further testing |
| TC-11 | Demo payment | Use "Pay with QR Code", continue, and confirm (S22–S24, S26). | Payment status changes from Unpaid to Paid; no real money moves. | Pages state "no real money is processed." Tripod rental shows Unpaid before (S22) and Paid after (S26). I did not separately record this as a formal retest. | Visible in screenshots; needs further testing |
| TC-12 | Notifications | Open Notifications and review items (S07, S19). | User can easily discover new notifications. | Page lists notifications with Unread/Read state, "Mark as read", and "View". The problem observed is discoverability: I cannot tell I have a notification without opening the page (Issue 1). | Usability issue observed (see Section 8) |
| TC-13 | Starting and reopening direct conversations | Start a conversation with another user and find it again. | User can start a conversation from a listing or rental and reopen it easily. | I find it inconvenient: I have to search for the person (Issue 2). Messaging as a whole was not found broken. No Messages screenshots captured. | Usability issue observed (see Section 8) |
| TC-14 | Email verification and delivery | Register, receive verification email, receive notification emails. | Real emails arrive at verified addresses. | The login page has "Resend verification email" (S14) and the notification page says delivery requires a verified address and SMTP settings (S07, S19). Delivery has not been verified; the team is using a test address. | Not established by available evidence |
| TC-15 | Password recovery | Request a password reset (S15). | Reset email is sent and the password can be changed. | Forgot Password page exists and shows a privacy-preserving message. Email delivery and reset completion not tested. | Not yet tested |
| TC-16 | Return and deposit workflow | Attempt to return an item; review deposit status (S03, S06, S22). | Return is allowed or blocked for the correct reasons; deposit status updates correctly. | A message says the rental payment must be marked paid before the item can be returned (S06). Deposit shows Pending or Refunded on different rentals. Who may confirm returns and when deposits refund were not tested. | Visible in screenshots; needs further testing |
| TC-17 | Late fees and damage handling | Review late-fee and damage fields (S03). | Fees and damage status are calculated and handled correctly. | Fields are displayed (e.g., Late Fee ¥0.0; Damage Status "Not Checked" / "Good Condition"). Calculation and dispute handling not tested. | Not established by available evidence |
| TC-18 | Mobile usability and accessibility | Use the site on a phone-sized screen; keyboard navigation. | Site is usable and accessible. | All screenshots are desktop-width. | Not yet tested |
| TC-19 | Team-reported automated tests | Not performed by me. Listed so the report distinguishes manual from automated results. | Automated tests pass, with supporting output available. | The progress presentation reports 36 passing tests in the latest full local run and notes that supporting output was not yet attached. I did not run them or verify the count. | Reported result pending supporting evidence (not tested by me) |

---

## 7. Usability Evaluation

This section separates **direct observations** (things I saw or experienced) from **recommendations** (suggestions that still need verification).

### 7.1 Navigation and discoverability

**Direct observations**

- The dashboard navigation lists Dashboard, Browse, Notifications, Messages, List Item, My Rentals, My Listings, Requests, and My Reviews (S02). Other pages show shorter menus: the Browse page shows Home, Browse, List Item, Dashboard (S16), the rating pages show Dashboard, Browse, My Rentals (S04), and My Listings shows a different set again (S13). The menu therefore changes depending on the page.
- The Notifications page (S07) shows its navigation in a plainer style than other pages and includes a "Students" link not seen on the dashboard.
- A new notification is not visible anywhere outside the Notifications page. I have to open it to find out (Issue 1).
- Starting a conversation requires searching for the other user (Issue 2).

**Recommendations**

- Use one consistent navigation menu on all signed-in pages, and confirm whether the page-by-page differences are intentional.
- Add a notification bell with an unread count (see Issue 1).

### 7.2 Booking clarity

**Direct observations**

- The hourly booking form shows start and end date and time, then a plain-language estimate: "Estimated rental cost: ¥120 (6 hours × ¥20). The security deposit is not included." (S18). This is clear and shows how the figure was reached.
- The listing form for hourly items shows the owner's daily pickup and return window and the note "Hourly bookings must start and finish within this daily window." (S12).

**Recommendations**

- State the rounding rule for partial hours and the day-counting rule where users can see them, once the team confirms the intended policy.
- Test fractional hours, invalid dates, end before start, and overlapping bookings (Section 9).

### 7.3 Rental status visibility

**Direct observations**

- Rental cards show status, payment, deposit status, security deposit, total price, and due-date messages such as "Return due tomorrow." and "Return due in 3 days." (S22). This makes the workflow far easier to follow than a bare list.
- Owner request cards show Late Fee and Damage Status alongside action buttons (S03).
- Rental cards for the tripod show a generic placeholder box even though the listing has a photo (S22, S26 versus S13, S17). I have not checked whether this is intended.
- One rental is marked "Completed" with an end date of 1 November 2026, which is after the date the screenshots were captured (S03, S22). This is probably demonstration data, but the team may want to confirm how status and dates relate.

**Recommendations**

- Show the equipment photo on rental cards where one exists.
- Verify that status transitions follow the intended order.

### 7.4 User feedback and error recovery

**Direct observations**

- When a rating option is not selected, a validation message appears (S25).
- When a return is attempted before payment, a "Please check your request" page explains the reason and offers a "Go back" button (S06). I infer this page was triggered by the "Mark as Returned" action; I did not record the exact steps.
- Before a demo payment is finalized, a browser dialog asks "Confirm this payment?" (S24).
- The notification page explains that email delivery depends on a verified address and SMTP settings (S07, S19), but the checkbox alone does not tell the user whether email is currently working.

**Recommendations**

- Provide clear messages for failed uploads, invalid bookings, failed actions, and email-delivery problems.
- Where practical, preserve entered form data after a validation failure.

### 7.5 Communication

**Direct observation:** A Messages link exists in the main navigation (S02). The difficulty I found is in starting and finding conversations, not in messaging as a whole.

**Recommendations:** see Issue 2 in Section 8.

---

## 8. Outstanding Issues

**Priority system**

- **High:** affects whether users learn about important rental events or can communicate and complete core flows.
- **Medium:** affects correctness or convenience but has a workaround.
- **Low:** polish or later-stage improvement.

### Issue 1 — Notifications are not sufficiently visible

| Item | Detail |
|---|---|
| **Type** | Confirmed observation (my own use) |
| **Priority** | **High** |
| **Description** | I cannot tell that I have received a notification without opening the Notifications page and checking. The page itself works as a list: it shows messages such as "New borrowing request for tripod 560x900 pixels.", an Unread/Read label, a timestamp, "Mark as read", and "View" (S19). The notification system as a whole is not broken; the problem is discoverability. |
| **User impact** | Owners may miss rental requests, and borrowers may miss approvals, due dates, or deposit updates, which delays the rental workflow. |
| **Recommended improvement** | Add a notification bell (or similar indicator) to the main navigation or dashboard with an unread count; keep a clear unread/read state; make important rental events easy to find; consider notifications for requests, approval or rejection, due dates, returns, messages, and deposit updates where the application supports them; ensure the indicator updates when new notifications arrive and that users can mark items as read. |
| **Reproduction / validation steps** | Use two accounts. Submit a rental request from account A. From account B, respond to it. Without opening the Notifications page, check whether account A can easily discover the resulting notification. Repeat after marking it read and confirm the indicator clears. |
| **Reasoning for priority** | Notifications drive the request-and-approval cycle; missing them directly slows core use. |

### Issue 2 — Starting a direct conversation is inconvenient

| Item | Detail |
|---|---|
| **Type** | Confirmed observation (my own use) |
| **Priority** | **High** |
| **Description** | I cannot conveniently start a direct conversation with another user and have to search for the person. Messaging is not entirely absent or broken; a Messages link exists. |
| **User impact** | Borrowers and owners cannot easily ask questions about pickup, condition, or timing, which can cause misunderstandings and failed rentals. |
| **Recommended improvement** | Add a "Message Owner" action on equipment listings; add "Message Borrower" or "Contact Other User" on rental requests; provide a conversation list with recent conversations; show unread-message indicators; where appropriate, link a conversation to the relevant listing or rental; enforce permissions so users see only conversations they are authorized to see. |
| **Reproduction / validation steps** | Open an equipment listing and try to start a conversation with the owner. Exchange messages using two accounts. Leave the conversation. Verify both users can easily find it again. |
| **Reasoning for priority** | Communication supports every rental, and the current path adds friction at the start of every interaction. |

### Issue 3 — Real email delivery has not been established

| Item | Detail |
|---|---|
| **Type** | Further verification task (current setup is a test address; actual delivery results were not tested) |
| **Priority** | **High** |
| **Description** | The team is still using a made-up or test email address rather than a verified, working email setup. The interface says email delivery requires a verified account address and configured SMTP settings (S07, S19). I have not claimed email is broken, only that real delivery has not been established. Email functions are separate from the browser's password-saving feature. |
| **User impact** | Account verification, password reset, and email notifications cannot be relied on. Users who forget a password may not be able to recover access. |
| **Recommended improvement** | Configure a suitable email delivery service; verify delivery to real, authorized addresses; test account verification if supported; test password recovery and reset emails; test email notifications and preferences; show clear feedback when delivery succeeds or fails; store SMTP credentials and related secrets securely outside source control. |
| **Reproduction / validation steps** | Register with a real, authorized address and check for the verification email. Use "Forgot Password" and confirm the reset email arrives and works. Enable the email-notification preference, trigger a notification, and confirm an email arrives. Record failures and the message the user sees. |
| **Reasoning for priority** | Verification and password recovery are core account functions. |

### Additional observations (lower priority, need confirmation)

| Observation | Source | Suggested follow-up | Priority |
|---|---|---|---|
| Navigation menu content and styling differ between pages. | S02, S04, S07, S13, S16 | Confirm whether intentional; make consistent. | Medium |
| Rental cards show a placeholder instead of the uploaded photo for the tripod. | S22, S26 | Check whether photos should display on rental cards. | Low |
| A rental is "Completed" with an end date later than the capture date. | S03, S22 | Confirm whether this is test data; check how completion relates to dates. | Medium |
| Listings sometimes use placeholder-like test data. | S08 | Use realistic sample data for demonstrations. This is a presentation point, not a defect. | Low |

---

## 9. Recommended Future Work

These are recommendations and verification tasks. They are **not confirmed defects** unless stated in Section 8. Many of these features appear to exist in some form; the question is whether they are verified.

### High priority

- **Notification visibility** — bell/indicator and unread count (Issue 1).
- **More accessible direct messaging** — "Message Owner" and "Message Borrower" actions, conversation list (Issue 2).
- **Working email configuration and delivery** (Issue 3).
- **End-to-end rental workflow validation** — request, approval, payment, pickup, return, deposit, rating, tested with two accounts, including status changes at each step.
- **Core authentication and authorization checks** — verify password hashing, authentication, session handling, and server-side authorization for listing, rental, return, rating, and messaging actions. Treat these as security verification tasks until confirmed. In particular, check that users cannot change rental status or submit ratings for rentals they are not part of.

### Medium priority

- **More extensive hourly booking tests** — whole and fractional hours, invalid dates and times, end before start, availability, overlapping requests, agreement between estimated and recorded price, and enforcement of booking and pricing rules on the server. Confirm the intended rounding and day-counting rules (see Section 5).
- **Return, deposit, late-fee, and damage-handling validation** — who can initiate or confirm a return, why returns are blocked, how overdue rentals are handled, how late fees are calculated, when deposits become refundable, how damage claims or disputes are handled, and whether status changes are recorded consistently.
- **Listing information, search/filter behavior, and rental status transitions** — keep item name, description, condition, rate and unit, availability, pickup arrangements, rental rules, and images clear and consistent. Test search, category filter, and status filter together, plus any price filter, and confirm that rental and listing statuses change in the intended order.
- **Mobile usability and error recovery** — test on a phone-sized screen (menus, cards, forms, dropdowns, buttons, error messages, readability); preserve form input after validation failures; give clear messages for failed uploads, invalid bookings, and failed actions.
- **Data persistence** — after restarting the application, check accounts, listings and images, rental requests and statuses, messages, ratings, notifications, and payment and deposit records. Verify actual storage and backup behavior before concluding anything about data loss.

### Later-stage work

- **Production readiness** — monitoring, logging, backups, and deployment hardening.
- **Broader accessibility testing** — keyboard navigation, form labels, contrast, and ongoing monitoring.
- **Input and upload handling review** — input validation, safe image-upload handling, protection of private user information, and secure handling of secret keys and external service credentials, with credentials kept out of GitHub.
- **Real payment integration** — only if the team decides to implement it (see below).
- **Administrative moderation and account suspension** — if this remains within project scope.
- Additional convenience features (for example, saved searches or reminders).

### Team-reported follow-up items requiring confirmation

The Group F project progress presentation identifies the items below as limitations or follow-up work. They are **team-reported**. I did not test or independently verify them, and "needs confirmation" below does not mean the feature is missing; it means the presentation indicates it should be checked.

| Item (as reported in the presentation) | Suggested next step | Related section |
|---|---|---|
| Damage-charge settlement and dispute handling remain unfinished or in progress. | Confirm the current state with the team, then validate the damage workflow once complete. | 9 (Medium), 10 |
| Production hosting, HTTPS, and secret configuration require confirmation. | Confirm the intended deployment and verify HTTPS and secret handling. | 9 (High, Later-stage), 10 |
| Uploaded images and their inclusion in backups need further attention. | Check where uploaded images are stored and whether backups include them. | 9 (Medium), 10 |
| Email delivery depends on SMTP configuration. | Configure and verify delivery (Issue 3). | 8, 10 |
| Administrative moderation and account suspension may be later-stage work, if still in scope. | Confirm scope with the team. | 9 (Later-stage) |
| Real payment processing is not implemented; the QR payment is a demonstration only. | Keep the demo wording; review separately if real payments are introduced. | 2, 9, 10 |

### Payment transparency

The payment pages say no real money is processed. Keep the "demo payment, no real money" message prominent. If real payment is ever introduced, review payment-provider integration, transaction verification, security, failure handling, and refunds separately.

---

## 10. Testing Limitations

- My manual retesting does not replace a complete regression test.
- Screenshots show visible interface states, not necessarily successful backend operations.
- I did not personally run the team's automated test suite. The only automated-test information is the progress presentation's report of 36 passing tests in the latest full local run; this is attributed to the team, has not been independently verified in this report, and the presentation notes that supporting output had not yet been attached. It should be attached or reviewed.
- The technical follow-up items in Section 9 (damage-charge settlement and disputes, production hosting, HTTPS and secrets, image backups, SMTP, moderation) come from the progress presentation. I did not test them, and they are not claimed as confirmed defects or missing features.
- Source-code security, deployment reliability, and production email delivery require separate verification.
- The demo payment is simulated; no real money is processed.
- The repository pages could not be opened by the tool used to prepare this report, so the source code, README, and technology stack were not inspected.
- The live demo is hosted through ngrok and, when checked during preparation, returned only an ngrok page rather than the app. If it expires or goes offline, further independent verification is limited.
- I have not recorded test dates, browser versions, devices, or logs.
- Screenshots use test data and show only the accounts, listings, and states I captured.
- Which account each screenshot was captured from is not recorded in this report.

---

## 11. Conclusion

After the developers' updates, equipment image upload, hourly rentals, borrower and owner ratings, and password-related behavior worked better when I retested them, and the rental screens now present status, payment, deposit, and due-date information in a structured way. These are manual observations of a prototype, not proof of full correctness or security.

Three issues remain from my own use: new notifications are hard to notice, starting a direct conversation is inconvenient, and real email delivery has not been established. Beyond these, the booking rules, return and deposit handling, permissions, and mobile behavior need further verification.

Continuing to retest after each round of changes, and recording evidence for each result, will help the team improve CampusShare steadily. The team's reported 36 passing automated tests are a separate matter that still needs supporting output. This report does not claim that the project is production-ready.

---

## Appendix A — Screenshot Evidence

### A.1 Where to put the images

Save the report at:

```
docs/AMANDA_FUNCTIONAL_AND_USABILITY_EVALUATION.md
```

Save the images in:

```
docs/images/campusshare/
```

The "Target file name" column below gives **suggested** file names. The original screenshots are named `Screenshot_2026-10-25_at_HH_MM.SS_AM` (no extension in the upload list; they are PNG images). The report links use paths relative to the report, for example `images/campusshare/18-hourly-booking-form-estimate.png`. For the images to display on GitHub:

1. Put each screenshot in `docs/images/campusshare/` and rename it to exactly the target name shown (names are case-sensitive and must end in `.png`).
2. Commit the images in the same branch and pull request as the report.
3. Preview the report on GitHub and confirm no image shows a broken-image icon.

Until the files are placed and renamed, the image links will not display. This report does not claim that any file has been renamed or committed.

**Optional precautions.** These are test accounts, so screenshots are included as evidence. As a precaution you may still crop the token link visible at the bottom of S23 and the password field in S01, and confirm that the other students shown (S03–S05, S08, S25) are comfortable appearing.

### A.2 Before / After

I did not supply matching before-and-after screenshots of the earlier version, so none are labeled Before/After. S08 shows a different set of listings captured earlier in the session and is not a before/after of a fix.

### A.3 Index

| ID | Target file name (suggested) | Original file (as uploaded) | Feature |
|---|---|---|---|
| S01 | 01-dashboard-password-save-prompt.png | Screenshot_2026-10-25_at_12_22.11_AM | Password |
| S02 | 02-student-dashboard.png | Screenshot_2026-10-25_at_12_22.32_AM | Dashboard |
| S03 | 03-owner-requests-return-and-rate-borrower.png | Screenshot_2026-10-25_at_12_23.11_AM | Requests, returns |
| S04 | 04-rate-borrower-form.png | Screenshot_2026-10-25_at_12_23.23_AM | Borrower rating |
| S05 | 05-rate-borrower-options.png | Screenshot_2026-10-25_at_12_23.30_AM | Borrower rating |
| S06 | 06-return-blocked-payment-required.png | Screenshot_2026-10-25_at_12_24.29_AM | Return restriction |
| S07 | 07-notifications-email-preference.png | Screenshot_2026-10-25_at_12_25.48_AM | Notifications |
| S08 | 08-browse-equipment-listings.png | Screenshot_2026-10-25_at_12_28.46_AM | Browse |
| S09 | 09-list-equipment-image-upload.png | Screenshot_2026-10-25_at_12_30.49_AM | Image upload |
| S10 | 10-list-equipment-paid-rental-day.png | Screenshot_2026-10-25_at_12_39.11_AM | Listing pricing |
| S11 | 11-list-equipment-price-unit-options.png | Screenshot_2026-10-25_at_12_39.19_AM | Listing pricing |
| S12 | 12-list-equipment-hourly-window.png | Screenshot_2026-10-25_at_12_39.35_AM | Hourly listing |
| S13 | 13-my-listings.png | Screenshot_2026-10-25_at_12_42.47_AM | My Listings |
| S14 | 14-login-browser-autofill.png | Screenshot_2026-10-25_at_12_44.29_AM | Password |
| S15 | 15-forgot-password.png | Screenshot_2026-10-25_at_12_45.19_AM | Password recovery |
| S16 | 16-browse-equipment-with-tripod.png | Screenshot_2026-10-25_at_12_46.13_AM | Browse |
| S17 | 17-equipment-details-tripod.png | Screenshot_2026-10-25_at_12_46.29_AM | Listing detail |
| S18 | 18-hourly-booking-form-estimate.png | Screenshot_2026-10-25_at_12_47.36_AM | Hourly booking |
| S19 | 19-notifications-list.png | Screenshot_2026-10-25_at_12_48.18_AM | Notifications |
| S20 | 20-qr-payment-macbook.png | Screenshot_2026-10-25_at_12_49.18_AM | Demo payment |
| S21 | 21-confirm-payment-macbook.png | Screenshot_2026-10-25_at_12_49.32_AM | Demo payment |
| S22 | 22-my-rentals-before-payment.png | Screenshot_2026-10-25_at_12_49.55_AM | My Rentals |
| S23 | 23-qr-payment-tripod.png | Screenshot_2026-10-25_at_12_50.06_AM | Demo payment |
| S24 | 24-confirm-payment-dialog.png | Screenshot_2026-10-25_at_12_50.18_AM | Demo payment |
| S25 | 25-rate-owner-validation.png | Screenshot_2026-10-25_at_12_50.37_AM | Owner rating |
| S26 | 26-my-rentals-after-payment-and-review.png | Screenshot_2026-10-25_at_12_51.33_AM | My Rentals |
| S27 | 27-browse-category-filter-options.png | Screenshot_2026-10-25_at_12_52.17_AM | Filters |
| S28 | 28-browse-status-filter-options.png | Screenshot_2026-10-25_at_12_52.24_AM | Filters |
| S29 | 29-browse-search-tripod.png | Screenshot_2026-10-25_at_12_52.57_AM | Search |

### A.4 Screenshots, with what each shows and does not prove

**S01 — Dashboard with browser password prompt**
![Student dashboard with a browser save-password prompt](images/campusshare/01-dashboard-password-save-prompt.png)
*Shows:* the dashboard after login, with the browser offering to save a password. *Does not prove:* secure server-side password storage or secure authentication.

**S02 — Student dashboard**
![Student dashboard](images/campusshare/02-student-dashboard.png)
*Shows:* the full navigation (including Notifications and Messages), summary counts, and quick actions. *Does not prove:* that the counts are correct, or that messaging works. No notification indicator is visible.

**S03 — Owner Requests page**
![Owner requests page with return and rate-borrower actions](images/campusshare/03-owner-requests-return-and-rate-borrower.png)
*Shows:* two request cards with status, payment, deposit, late fee, and damage status, plus "Mark as Returned" and "Rate Borrower". *Does not prove:* that returns, deposits, or fees are calculated correctly.

**S04 — Rate Borrower form**
![Rate Borrower form](images/campusshare/04-rate-borrower-form.png)
*Shows:* the rating and comment form. *Does not prove:* that a rating was saved. My retest result is stated in Sections 5 and 6.

**S05 — Rating options**
![Rate Borrower rating options](images/campusshare/05-rate-borrower-options.png)
*Shows:* the five rating choices (Excellent to Poor). *Does not prove:* eligibility rules or duplicate-rating protection.

**S06 — Return blocked message**
![Message saying payment must be marked paid before return](images/campusshare/06-return-blocked-payment-required.png)
*Shows:* a message that payment must be marked paid before the item can be returned. *Does not prove:* that this rule is enforced on the server, or what exact action triggered the page.

**S07 — Notifications with email preference**
![Notifications page with email preference](images/campusshare/07-notifications-email-preference.png)
*Shows:* an unread notification, "Mark as read" and "View", and an email-preference checkbox with a note that delivery needs a verified address and SMTP settings. *Does not prove:* that email delivery works. It also illustrates that the notification is seen only on this page.

**S08 — Browse Equipment (earlier listing set)**
![Browse equipment page](images/campusshare/08-browse-equipment-listings.png)
*Shows:* listing cards with status labels (Booked, Pending, Expired) and the search and filter bar. *Does not prove:* that statuses are correct. The test-style listing names are demonstration data.

**S09 — List Your Equipment form**
![List equipment form with photo upload field](images/campusshare/09-list-equipment-image-upload.png)
*Shows:* the photo upload field, which states JPG, PNG or WebP and a 5 MB maximum, plus name, category, and description fields. *Does not prove:* that all formats and sizes upload successfully.

**S10 — Paid rental, charged per day**
![Listing form with paid rental and per-day pricing](images/campusshare/10-list-equipment-paid-rental-day.png)
*Shows:* sharing type, price unit (Day), price, deposit, availability dates, and pickup location fields. *Does not prove:* server-side validation of these fields.

**S11 — Price unit options**
![Price unit dropdown showing Day and Hour](images/campusshare/11-list-equipment-price-unit-options.png)
*Shows:* Day and Hour options. *Does not prove:* that both work in every scenario.

**S12 — Hourly listing window**
![Listing form with hourly pricing and pickup window](images/campusshare/12-list-equipment-hourly-window.png)
*Shows:* earliest pickup and latest return times and the note that hourly bookings must fit within the daily window. *Does not prove:* that the window is enforced on the server.

**S13 — My Listings**
![My Listings page](images/campusshare/13-my-listings.png)
*Shows:* an uploaded tripod photo, price, deposit, availability, pickup, status, and View / Edit / Delete actions. *Does not prove:* that editing or deleting works correctly.

**S14 — Login with browser autofill**
![Login page with browser autofill suggestion](images/campusshare/14-login-browser-autofill.png)
*Shows:* the login form, a "Resend verification email" link, a Register link, and a browser saved-login suggestion. *Does not prove:* secure password handling, or that verification emails are delivered. Contains test-account email addresses.

**S15 — Forgot Password**
![Forgot Password page](images/campusshare/15-forgot-password.png)
*Shows:* a reset form with a privacy-preserving message. *Does not prove:* that a reset email is sent or that resetting works.

**S16 — Browse with tripod listing**
![Browse equipment page with the tripod listing](images/campusshare/16-browse-equipment-with-tripod.png)
*Shows:* an uploaded photo on a listing card, hourly pricing (¥20/hour), and an Available status. *Does not prove:* that all images display correctly.

**S17 — Equipment details**
![Equipment details page for the tripod listing](images/campusshare/17-equipment-details-tripod.png)
*Shows:* the uploaded photo at full size with category, description, and condition. *Does not prove:* long-term image storage.

**S18 — Hourly booking form with estimate**
![Hourly booking form showing estimated cost](images/campusshare/18-hourly-booking-form-estimate.png)
*Shows:* 26 October 2026, 09:00 AM to 02:30 PM, and "Estimated rental cost: ¥120 (6 hours × ¥20)". *Does not prove:* the intended rounding policy, or behavior for edge cases.

**S19 — Notifications list**
![Notifications page with two notifications](images/campusshare/19-notifications-list.png)
*Shows:* one unread and one read notification. *Does not prove:* that new notifications are easy to discover (my observation is that they are not), or how the read state changed.

**S20 — QR payment (macbook)**
![Demo QR payment page for the macbook rental](images/campusshare/20-qr-payment-macbook.png)
*Shows:* "Demo payment only — no real money is processed," the amount, status, QR code, and a 10-minute expiry note. *Does not prove:* any real payment.

**S21 — Confirm payment (macbook)**
![Confirm payment page for the macbook rental](images/campusshare/21-confirm-payment-macbook.png)
*Shows:* an explicit statement that no real money will be processed. *Does not prove:* correct recording of payment.

**S22 — My Rentals before payment**
![My Rentals page with an unpaid tripod rental](images/campusshare/22-my-rentals-before-payment.png)
*Shows:* an unpaid hourly rental with a "Pay with QR Code" button, due-date messages, deposit information, and a "Rate Owner" button on a completed rental. *Does not prove:* correct status transitions.

**S23 — QR payment (tripod)**
![Demo QR payment page for the tripod rental](images/campusshare/23-qr-payment-tripod.png)
*Shows:* the amount ¥120.00 for the hourly rental. *Does not prove:* real payment. A confirmation link with a token is visible at the bottom of the original screenshot; consider cropping it.

**S24 — Payment confirmation dialog**
![Browser dialog asking to confirm the payment](images/campusshare/24-confirm-payment-dialog.png)
*Shows:* a "Confirm this payment?" prompt. *Does not prove:* the result of the action.

**S25 — Rate Owner validation**
![Rate Owner form showing a validation message](images/campusshare/25-rate-owner-validation.png)
*Shows:* the validation message "Please select an item in the list." when no rating is chosen. *Does not prove:* rating eligibility or duplicate prevention.

**S26 — My Rentals after payment and review**
![My Rentals page after payment and owner review](images/campusshare/26-my-rentals-after-payment-and-review.png)
*Shows:* the tripod rental marked Paid and a completed rental showing "You have reviewed the owner." *Does not prove:* that all underlying records are correct.

**S27 — Category filter options**
![Browse page with category dropdown open](images/campusshare/27-browse-category-filter-options.png)
*Shows:* the category choices. *Does not prove:* that filtering returns correct results.

**S28 — Status filter options**
![Browse page with status dropdown open](images/campusshare/28-browse-status-filter-options.png)
*Shows:* the status choices (Available, Pending, Booked). *Does not prove:* that filtering returns correct results.

**S29 — Search for "tripod"**
![Browse results for the search term tripod](images/campusshare/29-browse-search-tripod.png)
*Shows:* one matching listing, now marked Booked. *Does not prove:* search behavior beyond this term, or what triggered the change from Available to Booked.

---

## Appendix B — Reusable Test Record Template

Copy this block for each test. Leave unknown fields blank or write "Not recorded".

```
Test ID:
Feature:
Date tested:
Preconditions:
Steps:
Expected result:
Actual result:
Status:
Screenshot or evidence:
Issue severity:
Recommended action:
```

**Suggested status values:** Passed — manually retested · Visible in screenshots · Needs further testing · Not yet tested · Not established by available evidence · Failed (use only with evidence)
