# 

CMBS Pricing Model

Commercial Mortgage Backed Securities (CMBS) are bonds backed by pools of mortgages
on commercial and multifamily real estate. Securitization of these mortgages into a CMBS allows one to divide the loans into credit classes, where the investor may buy securities of various credit qualities.

Compared to the residential Mortgage Backed Securities, the structures are generally
relatively simple. Since these mortgages always have some from of a prepayment penalty,
credit considerations are much more significant than the prepayment projections (the
opposite holds true for US residential mortgages). Generally, bonds are sequential pay,
with the most senior remaining class receiving the principal repayments (both scheduled
and prepays) and default recoveries. Similarly, the lowest rated class absorbs the default
losses.

This involves setting up subordination levels and coupon for the various tranches, together with tranche yields that are ultimately used to value the CMBS.

The subordination levels and yields are input into the system based on recent market activity, while the coupons and specifics of the transaction (e.g. the time tranching of the AAA securities) is determined based on the underlying collateral.

Finally, we use the all this information to project cash flows for the various tranches, and finally value the deal by discounting using the input yields. The actual calculations performed are quite simple, and the largest risk to the model is the parameter inputs (subordination levels and pricing spreads). One needs to ensure that the inputs being used are consistent with the valuation being performed, or that the CMBS structure being considered is consistent with the market data used.

Individual mortgages are being valued by assuming only one loan in the collateral pool. This effectively split an individual loan into several bonds of varying credit quality, based on the CMBS these mortgages will eventually enter. This seems to be a reasonable approach to valuing the mortgages, since otherwise one would need to determine an appropriate credit level for each mortgage to perform valuation.

Firstly, we will review the basic equations governing cash flows from a mortgage. For a regular (i.e. not Interest only mortgage), the monthly mortgage payment M made by the mortgagee is given by

 

where P0 is the initial principal balance and N is the amortization term of the mortgage. The interest rate r1 is the initial monthly interest rate, and is given by the quoted coupon r of the mortgage multiplied by an appropriate day count. In the mortgages we examined, the day count convention used was ACT/360, which we were told was typical for commercial mortgages. 

Therefore, r1 is given by r times the actual number of days preceding the first mortgage payment divided by 360. This monthly payment is fixed thereafter. For interest only mortgages, M is still given as above, this payment is not actually made until the IO period is complete.

For months n from 1, .., T, where T is the term of the mortgage, the interest rate portion of this payment is simply given as

 

while the scheduled principal payment is

 

The interest rate rn, as before, is given by multiplying the coupon r by the appropriate day count fraction for that payment month. Finally, the remaining principal at each period is then given by Pn = Pn−1 −PNn. At time T, the outstanding principal payment is made. For the interest cash flows, a servicing fee is subtracted out. Therefore, the actual collateral interest payment is given by

 

where s is a fixed servicing ratio (typically 30 bps).

As stated earlier, these mortgages differ from residential mortgages with regards to prepayments. Typically, they have a lock out period, followed by either a yield maintenance or defeasance period. The yield maintenance penalty is equal to the present value of the remaining mortgage payments multiplied by the difference between the note rate and treasury securities yield with the same term as the remaining term. 

This effectively allows the trustee of the securitization the ability to reinvest the amount in treasury securities that will yield the same return as if the mortgage were still part of the pool. The defeasance is similar, but in this case the mortgagee is responsible for providing a treasury security as replacement collateral for the prepaid mortgage. Thus, these provide no impact to the valuation of the CMBS. Finally, there is an open period near the end of the mortgage (typically 3 months) where the mortgage can prepay. This is discussed further in the next section.

The collateral pool considered in this report is shown in table 1. Note that most of the loans shown here have an IO period (some for full term), and most have a term of close to 10 years.

A typical CMBS structure consists of a series of tranches, where the cash flows are derived from the underlying collateral. In this simplest example, we define various sequential tranches where the sum of the notionals equals to the total collateral principal balance.

The main structural component of a CMBS deal is the credit tranching. To have AAA tranches, there must be enough credit support from less senior tranches that absorb any losses on the underlying collateral first. In table 2 we show the CMBS corresponding to the collateral pool shown earlier.

The sum of the tranches balances equals to the collateral outstanding principal. The last tranche (IO) equals to the collateral principal.

All principal cash flows from the underlying collateral first flow through the uppermost tranche (top down). In this case, this is the A1 tranche, and it receives principal cash flows (including potential prepayments and default recoveries) until the tranche balance is exhausted.

The A1,A2,A3 and A4 tranche are rated AAA, with a total principal balance of 86,976,000 or 88.35% of the total balance. They are time tranched, with the balances of each tranche dependent on the principal cash flows of the underlying collateral.

Any principal losses (from default) are absorbed by the most junior tranche (bottom up).

Interest is paid to all tranches based on the balance and coupon, subject to a net WAC limit. This means that the coupon on any individual tranche cannot exceed the collateral coupon for that period. Therefore, the coupon listed in the table are unrealistic and not relevant since the underlying collateral coupon is quite a bit below the coupons listed for the junior tranches.

Any excess interest payments after all tranches receive the appropriate interest is dumped into the IO tranche. There is no coupon listed since this value depends on the specifics of the collateral and CMBS structure.

As stated earlier, the relative sizes of each tranche (in terms of rating) are derived from recent market information of traded CMBS tranches. This is described in more detail in the valuation methodology documentation, where the document describes how to determine the subordination level of each rated tranche. Similarly, the documentation also describes how the yields used to discount the tranche cash flows are determined.

These yields are typically input as with a spread to a particular benchmark curve (see https://finpricing.com/lib/FxForwardCurve.html). To determine the appropriate benchmark rate, the average life Ta of each tranche is determined, which is simply the principal paid weighted average life, or

 

where Pt is the total principal (including scheduled, prepays and default recoveries) payable in period t. This is the average life that appears in table 2. Using this average life of each tranche together with the input spreads, the appropriate benchmark rate is determine using linear interpolation. Note that the final yield is used as a semi-annual rate with 30/360 day count convention.
