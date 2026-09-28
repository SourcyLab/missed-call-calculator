# Missed-Call Cost Calculator for Contractors

A free, open-source, single-page calculator that estimates how much revenue a contracting business may be losing to unanswered phone calls. It uses **only the numbers you type in**. There are no built-in industry averages, no tracking, and no server. Everything runs in your browser.

**Live tool:** https://sourcylab.github.io/missed-call-calculator/

**Repo:** https://github.com/SourcyLab/missed-call-calculator

Built and maintained by Sourcy Inc., Florida. MIT licensed.

---

## Why this exists

Every contractor knows missed calls cost money. Very few know roughly how much. Industry "averages" get quoted a lot, but they're rarely sourced and rarely match your trade, crew size, or season. This tool skips the averages. It walks your own numbers through a simple funnel so you can see the size of the leak and decide whether it's worth fixing.

## What it calculates

| You enter | Notes |
|---|---|
| Inbound calls per month | All inbound calls to your business line(s) |
| % of calls missed | Not answered live (rang out or went to voicemail) |
| % of missed callers who don't call back or go elsewhere | Missed calls you never reconnected with |
| % of calls that are real new-job leads | Leave out vendors, spam, and existing customers |
| Close rate on leads (%) | Out of every 100 leads you talk to, how many become paid jobs |
| Average job value ($) | Average revenue per job |
| Your monthly cost ($), optional | No default. Leave blank if you don't need a break-even figure |

| You get | |
|---|---|
| Lost leads per month | |
| Lost jobs per month | |
| Estimated revenue lost per month and per year | |
| Break-even (only if you enter "Your monthly cost") | Recovered jobs per month needed to cover that cost |

## The formula

```
lost revenue per month = calls × missed% × no-callback% × lead% × close% × average job value
lost revenue per year  = lost revenue per month × 12
break-even jobs/month  = your monthly cost ÷ average job value
```

### Worked example (illustrative example values, not data)

These numbers are made up to show the math. They're the same values the **Load example values** button fills in. They are not industry statistics. "Your monthly cost" (optional) is left blank in the example on purpose, so enter your own figure to see break-even.

| Step | Math | Result |
|---|---|---|
| Inbound calls per month | example input | 200 |
| Missed calls | 200 × 20% | 40 |
| Missed callers who don't call back | 40 × 60% | 24 |
| Lost leads | 24 × 50% | 12 |
| Lost jobs | 12 × 30% | 3.6 |
| Revenue lost per month | 3.6 × $1,500 | $5,400 |
| Revenue lost per year | $5,400 × 12 | $64,800 |

## How to get good inputs

The result is only as good as what you put in, so measure instead of guessing:

1. **Export your call log** from your carrier or VoIP system for at least two full weeks.
2. **Missed%** = unanswered inbound calls ÷ all inbound calls. Count calls that went to voicemail as missed.
3. **Compare voicemails to missed calls.** The gap is roughly the callers who hung up without leaving a message.
4. **No-callback%:** for the same period, note which missed numbers you never reconnected with.
5. **Lead%:** tag which calls were new-job inquiries.
6. **Close rate:** use your CRM, job board, or a spreadsheet of estimates sent vs. jobs won.

Measure during a busy stretch and a slow stretch if you can. Missed calls tend to bunch up when crews are on jobsites and after hours.

## Ways to recover missed calls

The page includes a neutral comparison of the common options, with the tradeoffs of each: call forwarding, live answering services, automatic text-back, AI receptionists, and a set callback routine. Many contractors combine two or more.

## Privacy

- No analytics, cookies, trackers, or third-party scripts.
- No external fonts, CDNs, or dependencies.
- No form is submitted anywhere. All math happens in the browser in plain JavaScript you can read in `index.html`.

## Accessibility

- Every input has a visible label and a hint. Errors are announced to screen readers (`aria-live`) and flagged with `aria-invalid`.
- Results and status updates are announced as they change.
- Full keyboard support, a skip link, and visible focus outlines.
- Touch targets are at least 44px, and the layout adapts from phone to desktop.
- Includes a print stylesheet.

## Use it, fork it, embed it

- **Use it:** open the [live page](https://sourcylab.github.io/missed-call-calculator/), or download `index.html` and open it locally. It works offline.
- **Clone it:** `git clone https://github.com/SourcyLab/missed-call-calculator.git`
- **Fork it:** click *Fork*, change the copy or colors in `index.html`, and enable GitHub Pages under **Settings → Pages → Deploy from branch → `main` / root**.
- **No build step.** It's one HTML file with inline CSS and JS.

The calculation lives in one pure function, `computeMissedCallCost()`, inside `index.html`, which makes it easy to test or port. In the browser it's also exposed as `window.MissedCallCalc.compute` for quick checks from the console:

```js
MissedCallCalc.compute({ calls: 200, missedPct: 20, noCallbackPct: 60, leadPct: 50, closePct: 30, jobValue: 1500 })
// → lostJobs ≈ 3.6, lostRevenueMonthly ≈ 5400, lostRevenueYearly ≈ 64800, breakEvenJobs = null (no cost entered)
```

## Contributing

Issues and pull requests are welcome, especially accessibility fixes, translations (Spanish would be great), and clearer explanations. Please don't add tracking scripts or unsourced statistics.

## About

Built by Sourcy Inc., a Florida AI implementation company. If you want to see how an AI receptionist can answer and route calls you'd otherwise miss, [see how Sourcy's AI receptionist handles missed calls](https://sourcyinc.com/ai-receptionist-pricing?utm_source=github&utm_medium=offsite&utm_campaign=parasite-pilot).

## License

[MIT](LICENSE) © 2026 Sourcy Inc.

*This tool gives estimates only, based entirely on user-entered numbers. It is not financial advice. Last updated September 28, 2026.*
