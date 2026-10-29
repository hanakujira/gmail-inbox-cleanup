# Cleaning a 33,000-email inbox with nothing but Gmail's built-in tools

> 繁體中文版 → [README.zh-TW.md](README.zh-TW.md)

> A free Gmail account holding 33,000+ messages. No apps, no extensions, **not a single email deleted** —
> and the inbox 90% smaller in about an hour. Everything here uses only what Gmail's web interface already
> has: search operators, Archive, and Filters.

## The short version

An inbox that has been filling up for a decade or more can go from **~33,000 to ~4,000 messages in under an hour**, and:

- **Nothing was deleted** (the All Mail total is identical before and after)
- **Nothing was duplicated**
- New promotional mail now **skips the inbox entirely** and lands under its own label

The 4,000 left behind were left on purpose — more on why below.

---

## Step 0: "Inbox" and "All Mail" are two different things

This is where most people get stuck.

- **Inbox**: a to-do list. It is just one label on a message, not a folder.
- **All Mail**: the actual store. Every message lives here, including the ones you archived.

So **Archive ≠ Delete**. Archiving only takes the message off the Inbox label. It stays in All Mail,
it is still searchable, it still shows up on your phone.

**Cleaning the inbox means moving things off the to-do list, not destroying them.**
Once that clicks, the mindset shifts from "I don't dare delete anything" to "I just need to move it".

---

## Step 1: Measure first, act second

Gmail's search box understands a lot. Size the job before deciding how much effort to spend:

| What you want to know | Search operator |
|---|---|
| How many messages are in the inbox | the number next to "Inbox" in the sidebar |
| Older than a year | `older_than:1y` |
| Older than six months | `older_than:6m` |
| Promotions | `category:promotions` |
| Notifications / receipts | `category:updates` |
| Social notifications | `category:social` |
| Primary (mail from actual humans) | `category:primary` |
| Has an attachment | `has:attachment` |
| Unread | `is:unread` |

**Operators stack**: `category:promotions older_than:1y`, `(category:promotions OR category:social) older_than:2y`.
The results header tells you roughly how many matches there are — that is the size of the move.

> My own numbers: an inbox of ~33,000 messages, of which "promotions + updates + social, older than a year"
> alone was **~29,000**. In other words, four fifths of that inbox was an ad warehouse, not a mailbox.

---

## Step 2: Sort out what should move and what must not

Gmail sorts mail into four tabs: **Primary / Promotions / Social / Updates**. A rough strategy:

| Category | Move it out of the inbox? |
|---|---|
| Promotions | ✅ Yes — and keep it from coming back |
| Social | ✅ Yes (social notifications nobody re-reads) |
| Updates | ⚠️ **Careful.** Bank, credit card, e-commerce and billing notices often land here |
| Primary | ❌ No. This is mail from actual people |

**"Updates" is the trap.** Plenty of people clear the whole Updates tab and only later discover their
statements, card notifications and invoices sank out of sight. I walked into this one myself: an earlier
plan of mine was going to archive `category:updates` too. Then I looked at the sender list —
one bank with 500 messages, another with 150, a digital account with 130, an app store with 200…
**Those are financial records, not junk.** So Updates stays, at most with a label on top.

> How to tell: check the senders before you move a batch. If banks, e-commerce, telecom, insurance or tax
> agencies show up in the list, leave that batch alone.

---

## Step 3: Move in one big batch (web UI only)

1. Type the condition into the search box, e.g.
   `(category:promotions OR category:social) older_than:1y`
2. Press Enter and wait for the results.
3. Tick the checkbox at the **top of the results list**.
4. A line appears: "All 50 conversations on this page are selected. **Select all conversations that match
   this search**." Click that link — otherwise you only selected this page.
5. Click the **Archive** icon in the toolbar (the box with a downward arrow).

That is the whole batch. You can also go in slices — change `older_than:1y` to `older_than:3y` and repeat.

**Check afterwards**: the All Mail count should be almost unchanged (archiving does not change the total).
If the total dropped, you pressed Delete instead of Archive — recover from Trash (it keeps 30 days).

---

## Step 4: Stop it happening again — filters

Without a rule, in six months you are back where you started. That rule is a **filter**:

1. Gear icon (top right) → **See all settings** → **Filters and Blocked Addresses**
2. **Create a new filter**
3. In "Has the words", enter: `category:promotions`
4. **Create filter**
5. Tick **Skip the Inbox (Archive it)** and **Apply the label**, creating a label called "Promotions"
6. **Create filter**

Repeat with `category:social` and a "Social" label.

**Do not set `category:updates` to skip the inbox** — same reason as step 2; that rule would make your bills disappear.

> Note: a filter only applies to mail that arrives *after* it is created. What is already in the inbox has to
> be moved with step 3.

### If "Create filter" does nothing on the filter page

If you hit this (some builds of the Gmail web UI have the bug), there is a second route: **import XML**.
The same settings page has an "Import filters" option that accepts a file like this:

```xml
<?xml version='1.0' encoding='UTF-8'?>
<feed xmlns='http://www.w3.org/2005/Atom' xmlns:apps='http://schemas.google.com/apps/2006'>
  <title>Mail Filters</title>
  <entry>
    <category term='filter'></category>
    <title>Mail Filter</title>
    <content></content>
    <apps:property name='hasTheWord' value='category:promotions'/>
    <apps:property name='shouldArchive' value='true'/>
    <apps:property name='label' value='Promotions'/>
  </entry>
</feed>
```

Pick the file → review → **Create filters**. All rules inside are created at once (missing labels are created too).

---

## So what are the 4,000 left behind?

Opening what remained, the top senders looked like this:

| Sender | Messages |
|---|---|
| A newsletter | ~600 |
| One bank | ~500 |
| An app store | ~300 |
| A payment service | ~170 |
| Another bank | ~150 |
| A digital account | ~220 |
| Others: brokers, telecom, delivery, streaming | 40–90 each |

All of it is **financial and purchase history**. Its value is not in reading it — it is in finding it when you
need to reconcile, cancel a subscription or file taxes. So it stays in the inbox; only ads and social
notifications were moved out.

If you want to go further, give them a filter that **only adds a label and does not skip the inbox** —
the inbox count stays the same, but you can pull them up with one click.

---

## One line to take away

> **An inbox is not a warehouse, it is a to-do list.**
> Archive is not delete, and a filter is the actual cure. The one thing to be careful about: don't throw your bills out with the ads.

---

License: CC BY 4.0 (please credit the source when reposting)
