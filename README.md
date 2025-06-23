# This is the human/machine readable list of Mozilla Privacy team triagers and dates each one is on duty

## To read the triage list and calendar
 Refer to regularly updated JSON file [triage.json](https://mozilla.github.io/privacy-triage/triage.json) with list of names and bugzilla emails, and a calendar with duty end-dates.
- `"triagers"` root object node holds a map of `"Full Name" -> { data }`.  Right now the `data` object keeps only the bugzilla email in `bzmail` field.
- `"duty-end-dates"` root holds a map of `date -> "Full Name"`, where the `date` is the last day the triager is on duty, inclusive.  The last date is `2035-01-01` pointing at the `Fallback` triager.  Getting there means the list has to be manually updated and re-published.

## To add Privacy triagers in to your google calendar
Just use [this link to add it to gcal](https://calendar.google.com/calendar/r?cid=https://mozilla.github.io/privacy-triage/privacy-triage.ics) and follow instructions.  The direct link to the ICS file is [here](https://mozilla.github.io/privacy-triage/privacy-triage.ics).

## To update the triage list
```
git clone https://github.com/mozilla/privacy-triage.git
cd triage-list
npm install
npm run update
npm run push
```

`npm run update` will automatically append the next full cycle of all triagers to the `triage.json` file.  `npm run push` will update the ICS file and `git push` the changes.  Then you are done.

If you already cloned before, then `update` and `push` commands are enough to publicly update the list.

## To remove a triager from the list because of PTO
Assuming you already cloned the repo as described above
```
npm run exempt -- <YYYY-MM-DD>
npm run push
```
where YYYY-MM-DD is the date from `duty-start-dates` you want to remove.  The triager at that date will be removed and all following triagers after the date will be shifted one week earlier.

Run `npm run help` for the full list of commands.

## Based on

This tool is based on [Necko Triage List](https://github.com/mozilla-necko/triage-list).

## Triage rotation in bugzilla

The triage owner is set up with the google doc mentioned in [firefox-source-docs](https://firefox-source-docs.mozilla.org/bug-mgmt/policies/triage-bugzilla.html).
