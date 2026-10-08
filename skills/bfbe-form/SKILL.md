---
name: bfbe-form
description: "Use when placing, wiring or styling BFB Advanced Forms (`bfbe-form`): a nestable form you build from field elements and step elements, with uploads and signatures, sent by Bricks' own script and actions. Read before writing its settings."
---

# BFB Advanced Forms (`bfbe-form`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-form.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/form/

## What it is
A nestable form you build from field elements and step elements, with uploads and signatures, sent by Bricks' own script and actions. Rules show or hide its parts and common Bricks elements inside it, and can also require, disable or fill in a field. The server runs the rules again on every send, so an answer a rule hides is dropped. A Formula prices the answers into a live total that the server recomputes, and that total can go to Stripe Checkout or a WooCommerce cart line.

**Not for:** Not for taking card details on your own page: payment happens on Stripe's own Checkout page. Uploads, signatures, steps, totals and other repeaters cannot sit inside a Repeater's rows, which suit rows of simple fields.

**Costs a page:** CSS 2.57 KB, JS 3.06 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable. Its own children: `bfbe-form-text`, `bfbe-form-button`, `bfbe-form-choice`, `bfbe-form-number`, `bfbe-form-date`, `bfbe-form-upload`, `bfbe-form-signature`, `bfbe-form-repeater`, `bfbe-form-step`, `bfbe-form-progress`, `bfbe-form-summary`, `bfbe-form-total`, with any Bricks block between them.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-form",
    "settings": {},
    "children": [
        {
            "name": "bfbe-form-text",
            "settings": {
                "label": "Name",
                "key": "name",
                "type": "text",
                "required": true,
                "autocomplete": "name"
            }
        },
        {
            "name": "bfbe-form-text",
            "settings": {
                "label": "Email",
                "key": "email",
                "type": "email",
                "required": true,
                "autocomplete": "email"
            }
        },
        {
            "name": "bfbe-form-text",
            "settings": {
                "label": "Message",
                "key": "message",
                "type": "textarea"
            }
        },
        {
            "name": "bfbe-form-button",
            "settings": {
                "kind": "send"
            }
        }
    ]
}
```

`bfbe-form-text` (BFB Text Field), 91 controls, schema `../bfbe-schemas/references/elements/bfbe-form-text.json`.

`bfbe-form-button` (BFB Form Button), 96 controls, schema `../bfbe-schemas/references/elements/bfbe-form-button.json`.

`bfbe-form-choice` (BFB Choice Field), 154 controls, schema `../bfbe-schemas/references/elements/bfbe-form-choice.json`, nestable itself.

`bfbe-form-number` (BFB Number Field), 126 controls, schema `../bfbe-schemas/references/elements/bfbe-form-number.json`.

`bfbe-form-date` (BFB Date Field), 140 controls, schema `../bfbe-schemas/references/elements/bfbe-form-date.json`.

`bfbe-form-upload` (BFB Upload Field), 145 controls, schema `../bfbe-schemas/references/elements/bfbe-form-upload.json`.

`bfbe-form-signature` (BFB Signature Field), 70 controls, schema `../bfbe-schemas/references/elements/bfbe-form-signature.json`.

`bfbe-form-repeater` (BFB Repeater), 75 controls, schema `../bfbe-schemas/references/elements/bfbe-form-repeater.json`, nestable itself.

`bfbe-form-step` (BFB Form Step), 43 controls, schema `../bfbe-schemas/references/elements/bfbe-form-step.json`, nestable itself.

`bfbe-form-progress` (BFB Form Progress), 88 controls, schema `../bfbe-schemas/references/elements/bfbe-form-progress.json`.

`bfbe-form-summary` (BFB Form Summary), 66 controls, schema `../bfbe-schemas/references/elements/bfbe-form-summary.json`.

`bfbe-form-total` (BFB Form Total), 98 controls, schema `../bfbe-schemas/references/elements/bfbe-form-total.json`.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Ungrouped
Styling only, every key in the schema file: `uploadButtonTypography`, `uploadButtonBackgroundColor`, `uploadButtonBorder`.

### Fields (`bfbeFields`)
- `disableFormValidationOn` (select) **Disable form validation**: options: `input` On input, `blur` On blur. Bricks' own setting. Fields are checked on input, blur and send, and you can turn off the check On input, On blur or both.
- `disableBrowserValidation` (checkbox) **Don't use browser validation**. Bricks' own setting. Tick it to turn off the browser's own checks and use the form's instead.
- `validateAllFieldsOnSubmit` (checkbox) **Validate all fields on submit**: only when `disableBrowserValidation` is `1`. Bricks' own setting. With Don't use browser validation ticked, a send shows an error for every field that fails, not just one.
- `requiredAsterisk` (checkbox) **Asterisk on required labels**. Tick it to put an asterisk on the label of every required field.
Styling, in the schema file: `fieldGap`.

### Actions (`actions`)
- `actions` (select) **Actions after successful form submit**: options: `custom` Custom, `email` Email, `webhook` Webhook, `redirect` Redirect, `mailchimp` Mailchimp, `sendgrid` SendGrid, `login` User login, `registration` User registration, `lost-password` Lost password, `reset-password` Reset password, `create-post` Create post, `update-post` Update post, `save-submission` Save submission, `bfbe-user` Update the user, `bfbe-meta` Update post fields, `bfbe-delete` Delete the post, `bfbe-pdf` Quote PDF, `bfbe-pay` Pay with Stripe. Pick what happens after a send. Bricks' own actions are here, with five more from BFB Elements: Update the user, Update post fields, Delete the post, Quote PDF and Pay with Stripe. An action with settings opens a group of its own.
- `successMessage` (text) **Success message**: default `Message successfully sent. We will get back to you as soon as possible.`. Bricks' own message after a successful send.

### Notices (`notices`)
- `noticeCloseAfter` (number) **Close after (ms)**
- `noticeCloseButton` (checkbox) **Close button**

### Email (`email`)
The whole group shows only when `actions` is `email`.
- `emailSubject` (text) **Subject**: default `Contact form request`. Set the email's subject. Unless set, it reads Finish your form on, then your site's name.
- `emailTo` (select) **Send to email address**: options: `admin_email` Admin email (dev-email@wpengine.local) (default), `custom` Custom email address
- `emailToCustom` (text) **Send to custom email address**: only when `emailTo` is `custom`. Accepts multiple addresses separated by comma.
- `emailRoutes` (repeater) **Send to, by answer**: placeholder Recipients. Add rows that send the email to more addresses when an answer holds. Each row has Field key, Test, Value and Send to, and every row that holds adds its addresses.
- `emailRoutesKeep` (checkbox) **Keep the usual recipients too**: only when `emailRoutes` is set. Off by default, so a row that holds replaces the usual recipients. Tick it to send to both.
- `emailBcc` (text) **BCC email address**
- `fromEmail` (text) **From email address**
- `fromName` (text) **From name**: default `bfb-elements`. Default: Site title.
- `replyToEmail` (text) **Reply to email address**: placeholder Name. Comma-separated list of name and email address or email addresses only. Default: Email address in submitted form.
- `emailContent` (textarea) **Email content**. Use field IDs to personalize your message. Type {{all_fields}} to output all the field labels and values of the submitted form. Learn more (https://academy.bricksbuilder.io/article/form-element/#email).
- `emailErrorMessage` (text) **Error message**: default `Submission failed. Please reload the page and try to submit the form again.`. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.
- `htmlEmail` (checkbox) **HTML email**: default `true`

### Webhook (`webhook`)
The whole group shows only when `actions` is `webhook`.
- `webhooks` (repeater) **Endpoints**: placeholder Endpoint. Bricks' own list of addresses each submission goes to, each with its Name, Endpoint URL, Data format, Data and Headers. BFB Elements adds the four settings below to every endpoint.
- `webhookMaxSize` (number) **Max payload size (KB)**: placeholder 1024. Maximum size of the webhook payload in kilobytes. (Default: 1024).
- `webhookRateLimit` (checkbox) **Rate limiting**. Limit the number of webhook requests that can be sent per hour.
- `webhookRateLimitRequests` (number) **Max requests per hour**: placeholder 60; only when `webhookRateLimit` is `1`. Maximum number of webhook requests allowed per hour. (Default: 60).
- `webhookErrorIgnore` (checkbox) **Continue on error**. If enabled, form submission will succeed even if the webhook fails. Errors will be logged to the server error log.
- `webhookErrorMessage` (text) **Error message**: only when `webhookErrorIgnore` is not set. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.

### Confirmation email (`confirmation`)
The whole group shows only when `actions` is `email`.
- `confirmationEmailSubject` (text) **Subject**. Set the email's subject. Unless set, it reads Finish your form on, then your site's name.
- `confirmationEmailTo` (text) **Send to email address**. Default: Email address in submitted form.
- `confirmationFromEmail` (text) **From email address**. Default: Admin email.
- `confirmationFromName` (text) **From name**. Default: Site title.
- `confirmationReplyToEmail` (text) **Reply to email address**: placeholder Name. Comma-separated list of name and email address or email addresses only. Default: From email address.
- `confirmationEmailContent` (textarea) **Email content**. Use field IDs to personalize your message. Type {{all_fields}} to output all the field labels and values of the submitted form. Learn more (https://academy.bricksbuilder.io/article/form-element/#email).
- `confirmationEmailHTML` (checkbox) **HTML email**

### Redirect (`redirect`)
The whole group shows only when `actions` is `redirect`.
- `redirectAdminUrl` (checkbox) **Redirect to admin area**: placeholder https://bfb-elements.local/wp-admin/
- `redirect` (text) **Custom redirect URL**: placeholder https://bfb-elements.local
- `redirectTimeout` (number) **Redirect after (ms)**

### Mailchimp (`mailchimp`)
The whole group shows only when `actions` is `mailchimp`.
- `mailchimpDoubleOptIn` (checkbox) **Double opt-in**: only when `apiKeyMailchimp` is set
- `mailchimpList` (select) **List**: options: ; only when `apiKeyMailchimp` is set
- `mailchimpGroups` (select) **Groups**: options: ; only when `apiKeyMailchimp` is set and `mailchimpList` is set
- `mailchimpEmail` (select) **Field: Email**: options: ; only when `apiKeyMailchimp` is set
- `mailchimpFirstName` (select) **First name**: options: ; only when `apiKeyMailchimp` is set
- `mailchimpLastName` (select) **Last name**: options: ; only when `apiKeyMailchimp` is set
- `mailchimpPendingMessage` (text) **Pending message**: default `Please check your email to confirm your subscription.`; only when `apiKeyMailchimp` is set
- `mailchimpErrorMessage` (text) **Error message**: default `Sorry, but we could not subscribe you.`; only when `apiKeyMailchimp` is set. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.

### Sendgrid (`sendgrid`)
The whole group shows only when `actions` is `sendgrid`.
- `sendgridList` (select) **List**: options: ; only when `apiKeySendgrid` is set
- `sendgridEmail` (select) **Field: Email**: options: ; only when `apiKeySendgrid` is set
- `sendgridFirstName` (select) **Field: First name**: options: ; only when `apiKeySendgrid` is set
- `sendgridLastName` (select) **Field: Last name**: options: ; only when `apiKeySendgrid` is set
- `sendgridErrorMessage` (text) **Error message**: default `Sorry, but we could not subscribe you.`; only when `apiKeySendgrid` is set. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.

### User Login (`login`)
The whole group shows only when `actions` is `login`.
- `loginName` (select) **Field: Login**: options: 
- `loginPassword` (select) **Field: Password**: options: 
- `loginRemember` (select) **Field: Remember me**: options: 
- `loginErrorMessage` (text) **Error message**. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.

### User Registration (`registration`)
The whole group shows only when `actions` is `registration`.
- `registrationEmail` (select) **Field: Email**: options: 
- `registrationPassword` (select) **Field: Password**: options: . Autogenerated if no password is required/submitted.
- `registrationPasswordMinLength` (number) **Password min. length**
- `registrationUserName` (select) **Field: User name**: options: . Auto-generated if form only requires email address for registration.
- `registrationFirstName` (select) **Field: First name**: options: 
- `registrationLastName` (select) **Field: Last name**: options: 
- `registrationRole` (select) **Role**: options: `editor` Editor, `author` Author, `contributor` Contributor, `subscriber` Subscriber (default), `customer` Customer, `shop_manager` Shop manager
- `registrationAutoLogin` (checkbox) **Auto log in user**. Log in user after successful registration. Tip: Set action "Redirect" to redirect user to the account/admin area.
- `registrationWPNotification` (checkbox) **Send WordPress notification**. Trigger "register_new_user" action to send WordPress notification. Learn more (https://academy.bricksbuilder.io/article/form-element/#login-registration).

### Lost password (`lostPassword`)
The whole group shows only when `actions` is `lost-password`.
- `lostPasswordEmailUsername` (select) **Field: Email or username**: options: 

### Reset password (`resetPassword`)
The whole group shows only when `actions` is `reset-password`.
- `resetPasswordNew` (select) **Field: Password**: options: 

### Create post (`createPost`)
The whole group shows only when `actions` is `create-post`.
- `createPostType` (select) **Post type**: options: . For Posts of a type, type the post type, post unless set.
- `createPostErrorMessage` (text) **Error message**: only when `createPostType` is set and `createPostDisableCapabilityCheck` is not set. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.
- `createPostDisableCapabilityCheck` (checkbox) **Disable capability checks**: only when `createPostType` is set
- `createPostTitle` (select) **Post title**: options: ; only when `createPostType` is set
- `createPostContent` (select) **Post content**: options: ; only when `createPostType` is set
- `createPostExcerpt` (select) **Post excerpt**: options: ; only when `createPostType` is set
- `createPostFeaturedImage` (select) **Featured image**: options: ; only when `createPostType` is set
- `createPostStatus` (select) **Post status**: options: ; only when `createPostType` is set
- `createPostMeta` (repeater) **Post meta**: only when `createPostType` is set
- `createPostTaxonomies` (repeater) **Taxonomies**: only when `createPostType` is set

### Update post (`updatePost`)
The whole group shows only when `actions` is `update-post`.
- `updatePostId` (select) **Post to update**: placeholder Select post/page
- `updatePostErrorMessage` (text) **Error message**. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.
- `updatePostDisableCapabilityCheck` (checkbox) **Disable capability checks**
- `updatePostTitle` (select) **Post title**: options: 
- `updatePostContent` (select) **Post content**: options: 
- `updatePostExcerpt` (select) **Post excerpt**: options: 
- `updatePostFeaturedImage` (select) **Featured image**: options: 
- `updatePostStatus` (select) **Post status**: options: 
- `updatePostMeta` (repeater) **Post meta**
- `updatePostTaxonomies` (repeater) **Taxonomies**

### Spam protection (`spam`)
- `enableRecaptcha` (checkbox) **reCAPTCHA (Google)**: only when `apiKeyGoogleRecaptcha` is set
- `enableTurnstile` (checkbox) **Turnstile (Cloudflare)**: only when `apiKeyTurnstile` is set
- `turnstileSize` (select) **Turnstile: Size**: options: `normal` Normal (default), `compact` Compact, `flexible` Flexible; only when `enableTurnstile` is `1`
- `turnstileTheme` (select) **Turnstile: Theme**: options: `light` Light, `dark` Dark; only when `enableTurnstile` is `1`
- `turnstileLabel` (text) **Turnstile: Label**: only when `enableTurnstile` is `1`
- `enableHCaptcha` (select) **hCaptcha**: options: `visible` Visible, `invisible` Invisible; only when `apiKeyHCaptcha` is set
- `hCaptchaSize` (select) **hCaptcha: Size**: options: `normal` Normal (default), `compact` Compact; only when `enableHCaptcha` is `visible`
- `hCaptchaTheme` (select) **hCaptcha: Theme**: options: `light` Light (default), `dark` Dark; only when `enableHCaptcha` is `visible`

### Save submission (`save-submission`)
The whole group shows only when `actions` is `save-submission`.
- `submissionFormName` (text) **Form name**: placeholder Contact form. Descriptive name for viewing submissions on the "Form Submissions" page (https://bfb-elements.local/wp-admin/admin.php?page=bricks-form-submissions).
- `submissionSaveIp` (checkbox) **Save IP address**
- `submissionMaxEntries` (number) **Max. entries**. Set maximum number of form submissions that you want to store in the database.
- `submissionMaxEntriesErrorMessage` (text) **Error message**: placeholder Maximum number of entries reached.. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.
- `submissionDupEntries` (repeater) **Compare with (Field ID)**
- `submissionDupEntriesErrorMessage` (text) **Error message**: placeholder Duplicate entries not allowed.. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.

### Unlock password protection (`unlock-password-protection`)
The whole group shows only when `actions` is `unlock-password-protection`.
- `passwordProtectionPassword` (select) **Field: Password**: options: . If no form field is selected, the first password field in the form is used.
- `passwordProtectionErrorMessage` (text) **Error message**. Type the words for an answer that fails a check. Left blank, the browser says what is wrong.

### Update the user (`bfbeUser`)
The whole group shows only when `actions` is `bfbe-user`.
- `userRows` (repeater) **Fields to change**. Add one row per field of the logged-in visitor's profile. Each has Change (First name, Last name, Nickname, Name shown, Website, About or A custom field), Field name, How, From the answer, By and Kept by. It never changes a role, a password or an email address.
- `userRefused` (text) **When not logged in**: placeholder Please log in first.. Type the words a visitor who is not logged in sees, Please log in first. unless set.

### Update post fields (`bfbeMeta`)
The whole group shows only when `actions` is `bfbe-meta`.
- `metaPost` (select) **Which post**: options: `current` The page it is on (default), `field` The post an answer names, `url` The post the address names. Pick The page it is on (the default), The post an answer names, or The post the address names. For the last two, Its key names the answer or the address parameter that holds the post's ID.
- `metaPostKey` (text) **Its key**: placeholder post_id; only when `metaPost` is `field` or `url`. The answer or the address parameter that holds its ID.
- `metaWho` (select) **Who may**: options: `editors` Who can edit the post (default), `anyone` Anyone, to count. Who can edit the post (the default), or Anyone, to count, which lets any visitor add or take away a fixed amount on a post the public can see, and nothing more.
- `metaRows` (repeater) **Fields to change**. Add one row per field of the logged-in visitor's profile. Each has Change (First name, Last name, Nickname, Name shown, Website, About or A custom field), Field name, How, From the answer, By and Kept by. It never changes a role, a password or an email address.
- `metaRefused` (text) **When not allowed**: placeholder You cannot change this.. Type the words shown when the change is refused, You cannot change this. unless set.

### Delete the post (`bfbeDelete`)
The whole group shows only when `actions` is `bfbe-delete`.
- `deletePost` (select) **Which post**: options: `current` The page it is on (default), `field` The post an answer names, `url` The post the address names. Pick The page it is on (the default), The post an answer names, or The post the address names. For the last two, Its key names the answer or the address parameter that holds the post's ID.
- `deletePostKey` (text) **Its key**: placeholder post_id; only when `deletePost` is `field` or `url`. The answer or the address parameter that holds its ID.
- `deleteWho` (select) **Who may**: options: `author` Its author (default), `deleters` Anyone who may delete it. Who can edit the post (the default), or Anyone, to count, which lets any visitor add or take away a fixed amount on a post the public can see, and nothing more.
- `deleteHow` (select) **How**: options: `trash` Into the bin (default), `delete` For good. Move the post Into the bin (the default) or delete it For good.
- `deleteTypes` (text) **Only these post types**: placeholder post, listing. List post types, with commas between them, to limit which posts the form may delete.
- `deleteRefused` (text) **When not allowed**: placeholder You cannot delete this.. Type the words shown when the change is refused, You cannot change this. unless set.

### Quote PDF (`bfbePdf`)
The whole group shows only when `actions` is `bfbe-pdf`.
- `pdfTitle` (text) **Title**: placeholder Your quote. Set the PDF's title, Your quote unless set.
- `pdfIntro` (textarea) **Opening words**: placeholder Thank you for asking. Here is what you chose.. Type words for the top of the PDF, under the title.
- `pdfAnswers` (select) **Answers in it**: options: `shown` Every answer given (default), `none` None, the sum only. Every answer given (the default) or None, the sum only. A priced form's sum is added either way.
- `pdfFooter` (textarea) **Small print**: placeholder Prices hold for 30 days.. Type words for the foot of the PDF, such as how long your prices hold.
- `pdfName` (text) **File name**: placeholder quote. Set the PDF's file name, quote unless set.
- `pdfLink` (select) **Download**: options: `link` A link under the message (default), `none` No link. A link under the message (the default) or No link. Link words names it, Download your quote (PDF) unless set, and the link is one nobody can guess.
- `pdfLinkText` (text) **Link words**: placeholder Download your quote (PDF); only when `pdfLink` is not `none`
- `pdfAttach` (select) **Attach it**: options: `email` To the email, `confirmation` To the confirmation email, `both` To both. Attach the PDF To the email, To the confirmation email or To both. It is not attached unless you pick one, and it rides on the Email action.
- `pdfDays` (number) **Kept for (days)**: placeholder 7. Set how long the PDF's link works, 7 days unless set, up to 90. A PDF is deleted once its days are over.

### Pay with Stripe (`bfbePay`)
The whole group shows only when `actions` is `bfbe-pay`.
- `payName` (text) **What they pay for**: placeholder Your order. Type the product name on Stripe's page. The default is Your order. Keys go in BFB Elements, Settings, under Stripe payments, or in wp-config.php constants, never in the page.
- `payCurrency` (text) **Currency code**: placeholder EUR. Type three letters as Stripe names the currency, such as EUR. There is no default, so a blank code or a missing Stripe key stops the payment from starting.
- `payEmail` (text) **Receipt to the answer**: placeholder The first email field. Name the field whose address goes to Stripe's Checkout as the customer's email. Left blank, it takes the earliest email field the visitor answered.
- `paySuccess` (text) **After paying, go to**: placeholder This page. Set where visitors land after paying. Unless you set a page, they come back to this page with bfbe_paid added to its address.
- `payCancel` (text) **If they stop, go to**: placeholder This page. Set where visitors land when they leave Stripe's page without paying, this page unless set.
- `payNothing` (text) **When there is nothing to pay**: placeholder There is nothing to pay.. Type the words shown when the total is zero or less, There is nothing to pay. unless set.

### Steps (`bfbeSteps`)
- `quiet` (checkbox) **Nothing is sent**. Tick it to make the form a calculator, with no Send button and no actions.
- `stepsMotion` (select) **Transition**: options: `slide` Sliding (default), `fade` Fading, `none` At once. Choose how a step changes: Sliding (the default), Fading or At once.
- `stepsEasing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS; only when `stepsMotion` is not `none`. Choose how a Sliding or Fading change speeds up and slows down, Snappy unless set. Pick Custom and type your own curve in Custom curve.
- `stepsScroll` (select) **On a step change**: options: `form` Scroll to the form (default), `still` Keep the page still. Scroll to the form (the default) or Keep the page still. Scroll offset leaves room for a sticky header, 0px unless set.
- `stepsOffset` (number) **Scroll offset**: placeholder 0px; with a unit; only when `stepsScroll` is not `still`. Room for a sticky header.
- `stepsEnter` (select) **Enter in a field**: options: `next` Moves to the next step (default), `none` Does nothing. Pressing Enter Moves to the next step (the default) or Does nothing.
- `stepsCheck` (select) **Before Next**: options: `check` Check the step (default), `skip` Move on, check on Send. Check the step, the default, holds visitors on a step until its fields pass. Move on, check on Send lets them continue and checks every field at the end.
- `stepsSuccess` (select) **After a successful send**: options: `clear` The message alone, every step done (default), `first` Back to the first step, `stay` Stay on the last step. The message alone, every step done is the default. The other choices go back to step one or Stay on the last step.
- `stepsHash` (checkbox) **Step in the address**. Tick it to put the step in the page address, so a link can open a step and the browser's Back goes back a step.
- `stepsOf` (text) **Count text**: placeholder Step %1$s of %2$s. Set the words of the step count, Step %1$s of %2$s unless set, where %1$s is the step and %2$s the number of steps. Form Progress announces it on each change and can show it.
Styling, in the schema file: `stepsDuration`, `stepsEasingCustom`.

