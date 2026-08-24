# feedwaffle.com

The landing page and waitlist for [waffle](https://apps.apple.com/): one photo
a day, with friends. A single static HTML file; no build step, no framework.

## Deploying

Vercel, root directory `./`. There is nothing to build: `index.html` and
`vercel.json` are the whole site. `vercel.json` adds security headers and
clean URLs.

## The waitlist

The form posts to a Supabase table called `waitlist`. The anon key in the page
is public on purpose (that is what it is for) and the table is **insert-only
for anon**: someone can add an address, nobody can read the list back with that
key. Read signups from the Supabase dashboard or with the service role, never
from the page.

A duplicate signup returns 409 and the page treats it as success, because from
the visitor's side already being on the list is not an error. Email format is
checked in the browser as a courtesy and in the database as a rule.

## Editing

The copy was checked against what the app actually does. The free tier is one
waffle and one photo a day, there is a paid tier, and friend search does match
any handle. If you change a claim here, check it against the app first.
