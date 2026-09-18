# 5. Measurement and kill rules

Distribution without measurement produces opinions with dates on them. This chapter is the arithmetic that
decides whether a result is readable at all, and the rule that stops a losing test from quietly becoming a
permanent line in the budget.

## 5.1 Sample size before the test, not after

A two-variant test on a base conversion rate `p`, with a lift `d` you want to detect, needs roughly

```
n per arm = ceil( ( z_alpha * sqrt(2 p (1-p)) + z_beta * sqrt(p(1-p) + (p+d)(1-p-d)) )^2 / d^2 )
```

with `z_alpha = 1.96` and `z_beta = 0.84` for a two-sided 5% test at 80% power.

Worked example that ships in the package: base 3%, lift +20% (3% -> 3.6%) => **13,914 per arm**. Two arms,
so ~27,800 observations of the same event before the difference is readable. If your list has 800 contacts,
the honest sentence is "this test cannot conclude anything", and the useful move is to change the offer
rather than to keep sending until the chart looks convincing.

`npx -y marketing-mindset sample --base 0.03 --lift 0.2` prints this number. Do the arithmetic before the
first send; afterwards you are only choosing which story to tell.

## 5.2 The interval, not the point

Reported rates are intervals. The Wilson score interval behaves sensibly at small n and near 0/1 where the
normal approximation falls apart:

```
den = 1 + z^2/n
centre = (p_hat + z^2/(2n)) / den
half = z * sqrt(p_hat(1-p_hat)/n + z^2/(4n^2)) / den
interval = [centre - half, centre + half]
```

Two arms with [2%, 9%] and [4%, 13%] are not "the second one is twice as good"; they are one unknown
number. Overlap means the test has not decided.

## 5.3 The rule of three

Zero conversions in `n` sends does not mean the rate is zero — it means the rate is below roughly `3/n` with
95% confidence. 0/100 -> under 3%. 0/200 -> under 1.5%. That is the difference between "it flopped" and
"this size cannot see it", and it is the number that usually kills the campaign that was kept alive by
wishful reading.

## 5.4 Kill rules, written in advance

Write these four lines before the test starts:

1. **Sample**: the number of observations that makes the test readable (5.1).
2. **Horizon**: the date by which that sample is expected, or the decision date if it is not.
3. **Kill**: the result at which the path is switched off without further debate (for a cold sequence: reply
   rate under 1% at n >= 200, or 0 replies at n = 100 — rule of three).
4. **Scale**: the result at which the winner gets more volume, budget, or a second channel.

A test without a written kill rule is not an experiment, it is a subscription. Kill rules are also what make
a monthly retainer auditable: the invoice pays for shipped artifacts and documented decisions, including the
decisions that ended something.

## 5.5 What to instrument on day one

- One analytics property you own, on every page that is part of the path.
- One custom event per conversion, with the event fired on the action, not on the page view.
- One place where the raw sends and replies live (a sheet is fine — the point is that the denominator is not
  held by a third party).
- One outbound click event on the pages that carry your contact link, so the intent signal is visible before
  the first reply.

Instruments installed later measure the second version of the campaign, not this one.

## 5.6 Free tools referenced in this chapter

- Test planner (sends per arm): https://axelfreeman.github.io/marketing-mindset/tools/email-test-planner.html
- Kill-rule calculator (Wilson + rule of three): https://axelfreeman.github.io/marketing-mindset/tools/kill-rule-calculator.html
- AEO / agent-readiness checklist (23 checks): https://axelfreeman.github.io/marketing-mindset/tools/aeo-readiness-checklist.html
- CLI: `npx -y marketing-mindset aeo --json` and `npx -y marketing-mindset sample --base 0.03 --lift 0.2`

---

Part of the marketing-engineer playbook. Work with me: https://axelfreeman.com/marketing-engineer.html