### Pricing (`bfbeSum`)
- `base` (number) **Starting amount**: placeholder 0. Use this to add a fixed amount to every total, on top of whatever the choices or the Formula make. It is 0 by default.
- `formula` (textarea) **Formula**: placeholder rooms * 45 + service + (windows ? 35 : 0). Write a line such as rooms * 45 + service + (windows ? 35 : 0) that names fields by their key. It reads + - * / and %, comparisons, a ? : choice, and min, max, round, ceil, floor, abs, pow, sqrt and sum.
- `roundTo` (number) **Round to**: placeholder No rounding. Round the finished total to the nearest multiple you set. There is no rounding unless set.
- `least` (number) **Never below**: placeholder No floor. Set a floor the total never goes under. There is no floor unless set.
- `taxRate` (number) **Tax (%)**: placeholder None. Set a tax rate as a percentage, or leave it empty for no tax. Once set, choose Added on top or Already in the prices under The tax is, and name it in Tax label, VAT unless set.
- `taxIn` (select) **The tax is**: options: `added` Added on top (default), `included` Already in the prices; only when `taxRate` is set
- `taxLabel` (text) **Tax label**: placeholder VAT; only when `taxRate` is set
- `over` (number) **Above this amount**: placeholder No ceiling. Set a ceiling for the total. A total at or over it shows the words in Say instead, Talk to us unless set, and nothing is charged. There is no ceiling by default.
- `overText` (text) **Say instead**: placeholder Talk to us; dynamic data accepted; only when `over` is set
- `subtotalLabel` (text) **Subtotal**: placeholder Subtotal. Name the subtotal line, Subtotal unless set. It shows when a discount or tax added on top is in the sum.
- `discountLabel` (text) **Discount**: placeholder Discount. Name the discount line, Discount unless set.
- `savingsLabel` (text) **Savings**: placeholder You save. Name the savings line, You save unless set. It shows when a Was price is beaten.
- `currency` (text) **Currency**: placeholder £; dynamic data accepted. Set the sign or word every price is written with, £ unless set. It takes dynamic data.
- `currencyAt` (select) **Currency goes**: options: `before` Before the number (default), `after` After the number. Before the number (the default) or After the number.
- `decimals` (number) **Decimals**: placeholder 0. Set how many decimals prices show, 0 unless set, up to 4.
- `thousands` (text) **Thousands mark**: placeholder ,. Set the mark between thousands, a comma unless set.
- `decimalMark` (text) **Decimal mark**: placeholder .. Set the mark before the decimals, a full stop unless set.

