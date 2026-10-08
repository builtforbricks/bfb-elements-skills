---
name: bfbe-form
description: "Use when building a multi-step form, a quote or price calculator, a form with conditional fields, uploads or a signature, or one that pays through Stripe or fills a WooCommerce cart, with BFB Advanced Forms (`bfbe-form`) and its twelve part elements. Read before writing its settings."
---

# BFB Advanced Forms (`bfbe-form`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-form.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/form/

## What it is
A nestable form you build from field elements and step elements, with uploads and signatures, sent by Bricks' own script and actions. Rules show or hide its parts and common Bricks elements inside it, and can also require, disable or fill in a field. The server runs the rules again on every send, so an answer a rule hides is dropped. A Formula prices the answers into a live total that the server recomputes, and that total can go to Stripe Checkout or a WooCommerce cart line.

**Not for:** Not for taking card details on your own page: payment happens on Stripe's own Checkout page. Uploads, signatures, steps, totals and other repeaters cannot sit inside a Repeater's rows, which suit rows of simple fields.

**Costs a page:** CSS 2.57 KB, JS 3.06 KB (gzipped), no dependencies, loaded only on pages that use it. Only where used, the steps engine: JS 3.00 KB. Only where used, the checks and their words: CSS 0.34 KB, JS 2.63 KB. Only where used, the formula: JS 1.00 KB. Only where used, a warning before leaving: JS 0.39 KB. Only where used, values from rules and the address: JS 0.94 KB. Only where used, the pricing: JS 2.59 KB. Only where used, the pricing rules: JS 1.37 KB. Only where used, floating labels: CSS 0.81 KB, JS 1.33 KB.

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
- `emailSubject` (text) **Subject**: default `Contact form request`
- `emailTo` (select) **Send to email address**: options: `admin_email` Admin email (admin@example.com) (default), `custom` Custom email address
- `emailToCustom` (text) **Send to custom email address**: only when `emailTo` is `custom`. Accepts multiple addresses separated by comma.
- `emailRoutes` (repeater) **Send to, by answer**: placeholder Recipients. Add rows that send the email to more addresses when an answer holds. Each row has Field key, Test, Value and Send to, and every row that holds adds its addresses.
- `emailRoutesKeep` (checkbox) **Keep the usual recipients too**: only when `emailRoutes` is set. Off by default, so a row that holds replaces the usual recipients. Tick it to send to both.
- `emailBcc` (text) **BCC email address**
- `fromEmail` (text) **From email address**
- `fromName` (text) **From name**: default `bfb-elements`. Default: Site title.
- `replyToEmail` (text) **Reply to email address**: placeholder Name. Comma-separated list of name and email address or email addresses only. Default: Email address in submitted form.
- `emailContent` (textarea) **Email content**. Use field IDs to personalize your message. Type {{all_fields}} to output all the field labels and values of the submitted form. Learn more (https://academy.bricksbuilder.io/article/form-element/#email).
- `emailErrorMessage` (text) **Error message**: default `Submission failed. Please reload the page and try to submit the form again.`
- `htmlEmail` (checkbox) **HTML email**: default `true`

### Webhook (`webhook`)
The whole group shows only when `actions` is `webhook`.
- `webhooks` (repeater) **Endpoints**: placeholder Endpoint. Bricks' own list of addresses each submission goes to, each with its Name, Endpoint URL, Data format, Data and Headers. BFB Elements adds the four settings below to every endpoint.
- `webhookMaxSize` (number) **Max payload size (KB)**: placeholder 1024. Maximum size of the webhook payload in kilobytes. (Default: 1024).
- `webhookRateLimit` (checkbox) **Rate limiting**. Limit the number of webhook requests that can be sent per hour.
- `webhookRateLimitRequests` (number) **Max requests per hour**: placeholder 60; only when `webhookRateLimit` is `1`. Maximum number of webhook requests allowed per hour. (Default: 60).
- `webhookErrorIgnore` (checkbox) **Continue on error**. If enabled, form submission will succeed even if the webhook fails. Errors will be logged to the server error log.
- `webhookErrorMessage` (text) **Error message**: only when `webhookErrorIgnore` is not set

### Confirmation email (`confirmation`)
The whole group shows only when `actions` is `email`.
- `confirmationEmailSubject` (text) **Subject**
- `confirmationEmailTo` (text) **Send to email address**. Default: Email address in submitted form.
- `confirmationFromEmail` (text) **From email address**. Default: Admin email.
- `confirmationFromName` (text) **From name**. Default: Site title.
- `confirmationReplyToEmail` (text) **Reply to email address**: placeholder Name. Comma-separated list of name and email address or email addresses only. Default: From email address.
- `confirmationEmailContent` (textarea) **Email content**. Use field IDs to personalize your message. Type {{all_fields}} to output all the field labels and values of the submitted form. Learn more (https://academy.bricksbuilder.io/article/form-element/#email).
- `confirmationEmailHTML` (checkbox) **HTML email**

### Redirect (`redirect`)
The whole group shows only when `actions` is `redirect`.
- `redirectAdminUrl` (checkbox) **Redirect to admin area**: placeholder https://example.com/wp-admin/
- `redirect` (text) **Custom redirect URL**: placeholder https://example.com
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
- `mailchimpErrorMessage` (text) **Error message**: default `Sorry, but we could not subscribe you.`; only when `apiKeyMailchimp` is set

### Sendgrid (`sendgrid`)
The whole group shows only when `actions` is `sendgrid`.
- `sendgridList` (select) **List**: options: ; only when `apiKeySendgrid` is set
- `sendgridEmail` (select) **Field: Email**: options: ; only when `apiKeySendgrid` is set
- `sendgridFirstName` (select) **Field: First name**: options: ; only when `apiKeySendgrid` is set
- `sendgridLastName` (select) **Field: Last name**: options: ; only when `apiKeySendgrid` is set
- `sendgridErrorMessage` (text) **Error message**: default `Sorry, but we could not subscribe you.`; only when `apiKeySendgrid` is set

### User Login (`login`)
The whole group shows only when `actions` is `login`.
- `loginName` (select) **Field: Login**: options: 
- `loginPassword` (select) **Field: Password**: options: 
- `loginRemember` (select) **Field: Remember me**: options: 
- `loginErrorMessage` (text) **Error message**. Enter a generic error message. Otherwise the reason why the login failed is displayed.

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
- `createPostErrorMessage` (text) **Error message**: only when `createPostType` is set and `createPostDisableCapabilityCheck` is not set
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
- `updatePostErrorMessage` (text) **Error message**
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
- `submissionFormName` (text) **Form name**: placeholder Contact form. Descriptive name for viewing submissions on the "Form Submissions" page.
- `submissionSaveIp` (checkbox) **Save IP address**
- `submissionMaxEntries` (number) **Max. entries**. Set maximum number of form submissions that you want to store in the database.
- `submissionMaxEntriesErrorMessage` (text) **Error message**: placeholder Maximum number of entries reached.
- `submissionDupEntries` (repeater) **Compare with (Field ID)**
- `submissionDupEntriesErrorMessage` (text) **Error message**: placeholder Duplicate entries not allowed.

### Unlock password protection (`unlock-password-protection`)
The whole group shows only when `actions` is `unlock-password-protection`.
- `passwordProtectionPassword` (select) **Field: Password**: options: . If no form field is selected, the first password field in the form is used.
- `passwordProtectionErrorMessage` (text) **Error message**

### Update the user (`bfbeUser`)
The whole group shows only when `actions` is `bfbe-user`.
- `userRows` (repeater) **Fields to change**. Add one row per field of the logged-in visitor's profile. Each has Change (First name, Last name, Nickname, Name shown, Website, About or A custom field), Field name, How, From the answer, By and Kept by. It never changes a role, a password or an email address.
- `userRefused` (text) **When not logged in**: placeholder Please log in first.. Type the words a visitor who is not logged in sees, Please log in first. unless set.

### Update post fields (`bfbeMeta`)
The whole group shows only when `actions` is `bfbe-meta`.
- `metaPost` (select) **Which post**: options: `current` The page it is on (default), `field` The post an answer names, `url` The post the address names. Pick The page it is on (the default), The post an answer names, or The post the address names. For the last two, Its key names the answer or the address parameter that holds the post's ID.
- `metaPostKey` (text) **Its key**: placeholder post_id; only when `metaPost` is `field` or `url`. The answer or the address parameter that holds its ID.
- `metaWho` (select) **Who may**: options: `editors` Who can edit the post (default), `anyone` Anyone, to count. Who can edit the post (the default), or Anyone, to count, which lets any visitor add or take away a fixed amount on a post the public can see, and nothing more.
- `metaRows` (repeater) **Fields to change**. Add one row per custom field, with Field name, How, From the answer, By and Kept by. How sets it to the answer, adds to it or takes from it, adds the answer to a list or takes it out, or saves a repeater's rows.
- `metaRefused` (text) **When not allowed**: placeholder You cannot change this.. Type the words shown when the change is refused, You cannot change this. unless set.

### Delete the post (`bfbeDelete`)
The whole group shows only when `actions` is `bfbe-delete`.
- `deletePost` (select) **Which post**: options: `current` The page it is on (default), `field` The post an answer names, `url` The post the address names. Pick The page it is on (the default), The post an answer names, or The post the address names, whose ID Its key holds.
- `deletePostKey` (text) **Its key**: placeholder post_id; only when `deletePost` is `field` or `url`. The answer or the address parameter that holds its ID.
- `deleteWho` (select) **Who may**: options: `author` Its author (default), `deleters` Anyone who may delete it. Its author (the default) or Anyone who may delete it. Either way the visitor must be logged in and allowed by WordPress.
- `deleteHow` (select) **How**: options: `trash` Into the bin (default), `delete` For good. Move the post Into the bin (the default) or delete it For good.
- `deleteTypes` (text) **Only these post types**: placeholder post, listing. List post types, with commas between them, to limit which posts the form may delete.
- `deleteRefused` (text) **When not allowed**: placeholder You cannot delete this.. Type the words shown when the delete is refused, You cannot delete this. unless set.

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
- `errorsTitle` (text) **Title**: placeholder Please check these answers:; only when `errorsOff` is not set. Type the heading over that list, Please check these answers: unless set.
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

## Rendered DOM

A sending form is a real `<form method="post">` wearing Bricks' own `brxe-form` class and `data-element-id`, so Bricks'
script sends it and Bricks' handler runs the actions. With **Nothing is sent** `quiet: true` the root is a `<div>` with
`bfbe-form--quiet`: Send is hidden and the Total's hidden input is not drawn. Pattern 1 below, trimmed:

```html
<form id="brxe-abc123" class="brxe-bfbe-form bfbe-form bfbe-pc brxe-form bfbe-pc--steps bfbe-pc--total-right" method="post"
      data-element-id="abc123" data-bfbe-steps="4" data-bfbe-motion="slide" data-bfbe-form="{…}" data-bfbe-pc="{…}"
      data-bfbe-side-stack="768" style="--bfbe-pc-rows:3;--bfbe-pc-side:320px">
  <div class="brxe-bfbe-form-progress bfbe-pc__progress bfbe-pc--marks-titles" data-bfbe-progress="1">
    <p class="bfbe-pc__count" aria-live="polite"></p>
    <div class="bfbe-pc__rail"><ol class="bfbe-pc__marks"><li class="bfbe-pc__mark is-current"><button type="button" class="bfbe-pc__mark-btn" aria-current="step">…</button></li>…</ol>
      <div class="bfbe-pc__bar" role="progressbar" aria-valuenow="1" aria-valuemax="4"><span class="bfbe-pc__bar-fill"></span></div></div>
  </div>
  <div class="brxe-bfbe-form-step bfbe-pc__panel" data-bfbe-panel="0" data-bfbe-step="Plan" aria-label="Plan">
    <div class="brxe-bfbe-form-choice form-group bfbe-pc__field bfbe-pc__field--radio bfbe-pc__field--segments" data-bfbe-key="plan">
      <div class="form-group-error-message"></div><div class="label bfbe-pc__label">Plan</div>
      <span class="bfbe-pc__opts bfbe-pc__opts--segments" role="radiogroup"><label class="bfbe-pc__opt"><input type="radio"
        class="bfbe-pc__value bfbe-pc__box" name="form-field-plan[]" value="Starter" data-bfbe-amount="9">…</label>…</span>
    </div>
  </div>
  <div class="brxe-bfbe-form-step bfbe-pc__panel" data-bfbe-panel="1" hidden>…</div>
  <div class="brxe-bfbe-form-total bfbe-pc__total" data-bfbe-total-box="total" data-bfbe-rule="{…}">
    <div class="bfbe-pc__total-head"><span class="bfbe-pc__total-label">Your plan</span><span class="bfbe-pc__figure"><output
      class="bfbe-pc__amount" aria-live="polite">$0</output><span class="bfbe-pc__suffix"></span></span></div>
    <dl class="bfbe-pc__lines"></dl><input type="hidden" name="form-field-total" data-bfbe-total="total">
  </div>
  <div class="brxe-bfbe-form-button form-group bfbe-pc__nav bfbe-pc__nav--nav submit-button-wrapper">
    <button type="button" class="bfbe-pc__back" hidden>…</button><button type="button" class="bfbe-pc__next">…</button>
    <button type="submit" class="bricks-button bfbe-pc__send">…</button></div>
  <div class="bfbe-pc__errors" hidden></div>
</form>
```

- **Fields.** Each is `.form-group.bfbe-pc__field.bfbe-pc__field--<type>` with `data-bfbe-key`: an empty
  `.form-group-error-message` first (Bricks writes the error into it), the label (`label.bfbe-pc__label`, or
  `div.label.bfbe-pc__label` over a set), the control, then `span.bfbe-pc__note`. Boxes are `.bfbe-pc__input`, ticks and
  radios `.bfbe-pc__box`. Inputs are named `form-field-<key>` (`[]` for a set; `form-field-<repeater>[<row>][<key>]` in a
  repeater row).
- **Rules.** An element with a rule carries `data-bfbe-rule` (`{"a":"show","m":"all","r":[["plan","is","Business"]]}`).
  Hidden by it: `data-bfbe-off`, `.bfbe-pc__off`, inline `display: none`, its inputs disabled. Required by it:
  `data-bfbe-required`. Held by a Block rule: `data-bfbe-block` and a `p.bfbe-pc__block` with the rule's words.
- **Steps.** One `.bfbe-pc__panel` shows; the others get `hidden` and inline `display: none`. Marks take `is-current` and
  `is-done`, the Progress root `--bfbe-pc-progress` (the share reached, up to 1). The form toggles `bfbe-fs--first`, `bfbe-fs--last` and, after
  a successful send, `bfbe-fs--done`; a step coming in gets `bfbe-fs__in` and `data-bfbe-dir="next"` or `"back"`.
- **Summary and Total.** `div.bfbe-sum` stays empty until its step shows, then holds `.bfbe-sum__step` blocks of
  `.bfbe-sum__row` (`dt`, `dd`) and a `button.bfbe-sum__change`. The Total's amount and `.bfbe-pc__line` rows are written
  by script, in `.bfbe-pc__total-head`, `.bfbe-pc__lines`, `.bfbe-pc__total-details` and `.bfbe-pc__total-foot`.
- **Events** on the form element: `bfbe/pc` (detail: the price state, also at `form.bfbePcState`), `bfbe/step` (detail
  `{at, of, focus}`) and `bfbe/rules`. Bricks' own `bricks/form/success` and `bricks/form/error` fire on `document`.
- **Where styling writes.** The form's field groups (Label and note, Input, Slider, Choices styling, Tick box, Switch,
  Dropdown, Stepper, Number arrows, Calendar, the three upload groups, Errors) are defaults for every field inside; the
  same key set on one field wins there. `fieldGap` is `--bfbe-pc-gap` on the root, a flex column; `innerGap` is
  `--bfbe-pc-field-gap`, `errorBorder` `--bfbe-pc-error`, `accent` `--bfbe-pc-accent`.
- **Fetched HTML is not the page.** The server draws every field and the first step; rules, steps, prices and the Summary
  act once the scripts run. Read their states in a browser.

## Wiring to other elements

The form and its parts find each other by **key** and by their place in the tree, never by element id. To target one form
in CSS or a script, give it a class in `_cssClasses`, never `_cssId`: component instances share ids.

**The tree.**
- `bfbe-form` holds the seven fields, the five parts and any Bricks element between them. Fields count at any depth, so a
  `block`, `div` or `container` (in the form or in a Step) lays them out.
- A stepped form: `bfbe-form-progress`, then two or more `bfbe-form-step` holding the fields, the `bfbe-form-summary` in the
  last Step, then `bfbe-form-total` and one `bfbe-form-button` with `kind: "nav"` directly in the form. A Button inside a
  Step hides with it. With `stepsHash` the address takes `#<element id>-<n>`.

**Keys.**
- A field's **Key** `key` names its answer in rules, formulas, `{{key}}` in Bricks' email subject and content, the saved
  entry, the webhook payload and `{bfbe_answer:key}`. Lowercase letters, digits and underscores.
- The Total's own `key` is `total` unless set; **Send the choices too** `sendChoices` adds `total_choices`, the choices
  in words. Both are keys like a field's.
- Bricks' field dropdowns (`createPostTitle`, `mailchimpEmail`, `loginName`, `registrationEmail` and the rest) take a
  key as their value. The save writes the form's `fields` list, which those dropdowns and the entries screen read.

**Rules: Shown when.**
- Keys: `ruleAction`, `ruleMatch` (`all` unless `any`) and `rules`, rows of `{"field", "op", "value"}`. Text, Choice, Number
  and Date offer `show`, `hide`, `require`, `disable`, `set` (with `ruleValue`); Upload and Signature the first four; Step
  and Button `show`, `hide`, `block` (with `ruleMessage`); Progress, Summary, Total and Repeater `show` and `hide`.
- Bricks' own `container`, `block`, `div`, `heading`, `text-basic`, `text`, `image`, `icon`, `icon-box`, `divider`,
  `button`, `list` and `video` take `ruleAction` (`show`, `hide`) and `rules` too, and act only inside a BFB form.
- `field` is a key, `total` (the running total), `step` (the step shown, counted from 1), `url:ref` (the address's
  `?ref=`) or `saved:name` (a value the site keeps in the browser's localStorage).
- `op`: `is`, `not`, `in` (`"a, b"`), `contains`, `starts`, `ends`, `gt`, `gte`, `lt`, `lte`, `between` (`"10, 20"`),
  `filled`, `empty`, `ticked`, `unticked`, `matches` (a pattern on the whole value), `before` and `after` (`2026-12-25`,
  the site's date format, or `today`), `same` (`value` names another key). Words compare without case, numbers as numbers.
- `set` gives `ruleValue` while the conditions match (`"a, b"` ticks two) and takes it back after, unless the visitor
  changed it. `block` stops Next, Enter, a later mark and Send with `ruleMessage`, and the server refuses with the same words.
- A field's **Fill from the address** `fromUrl` fills it from that parameter: `plan` reads `?plan=`.

**Pricing and the Formula.**
- With **Formula** `formula` empty, the total is **Starting amount** `base` plus every field's own price: a choice's
  `amount`, a number times its **Adds** `price`, a ticked box's `price`, a `fixed` number's `price`, each times **Multiply
  by** `times` (another key) and banded by **Rates by quantity** `tiers`. With a formula, it is the formula plus `base`.
- In a formula a number or slider is its number, `fixed` its `price`, a dropdown or `radio` the chosen `amount`, `multi` the
  ticked amounts added, a tick box or consent box 1 or 0, a `period` its multiplier. Text, dates, uploads, signatures, the
  repeater, a range, a rating and anything a rule hides are 0.
- Grammar: numbers and keys, `+ - * / %`, brackets, `< > <= >= == !=` (1 or 0), `test ? this : that`, `min(a, b)`,
  `max(a, b)`, `pow(a, b)`, `round`, `ceil`, `floor`, `abs` and `sqrt` of one value, and `sum(extra_*)`, every key that
  starts `extra_` added. `;` separates statements, `name = expression` keeps a result for the ones after, and the last is
  the total: `stay = nights * 90; stay + sum(extra_*) * 10`. An unknown key is 0; dividing by zero gives 0.
- Then, in order: a promo code's discount, times the billing period, **Never below** `least`, **Tax (%)** `taxRate`
  (`taxIn: "added"` or `"included"`), **Round to** `roundTo`, and **Above this amount** `over`, which shows **Say
  instead** `overText` and charges nothing. `currency`, `currencyAt`, `decimals`, `thousands` and `decimalMark` only write
  the prices. Formula guide: https://builtforbricks.com/bfb-elements/docs/form/#formula

**The parts and the settings a build depends on.** Each schema is `../bfbe-schemas/references/elements/<name>.json`.
- `bfbe-form-text`: `type` `text` (default), `email`, `tel`, `url`, `password`, `textarea`, `richtext`, `color`, `hidden`
  (its **Starts with** `value`), `promo` (`codes` rows `{code, off, percent, note}`, checked on the server) or `section` (a
  heading, no key). Checks: `required`, `minLength`, `maxLength`, `pattern`, `sameAs` (another key), `telCountry`, and
  `mask` (`card`, `date`, `time`, `phone`, or `custom` with **Its shape** `maskPattern`: `9` a digit, `a` a letter, `*` either).
- Words per check: `msgRequired`, `msgFormat`, `msgLength`, `msgPattern`, `msgMatch` (and `msgRange` on a number), else
  **Error message** `errorMessage`. A missed pattern or mask says `msgPattern`, else `errorMessage`, else "Not in the
  expected form.", on the page and from the server alike. <!-- src: plugins/bfb-elements-pro/elements/form-text.php:247-255 -->
- `bfbe-form-choice`: `type` `select` (default), `radio`, `multi`, `checkbox`, `consent`, `period`, `rememberme` or
  `rating`. Choices are `options` rows `{label, value, amount, note, badge, was, icon, width, group, image, swatch}` or come
  from `source` (`json`, `dynamic`, `posts`, `terms`, `countries`, `acf`); a billing period's are `periods` rows, `amount`
  multiplying the total and `note` following it (`"/month"`). `show` (`plain`, `segments`, `cards`, `pills`, `swatches`,
  `images`, `content`) suits `radio`, `multi` and `period`; `content` takes one child element per choice, in order.
- More Choice keys: a single tick box prices with `price`; **Go on when chosen** `advance` (`radio`, `rating`) moves to
  the next step; `noPreselect` leaves a `radio` empty; `ddSearch` and `ddMulti` shape a dropdown.
- `bfbe-form-number`: `type` `number` (default), `slider`, `range` (two handles, both ends in one answer) or `fixed` (adds
  `price`, not shown). `min`, `max`, `step`, `start`, `startEmpty`, `unit`; `price` per unit, `times`, `was`, and `tiers`
  rows `{upTo, rate}` with `tiersMode` `stepped` or `graduated`.
- `bfbe-form-date`: `type` `date`, `time`, `datetime` or `daterange`; `minDate` (`today` or `2027-01-31`), `maxDate`,
  `closedDates` (a date or `2026-12-31 to 2027-01-02` a line), `weekends: "closed"`, `minFrom` (another date's key) with
  `minFromDays`, `minTime`, `maxTime`. `calendar: "browser"` cannot grey out shut days (sending still refuses them); a span
  is always the styled calendar. Answers arrive in the site's date format. <!-- src: plugins/bfb-elements-pro/elements/form-date.php:60-63 -->
- `bfbe-form-upload`: `type` `file` (default), `image` or `gallery`; `fileUploadLimit` (count), `fileUploadSize` (MB each,
  2 unless set, 50 at most), `fileUploadAllowedTypes` (`"pdf, jpg"`), `fileUploadStorage` (`attachment` or `directory`),
  `urlUpload` (a web address too), `previews`.
- `bfbe-form-signature`: `label`, `key`, `required`, `toolsPlace` (`under`, `footer`). A drawing is sent as a link to a PNG
  under `uploads/bfbe-signatures/`, a typed name marked "(typed)".
- `bfbe-form-repeater`: its children are one row of Text, Choice, Number or Date fields, keyed within the row. `rowTitle`
  (`%d` the row number), `rowsLeast` (1), `rowsMost` (10), `rowsStart`; `rowsFrom`, `rowsFromName` and `rowsOf` start it
  from saved rows. `_flexDirection: "row"` on the repeater puts a row's fields side by side.
- `bfbe-form-step`: `title`, `text`, `heading` (`title` or `both`, drawn above its fields). `bfbe-form-progress`:
  `stepsMarks` `full`, `titles` (with descriptions), `numbers`, `bar` or `none`; `markClick` `behind`, `any`, `none`; `countShow`.
- `bfbe-form-summary`: `byStep: "flat"` for one list, `skipEmpty`, `empty`, `change`, `sumLines`. A password reads as dots,
  a drawn signature as "Signed", a lone tick box as "Yes".
- `bfbe-form-total`: `totalLabel`, `breakdown`, `countUp`, `countLine` (`%d` the ticked boxes), `equivalents`, `terms` (a
  tick box its buttons wait for), `ctaText` with `ctaLink` and `ctaCarry` (`bfbe_total` and `bfbe_choices` in the link);
  `position` `flow`, `sticky`, `right`, `left` or `bar`, with `sideWidth`, `sideGap`, `sideStack`, `stickyTop`.
- `bfbe-form-button`: `kind` `nav` (Back, Next and Send; default), `send`, `next`, `back` or `save`; `navPlace` or `place`;
  `sayMissing` lists the required fields still empty under Send; `nextText`, `sendText`, `backText`, `backStyle: "text"`.

**Sending.**
- `actions` is an array of Bricks' own (`email`, `webhook`, `redirect`, `save-submission`, `create-post`, `login` and the
  rest, each with Bricks' own keys) and the pack's `bfbe-user`, `bfbe-meta`, `bfbe-delete`, `bfbe-pdf` and `bfbe-pay`.
  `save-submission`, which Bricks offers once its setting Save form submissions in database is on, always runs first.
  <!-- src: plugins/bfb-elements-pro/includes/class-form-engine.php:1714-1717 -->
- Email: `emailTo: "custom"` with `emailToCustom`, and `{{key}}` or `{{all_fields}}` in `emailSubject` and `emailContent`.
  **Send to, by answer** `emailRoutes` rows `{field, op, value, to}` use the rules' tests; every row that holds adds its
  addresses, which replace the usual recipients unless `emailRoutesKeep`.
- Webhook: each `webhooks` row is Bricks' (`name`, `url`, `contentType`, `dataTemplate`, `headers`) plus `method` (`POST`
  unless set), `secret`, `loggedIn` and `debug` (the reply shown to administrators); a row with another method, a secret or
  `debug` refuses addresses inside the site's own network. With `secret`, `X-BFB-Signature: sha256=<hex>` is the HMAC-SHA256 of
  `X-BFB-Timestamp`, a dot and the raw body (`GET`: the query): https://builtforbricks.com/bfb-elements/docs/form/#signed-webhooks
- `bfbe-pdf` (Quote PDF): the answers and the server's sum, linked under the message (`pdfLink`) and kept `pdfDays` (7, up
  to 90). `pdfAttach` attaches it only when `email` is in `actions` too.
- `bfbe-pay` (Pay with Stripe): Checkout for the server's total in `payCurrency`, after every other action; the visitor
  returns with `?bfbe_paid=1` unless `paySuccess`. Keys: BFB Elements, Settings, Stripe payments, or `BFBE_STRIPE_SECRET_KEY` and
  `BFBE_STRIPE_WEBHOOK_SECRET` in `wp-config.php` (https://builtforbricks.com/bfb-elements/docs/form/#stripe). Stripe's
  webhook turns the Payment answer "Waiting, REF" into "Paid, …" only on an entry Save submission kept. <!-- src: plugins/bfb-elements-pro/includes/class-form-pay.php:188, :383-399 -->
- WooCommerce cart: on the Total, `wooOn` and `wooProduct` (a product id), offered only where WooCommerce is active. The
  line is priced on the server from the choices, in the store's currency, and refused above `over` or below zero.
- `bfbe-user`, `bfbe-meta` and `bfbe-delete` change the visitor's profile (`userRows`), a post's fields (`metaRows`) or
  delete a post (`deletePost`, `deleteHow`). **Save for later** is a Button with `kind: "save"`, emailing a link back (`saveDays`, 30).
- A form on a draft or private page refuses to send unless the visitor may edit that page.
  <!-- src: plugins/bfb-elements-pro/includes/class-form-engine.php:133-136 -->

**What the server never trusts.** It runs the rules again and drops what they hide, checks every choice against the saved
options, prices the answers itself and writes its own total, and takes labels, required fields, Set values, Block rules,
ranges, repeater rows, signatures, phone codes, shut dates and upload counts and sizes from the saved form. A dynamic tag
typed into an answer is made inert before Bricks renders the email.

**Outside the form.** `{bfbe_answer:key}` shows an answer live anywhere on the page, `{bfbe_answer:total}` the total, and
`{bfbe_answer:key:<form element id>}` picks the form when a page has two; `@fallback:'friend'` shows until there is an
answer. For steps or styled fields on Bricks' own `form` element, see the skills `bfbe-form-steps` and `bfbe-form-fields`.

## Verified patterns

**A priced form in four steps.** From the fixture page `fixture-form` ("PRO: BFB Form", its Plan form), with the saved
`fields` copy left out. Progress on top, the Summary on the last step, the Total beside the fields, one `nav` Button after
the steps. SSO seats show for Business, the Add-ons step hides for Starter, and `times: "seats"` prices the plan per seat.

```json
{"name": "bfbe-form", "settings": {"actions": ["save-submission"], "successMessage": "Sent, thank you.", "currency": "$", "decimals": 2, "stepsHash": true}, "children": [
  {"name": "bfbe-form-progress", "settings": {"stepsMarks": "titles", "marksJustify": "space-between", "countShow": true}},
  {"name": "bfbe-form-step", "settings": {"title": "Plan", "text": "Pick the one that fits the team today.", "heading": "both"}, "children": [
    {"name": "bfbe-form-choice", "settings": {"label": "Plan", "key": "plan", "type": "radio", "show": "segments", "times": "seats", "priceOn": true, "options": [
      {"label": "Starter", "amount": "9", "note": "For one team"}, {"label": "Team", "amount": "19", "note": "Shared boards", "badge": "Most picked"},
      {"label": "Business", "amount": "39", "note": "SSO and audit log"}]}},
    {"name": "bfbe-form-number", "settings": {"label": "Seats for SSO", "key": "sso_seats", "type": "number", "min": 0, "max": 500, "start": 0, "price": 2,
      "ruleAction": "show", "rules": [{"field": "plan", "op": "is", "value": "Business"}]}}]},
  {"name": "bfbe-form-step", "settings": {"title": "Team", "text": "Seats and how you pay."}, "children": [
    {"name": "bfbe-form-number", "settings": {"label": "Seats", "key": "seats", "type": "slider", "min": 1, "max": 200, "step": 1, "start": 12, "ticks": 3, "bubble": true, "box": true}},
    {"name": "bfbe-form-choice", "settings": {"label": "Billing", "key": "cycle", "type": "period", "show": "segments", "periods": [
      {"label": "Monthly", "amount": "1", "note": "/month"}, {"label": "Yearly", "amount": "10", "note": "/year", "badge": "Two months free"}]}},
    {"name": "bfbe-form-choice", "settings": {"label": "Priority support", "key": "support", "type": "checkbox", "showBox": "row", "price": 49, "priceOn": true, "pricePrefix": "+", "on": true}}]},
  {"name": "bfbe-form-step", "settings": {"title": "Add-ons", "ruleAction": "hide", "rules": [{"field": "plan", "op": "is", "value": "Starter"}]}, "children": [
    {"name": "bfbe-form-choice", "settings": {"label": "Extras", "key": "extras", "type": "multi", "show": "cards", "priceOn": true, "options": [
      {"label": "Extra storage", "amount": "8", "note": "1 TB more", "icon": "ti-cloud"},
      {"label": "Onboarding call", "amount": "120", "note": "One hour", "badge": "New", "was": "150", "icon": "ti-headphone"}]}},
    {"name": "bfbe-form-text", "settings": {"label": "Promo code", "key": "promo", "type": "promo", "codes": [
      {"code": "WELCOME", "off": "10", "percent": true, "note": "10% off"}, {"code": "CLUB50", "off": "50", "note": "50 off"}]}}]},
  {"name": "bfbe-form-step", "settings": {"title": "Send it"}, "children": [
    {"name": "bfbe-form-text", "settings": {"label": "Your name", "key": "name", "type": "text", "required": true}},
    {"name": "bfbe-form-text", "settings": {"label": "Email", "key": "email", "type": "email", "required": true}},
    {"name": "bfbe-form-summary", "settings": {"sumLines": true}}]},
  {"name": "bfbe-form-total", "settings": {"totalLabel": "Your plan", "breakdown": true, "position": "right", "sideWidth": "320px", "sideGap": "48px",
    "sendChoices": true, "countLine": "%d extras selected", "ruleAction": "hide", "rules": [{"field": "plan", "op": "empty", "value": ""}]}},
  {"name": "bfbe-form-button", "settings": {"kind": "nav", "nextText": "Continue", "backStyle": "text"}}
]}
```

**A contact form that emails by answer.** From `fixture-form-actions` ("PRO: BFB Form, phase 3", its Routing form), the
test subject left out. Sales and Support go to their own addresses, a budget of 5000 or more adds a third, and anything no
row matches goes to `emailToCustom`. Put `{{name}}` in `emailSubject` or `emailContent` to quote an answer.

```json
{"name": "bfbe-form", "settings": {"actions": ["email"], "emailTo": "custom", "emailToCustom": "office@example.com", "successMessage": "Sent, thank you.", "emailRoutes": [
    {"field": "topic", "op": "is", "value": "Sales", "to": "sales@example.com"},
    {"field": "topic", "op": "is", "value": "Support", "to": "help@example.com, desk@example.com"},
    {"field": "budget", "op": "gte", "value": "5000", "to": "boss@example.com"}]}, "children": [
  {"name": "bfbe-form-text", "settings": {"label": "Name", "key": "name", "type": "text", "required": true}},
  {"name": "bfbe-form-choice", "settings": {"label": "Topic", "key": "topic", "type": "radio", "options": [{"label": "Sales"}, {"label": "Support"}, {"label": "Billing"}]}},
  {"name": "bfbe-form-number", "settings": {"label": "Budget", "key": "budget", "type": "number", "min": 0, "max": 100000, "start": 0}},
  {"name": "bfbe-form-button", "settings": {"kind": "send"}}
]}
```

**A form that pays.** From `fixture-form-actions` (its Pay with Stripe form). Save submission keeps the entry whose
Payment answer Stripe's webhook updates; the Total shows what Stripe will charge, worked out again on the server. It needs
the Stripe keys on the site: without them the send answers that payment is not available.

```json
{"name": "bfbe-form", "settings": {"actions": ["save-submission", "bfbe-pay"], "currency": "€", "successMessage": "Taking you to the payment page.", "payName": "Ridgeline plan", "payCurrency": "EUR"}, "children": [
  {"name": "bfbe-form-text", "settings": {"label": "Name", "key": "name", "type": "text"}},
  {"name": "bfbe-form-text", "settings": {"label": "Email", "key": "email", "type": "email"}},
  {"name": "bfbe-form-choice", "settings": {"label": "Plan", "key": "plan", "type": "radio", "options": [{"label": "Starter", "amount": "9"}, {"label": "Team", "amount": "19"}, {"label": "Business", "amount": "39"}]}},
  {"name": "bfbe-form-choice", "settings": {"label": "Extras", "key": "extras", "type": "multi", "options": [{"label": "Priority support", "amount": "5"}, {"label": "Training", "amount": "12"}]}},
  {"name": "bfbe-form-total", "settings": {"totalLabel": "To pay"}},
  {"name": "bfbe-form-button", "settings": {"kind": "send"}}
]}
```

## Gotchas

- **Keys decide everything, so set them.** The save makes a missing key from the label, gives a repeated key `_2`, and
  never lets a field take `total` or `step` (a field keyed `total` becomes `total_2`). A formula is case-sensitive: `Rooms`
  is not `rooms` and counts 0. <!-- src: plugins/bfb-elements-pro/includes/class-form-engine.php:1788-1805, docs/elements/form.md "Formulas" -->
- **To a rule, a tick box answers `on` and a choice its value.** Test a single tick box with `ticked` or `unticked`, never
  `is`. A choice compares its `value`, else its `label`, without case, so renaming a label with no `value` breaks its rules.
  <!-- src: src/elements/form/form.js:117-124, plugins/bfb-elements-pro/includes/class-form-engine.php:659, :734-736 -->
- **A Formula replaces the fields' own prices.** Once `formula` is set, Adds, `times` and `tiers` count only through the
  keys it names: a number's key is its number, not number times Adds. `sum()` takes one starred prefix; `sum(a, b)` gives `b`.
  <!-- src: plugins/bfb-elements-pro/includes/class-price-calculator-pricing.php:327-335, :527-538, :582-583 -->
- **Hidden by a rule is gone.** Its inputs are disabled, so they neither post nor count as required, the formula reads 0,
  and the server drops the answer even when one is sent. A hidden Step is skipped and its mark goes with it.
  <!-- src: src/elements/form/form.js:177-183, plugins/bfb-elements-pro/includes/class-form-engine.php:169-182 -->
- **Steps work from two up.** With one Step or none every field shows, Next and Back hide, and Summary stays empty; with two
  or more, Send shows on the last step only. The Summary fills when its step shows and lists the other steps' answers.
  <!-- src: src/elements/form-wizard/form-wizard.js:119-122, :216-230, src/elements/form-summary/form-summary.js:53 -->
- **The Total stands beside the fields only as a direct child.** `position: "right"` or `"left"` makes the form a grid of
  its direct children, read from the first Total alone, and stacks below `sideStack` (768 unless set) of the window width.
  <!-- src: src/elements/form-total/form-total.css:65-85, plugins/bfb-elements-pro/elements/form.php:1197-1204 -->
- **Nothing is sent means nothing.** `quiet: true` hides Send, runs no action and draws no hidden total, so
  `{bfbe_answer:total}` keeps its fallback; the Total element itself still counts.
  <!-- src: plugins/bfb-elements-pro/elements/form.php:1129-1131, plugins/bfb-elements-pro/elements/form-total.php:340, src/elements/form-live/form-live.js:24 -->
- **A Number Field is 0 to 10 unless set.** `min` 0, `max` 10 and `step` 1 stand when unset, and the server refuses a
  number outside them or off the step. The box starts at `start`, else `min`, so Required holds until the visitor clears
  it; `startEmpty` starts it blank. <!-- src: plugins/bfb-elements-pro/includes/class-form-engine.php:1393-1408, plugins/bfb-elements-pro/elements/form-number.php:244-273, docs/elements/form.md "Round 446" -->
- **A Repeater row holds four kinds of field.** Text, Choice, Number and Date fields only; an upload, signature, step,
  total or repeater inside it is left out. Rows carry no rules or prices of their own and arrive as one answer, a line a row.
  <!-- src: plugins/bfb-elements-pro/includes/class-form-engine.php:514-538, plugins/bfb-elements-pro/elements/form-repeater.php:14-15 -->
- **Uploads go up when chosen.** A file waits 12 hours for its form, and with **Keep the file** `fileUploadStorage` unset
  it serves the send only. `type: "image"` or `"gallery"` draws nothing for a visitor who may not upload files.
  <!-- src: plugins/bfb-elements-pro/includes/class-form-uploads.php:17, plugins/bfb-elements-pro/elements/form-upload.php:73, :280-289 -->
- **A setting the panel hides does nothing.** The page and the server drop it alike, and a changed `type` keeps the old
  type's keys: a `telCountry` left from a phone hides `mask`, so the mask never runs.
  <!-- src: plugins/bfb-elements-pro/includes/class-form-engine.php:986-987, docs/elements/form.md "Known limits" -->
- **The builder canvas is not the page.** **Show it** `builderView` is `free` unless set: one step at a time, any step
  reachable, and Next never checks. `open` shows every step and runs no rule; only `live` works as the page does.
  <!-- src: src/elements/form/form.js:145-147, src/elements/form-wizard/form-wizard.js:52-53, plugins/bfb-elements-pro/elements/form-step.php:143-148 -->

## Never do

- Do not write the form's `fields` setting (the save writes it), or key a field `total` or `step`.
- Do not test a single tick box with `is`; use `ticked` or `unticked`.
- Do not count on a field's Adds, `times` or `tiers` once `formula` is set; write them into the formula.
- Do not leave `max` unset on a Number Field whose answer may pass 10.
- Do not put a `bfbe-form-summary` or `bfbe-form-progress` in a form with fewer than two Steps, or a Button inside a Step.
- Do not wrap the Total in a block when `position` is `right` or `left`.
- Do not put an upload, signature, step, total or repeater inside a `bfbe-form-repeater`.
- Do not change a field's `type` without removing the keys only the old type offered.
