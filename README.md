# GTA Blackjack Coach

A blackjack helper for the Diamond Casino in GTA Online. Enter your cards and the dealer's upcard and it tells you the mathematically best move, shows your odds, tracks every hand you play, and runs statistical tests to find out whether GTA's blackjack is fair and how many decks it deals from.

It's a single web page that runs on your computer. There's nothing to install, no account, and none of your data is uploaded anywhere.

## Getting it

1. On this GitHub page, click the green **Code** button, then **Download ZIP**.
2. Unzip it and keep the folder somewhere you'll find again, like Documents.
3. Open `blackjack.html` in **Google Chrome**. If double-clicking opens it in Safari, right-click it and choose **Open With → Google Chrome**.

Use Chrome (or Edge or Brave) if you can. Everything works in Safari except saving straight to a CSV file. Don't open it from an iMessage or email preview: those show a blank page because they don't run the page's code.

To update later, download the ZIP again and replace the old `blackjack.html`. Your stats live in the browser, so they carry over. If they ever look empty, use **Open existing CSV** (see below) to load them back from your CSV file.

## Playing

1. Enter **your two cards**, then the **dealer's upcard**.
2. It shows the best move with a short reason, plus your chance of winning for each possible move.
3. Make that move in GTA, press the matching button, and enter any card you're dealt. If it says **Hit**, you can just enter the card you got.
4. When the round ends, tap what the dealer finished on (17–21 or Bust). Tap **I missed it** if you didn't see.

If the dealer shows a 10 or an Ace and turns over blackjack before you move, press **Dealer has blackjack**. A dealer who draws to 21 with three or more cards just has 21, not blackjack.

### Keyboard shortcuts

| Key | Does |
|---|---|
| `2`–`9`, `0` or `T` (10), `J` `Q` `K`, `A` | Enter a card |
| `H` `S` `D` `P` | Hit, Stand, Double, Split |
| `B` | Dealer has blackjack |
| `Backspace` | Undo |
| `N` or `Esc` | Start a new hand |

### The tabs

- **Play**: the coach, your current session's results, and the CSV controls.
- **Stats**: pick a day from the drop-down to see each session, your win rate, how lucky you were and every round.
- **Fairness**: the experiment (below).
- **Strategy chart**: the full basic-strategy chart, with your current decision outlined.

A new session starts automatically after an hour without a round, or whenever you press **New session**.

### Bet size and table

On the Play tab, set your **bet** ($50k max, $10k+ or under $10k) and **table** (main floor, high-limit or Penthouse). Both stay set until you change them and are saved with every round, so the Fairness tab can check claims that the game deals worse cards on big bets. If you have rounds from before this existed, the Fairness tab offers to tag them all with one bet size.

## Saving your data to a CSV

Under **CSV file**, click **New CSV file** and save it somewhere like Documents. From then on, every round is written to that file the moment it finishes. If Chrome asks about access, choose **Allow on every visit** so it reconnects by itself next time. If it asks again later, click **Reconnect**. Rounds played in the meantime are kept in the browser and written when you reconnect.

- **Open existing CSV** connects a file you already have and brings back any rounds the browser is missing.
- **Download CSV** saves a one-off copy.
- The CSV has one row per hand, including your bet size and table. Cards are written like `Kh` (K♥) when suits are recorded.

## The fairness experiment

Nobody seems to have tested how GTA deals its blackjack cards. This page can. The **Fairness** tab answers six questions:

| Question | How it's tested |
|---|---|
| **Is the card mix fair?** | Counts every recorded card by rank and compares it with a real deck (each rank 1 in 13, 10-value cards 4 in 13). |
| **Is the dealer fair?** | Compares how often the dealer finished on each total, and how often they had blackjack, with the exact math for the upcards they showed. |
| **How many decks?** | Within one round, every card comes out of the same shoe. With one deck you can never see the same exact card twice in a round. With more decks it gets a little more likely, and most likely if every card is drawn at random. It works out which of 1, 2, 4, 6, 8 decks or "every card random" best explains what you've seen. |
| **Do cards carry over between rounds?** | If GTA keeps dealing from the same shoe, cards from earlier rounds are missing from the next one, which would mean card counting could work. It compares that with a fresh shuffle every round. |
| **Is the dealer's upcard fair?** | How often the dealer shows a 10, J, Q or K, against 30.8% in a real deck. |
| **Do you get your share of blackjacks?** | How often your first two cards are a blackjack, against 4.7%. GTA ends the round instantly when you get one, so log those hands too or this reads low. |

**Compare by bet size or table.** A table on the Fairness tab splits the main checks (dealer upcards, dealer busts, dealer 19–21, dealer blackjacks, your blackjacks and hands won) by bet size or by table, each next to what the maths expects for those exact rounds. Anything a fair game would rarely produce is highlighted. The **Bet size** and **Table** filters narrow every test to just those rounds.

Each test gives a plain verdict: **Looks fair**, **Worth watching** or **Suspicious**, and for the deck tests the most likely answer. The percentages are the chance that a fair game would look at least this uneven by luck alone. Under 5% is worth watching; under 1% is suspicious.

These tests were checked against simulated games from known shoes. They identified 1 and 2 decks with certainty. After 500 rounds they picked 4 decks and "every card random" with about 75% confidence. In 30 simulated games the carry-over test never gave a wrong verdict; with too little data it says "Not clear yet" instead.

### Recording good data: lab mode

Turn on **Lab mode** on the Play tab. It's slower to enter, but it's what the deck tests need.

- **Suits:** after each card, press its suit (`S` ♠, `H` ♥, `D` ♦, `C` ♣), or `X` if you didn't see it. You can also tap the suit buttons.
- **Dealer's cards:** when your hand is done, enter the dealer's hole card and each card they draw. It stops by itself once they reach 17. If you miss them, tap their total instead.
- **Other players' cards:** enter every other card you can see at the table, then press **Save round** (or `Enter`).

Suits make the deck test about ten times more sensitive. As a rough guide, it takes about 200 lab-mode rounds to tell 1 or 2 decks from many, about 500 to tell 4 decks from "every card random", and thousands to separate 6 decks from 8. Two people collecting gets there twice as fast.

### Combining data with a friend

1. On the **Fairness** tab, enter **your name**, so your CSV says whose data it is.
2. Send each other your CSV files (download one with **Download CSV** if you haven't connected one).
3. On the **Fairness** tab, click **Add a friend's CSV** and pick their file. Their rounds are added to the tests but never mixed into your own stats. Adding a newer file from the same person replaces the old one.

**Playing at the same table?** Both of you turn on **Same table as a friend** before playing. You'll both log the same dealer cards, so rounds you both marked, logged within 2 minutes of each other with the same dealer upcard, are merged into one and each card is only counted once. You can skip entering your friend's hand as "other players", since their own log has it.

## Rules it assumes

These match the Diamond Casino:

- Dealer stands on soft 17.
- Dealer checks for blackjack before you play.
- You can double on any two cards, including after a split.
- One split per hand, and split Aces get one card each.
- No surrender.

The strategy and odds are for 4 or more decks.

## Privacy

Everything stays on your computer: your rounds are kept in your browser and in any CSV file you choose. Nothing is sent anywhere.

---

A fan-made tool for fun. Not affiliated with Rockstar Games.
