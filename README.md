# The Zevrant Forge safety brake

This public repository holds one small file, **`HOLD`**, that every
client's Forge reads at the start of every run, right after the client's own
kill switch. It is Zevrant's one way to pause buying for everyone at once,
because Zevrant has no access to any client's repository, account or keys.

*Zevrant executes rules the client defines. It provides no investment advice
and does not evaluate or endorse any configuration. Every option can lose
money.*

## What the file says

`HOLD` holds one line:

- `off`: nothing happens. This is its normal state.
- `on 2026-11-05 <a plain reason>`: the hold is on since that date, for that
  reason.

## What the hold does

While the file says the hold is on, every client's Forge **places no new
buys**: a morning run proposes or places sells only, and a check-in closes
any buy still waiting for an approval. **Sells, protective stops, fills and
the client's own controls (Pause, Kill switch, Close all) keep working as
normal.** Each client sees one line in their run and on their Forge Today
page: "Zevrant's hold is on since <date>: <reason>. Forge places no new buys
until it is off. Your sells and protective stops keep working."

## What it cannot do

It holds one word. Forge reads it into a yes or no and nothing else. It
cannot start trading, change a rule, place or cancel an order, turn a kill
switch off, or do anything but stop new buys. If the file cannot be reached
or read, Forge runs normally and Zevrant is alerted after two trading days
in a row.

## Who may turn it on, and when

**Only Zevrant's owner, and only when a defect could place wrong orders for
any client.** Never for market conditions, never for one client, never as a
trading decision of any kind. Every switch on or off is a commit in this
repository, so the date, the reason and who did it are public.

**To turn it on:** open the file `HOLD`, click the pencil (Edit), replace the
line with `on <today's date, YYYY-MM-DD> <the reason in plain words>`, click
**Commit changes**, keep the message, **Commit changes** again. Clients' runs
read it from their next run on.

**To turn it off:** the same steps with the single word `off`.