### Answers (`bfbeAnswers`)
- `keepAnswers` (checkbox) **Keep the answers after sending**. Tick it for a form that is sent again, like a profile, so it keeps its answers.
- `warnLeave` (checkbox) **Warn before leaving it half filled**. Tick it to make the browser ask before a visitor leaves with answers not yet sent.

### Label and note (`bfbeText`)
- `labelsAt` (select) **Labels**: options: `above` Above the field (default), `border` Floating, on the border. Above the field (the default) or Floating, on the border, where a box's label rests inside it and rises onto its top border while the box is in use or filled.
Styling, in the schema file: `labelTypography`, `noteTypography`, `valueTypography`, `headingTypography`, `innerGap`, `floatHeight`, `floatInset`, `floatGap`, `floatRestColor`, `floatFocusColor`.

### Input (`bfbeInput`)
Styling only, every key in the schema file: `inputBackground`, `inputBorder`, `inputPadding`, `inputTypography`, `inputPlaceholder`, `inputFocus`.

### Slider (`bfbeSlider`)
Styling only, every key in the schema file: `accent`, `trackHeight`, `trackColor`, `trackFill`, `dotSize`, `dotBorder`, `bubbleGap`, `bubbleBackground`, `bubbleColor`, `bubblePadding`, `bubbleBorder`, `bubbleShadow`, `tailSize`, `tailColor`, `bubbleTypography`, `sliderGap`, `tickGap`, `tickTypography`.

