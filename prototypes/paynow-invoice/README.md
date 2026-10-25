# Chop Invoice (PayNow QR invoice maker)

Phone-first invoice and quick-charge tool for hawkers and SMEs. Make an invoice, and it adds a PayNow QR with the exact amount and invoice number as reference. Or type an amount and show a full-screen QR at the counter.

## Open
Double-click `index.html` (needs internet once to load the QR library), or use the artifact link on your phone.

## What works
- **Quick charge:** amount + optional reference → full-screen locked-amount QR, preset amount chips, "Paid, save it" logs today's takings
- **Invoice:** line items, qty × unit price, optional 9% GST (shows "Tax invoice" + GST reg. no.), due date from your payment terms, notes
- Paper-style invoice preview with QR, red PAID chop when marked paid
- Copy WhatsApp message / open WhatsApp with the message filled in
- Customer link (invoice + QR in the URL, no server) and print / save PDF. These only work when opened directly or from a normal website, not inside the claude.ai artifact viewer
- History: owed, overdue, paid this month; tap status to toggle paid; tap an invoice to reopen it
- My business: PayNow mobile or UEN with validation, a S$0.01 test QR to check in your own banking app, backup / restore, erase
- Example data is preloaded with a banner until you enter your own name and PayNow number

## How the QR works
It builds a standard SGQR / EMVCo payload (`SG.PAYNOW`, currency 702, amount not editable, reference in tag 62) with a CRC16 checksum. **Scan the test QR with your own bank app before using it with customers.**

## Next steps
1. Test with DBS / OCBC / UOB apps and fix anything an app rejects
2. Auto-detect payment (needs a bank API or a manual "check" flow); reminders for overdue invoices
3. Sync across devices and a proper hosted link (GitHub Pages) so customer links work everywhere
