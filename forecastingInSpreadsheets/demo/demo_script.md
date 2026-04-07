# Demo Script 1.2: Forecasting in Spreadsheets

OK so we've got 731 days of bread sales. The bakery owner wants to know how much to bake next week. Let's see what we can do with just spreadsheet functions — no code, nothing fancy.

First up: the naive forecast. This is literally just "whatever happened yesterday, do that again." So we take the last day's sales — let's say it was 912 loaves — and paste that forward for two weeks. Dead simple. Dead flat. It's a baseline.

Next, the moving average. We take AVERAGE of the last 7 days. This is better because it smooths out the randomness. If Monday was weirdly low and Wednesday was weirdly high, they cancel out. The 7-day window is nice because it covers a full week. The 30-day window is smoother still but it's averaging over a whole month, so it's slower to react to recent changes.

Now TREND. This one actually fits a line through all 731 days. And look — the slope is positive. The bakery is growing, roughly an extra loaf every three days. That's useful information. But it's still just a line. It can't bend, and it certainly can't tell you that Saturdays are 15% busier than Mondays.

And that's the key takeaway here. All three methods give you a number. They answer "roughly how much." But none of them can answer "how much on Saturday vs Wednesday." For that you need something that understands the weekly cycle — which is what we'll get to with decomposition and seasonal models.