### Choices styling (`bfbeOpts`)
Styling only, every key in the schema file: `optPadding`, `optAlign`, `optBorder`, `optBackground`, `optHover`, `optChosen`, `optChosenText`, `optChosenBorder`, `optsBackground`, `optsBorder`, `optsPadding`, `optsShadow`, `optGap`, `optMin`, `optColumns`, `optTitleTypography`, `optNoteTypography`, `optPriceTypography`, `optIconSize`, `optIconColor`, `badgeBackground`, `badgeColor`, `badgeTypography`, `badgeGap`, `badgePadding`, `badgeBorder`, `wasTypography`.

### Tick box (`bfbeCheck`)
Styling only, every key in the schema file: `checkSize`, `checkRadius`, `checkGap`, `checkBackground`, `checkLine`, `checkMarkColor`.

### Switch (`bfbeSwitch`)
Styling only, every key in the schema file: `rowPadding`, `rowBorder`, `rowBackground`, `swWidth`, `swHeight`, `swPad`, `swOff`, `swOn`, `swBorder`, `swDot`, `swDotOff`, `swDotOn`, `swDotBorder`.

### Dropdown (`bfbeDrop`)
Styling only, every key in the schema file: `ddMenuBackground`, `ddColor`, `ddPriceTypography`, `ddMenuBorder`, `ddMenuShadow`, `ddMenuPadding`, `ddMaxHeight`, `ddOffset`, `ddRowPadding`, `ddRowGap`, `ddOver`, `ddOverColor`, `ddChosen`, `ddChosenColor`, `ddArrow`.

### Number arrows (`bfbeArrows`)
Styling only, every key in the schema file: `arrowWidth`, `arrowSize`, `arrowGap`, `arrowColor`, `arrowHoverColor`, `arrowBackground`, `arrowHoverBackground`, `arrowDivider`, `arrowBorder`.

### Calendar (`bfbeCal`)
Styling only, every key in the schema file: `calWidth`, `calBackground`, `calBorder`, `calShadow`, `calPadding`, `calOffset`, `calHeadSpace`, `calWeekSpace`, `calDayGap`, `calHeadLine`, `calHeadLineColor`, `calWeekLine`, `calWeekLineColor`, `calMonthTypography`, `calMonthPadding`, `calYearPadding`, `calHeadHoverBg`, `calYearArrow`, `calYearArrowHover`, `calArrowSize`, `calArrowPadding`, `calArrowColor`, `calArrowHover`, `calArrowBg`, `calArrowHoverBg`, `calArrowBorder`, `calArrowHoverBorder`, `calWeekdayTypography`, `calTimeTypography`, `calTimeBackground`, `calTimeBorder`, `calClockLine`, `calClockLineColor`.

### Calendar days (`bfbeCalDays`)
Styling only, every key in the schema file: `calDayTypography`, `calDaySize`, `calDayPadding`, `calDayBg`, `calDayColor`, `calDayBorder`, `calDayHoverBg`, `calDayHoverColor`, `calDayHoverBorder`, `calTodayBg`, `calTodayColor`, `calTodayBorder`, `calTodayHoverBg`, `calTodayHoverColor`, `calTodayHoverBorder`, `calSelected`, `calSelectedColor`, `calSelectedBorder`, `calSelectedHoverBg`, `calSelectedHoverColor`, `calSelectedHoverBorder`, `calRange`, `calRangeColor`, `calRangeBorder`, `calRangeHoverBg`, `calRangeHoverColor`, `calRangeHoverBorder`, `calShutBg`, `calShut`, `calShutBorder`, `calShutHoverBg`, `calShutHoverColor`, `calShutHoverBorder`, `calOtherBg`, `calOther`, `calOtherBorder`, `calOtherHoverBg`, `calOtherHoverColor`, `calOtherHoverBorder`.

### Stepper (`bfbeStepper`)
Styling only, every key in the schema file: `stepperBackground`, `stepperBorder`, `stepperPadding`, `stepperGap`, `stepperWidth`, `stepTypography`, `stepBackground`, `stepBorder`, `stepPadding`, `stepWidth`, `stepHeight`, `stepHoverBackground`, `stepHoverColor`, `numberTypography`, `numberBackground`, `numberBorder`, `numberPadding`, `numberWidth`.

### Code button (`bfbePromoUi`)
Styling only, every key in the schema file: `promoButtonBackground`, `promoButtonColor`.

### Upload drop area (`bfbeUpArea`)
Styling only, every key in the schema file: `dropBackground`, `dropOver`, `dropOverLine`, `dropBorder`, `dropPadding`, `dropShadow`, `dropDirection`, `dropAlign`, `dropJustify`, `dropTextAlign`, `dropGap`, `dropIconSize`, `dropIconColor`, `dropTitleTypography`, `dropSizeTypography`, `dropCountTypography`, `dropLines`, `fileButtonTypography`, `fileButtonBackground`, `fileButtonBorder`, `fileButtonPadding`, `fileButtonShadow`, `fileButtonHoverBackground`, `fileButtonHoverColor`, `fileButtonHoverLine`.

### Upload from a web address (`bfbeUpUrl`)
Styling only, every key in the schema file: `urlLabelTypography`, `urlSpace`, `urlBackground`, `urlBorder`, `urlFocusLine`, `urlPadding`, `urlTypography`, `urlPlaceholderColor`, `urlButtonTypography`, `urlButtonBackground`, `urlButtonBorder`, `urlButtonPadding`, `urlButtonHoverBackground`, `urlButtonHoverColor`.

### Uploaded files (`bfbeUpFiles`)
Styling only, every key in the schema file: `listTitleTypography`, `listSpace`, `listGap`, `cardBackground`, `cardBorder`, `cardPadding`, `cardShadow`, `cardGap`, `fileIconSize`, `fileIconColor`, `fileIconBackground`, `fileNameTypography`, `fileMetaTypography`, `fileNameSpace`, `fileDoneColor`, `fileFailColor`, `barHeight`, `barTrack`, `barFill`, `barDone`, `barSpace`, `actIconSize`, `actColor`, `actHoverColor`, `actBackground`, `actHoverBackground`, `actBorder`, `actPadding`, `actTypography`, `failBackground`, `failBorder`.

### Errors (`bfbeErrors`)
- `errorsOff` (checkbox) **Go to the first error instead**. No list: focus goes to the first field that fails.
- `errorsTitle` (text) **Title**: placeholder Please check these answers:; only when `errorsOff` is not set. Set the PDF's title, Your quote unless set.
Styling, in the schema file: `errorTypography`, `errorSpace`, `errorBorder`, `errorsTypography`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `free` One step at a time, click any step (default), `open` Every step open, so you can style it, `live` Working, as on the site. One step at a time, click any step (the default), Every step open, so you can style it, or Working, as on the site, where steps work and rules hide fields as the site does.
- `ddOpen` (select) **Dropdown lists**: options: `closed` Closed, as the site leaves them (default), `open` Open, so you can style them. Closed, as the site leaves them (the default), or Open, so you can style them.
- `floatPreview` (select) **Floating labels**: options: `page` As the page shows them (default), `up` Risen, so you can style them; only when `labelsAt` is `border`. With floating labels on, show them As the page shows them (the default) or Risen, so you can style them.

## What it guarantees for accessibility (do not undo)
- Enter inside a text field moves to the next step by default, and Enter on the last step sends the form. Set Enter in a field to Does nothing and Enter is ignored until the last step.
- Next checks the step's own fields, shows the error for the earliest one that fails and puts focus on it.
- Step marks are buttons, and the current one carries aria-current="step".
- The Form Progress writes the count, such as Step 2 of 4, to a polite live region on every change.
- The Form Total's amount is an output element in a polite live region, so a screen reader hears the sum change.
- The Signature Field offers a typed signature beside the drawn one, so the keyboard and assistive technology have their own way in.
- Under reduced motion steps change without sliding, the page scrolls to the form without gliding, and the total's count-up cuts to the final amount.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
