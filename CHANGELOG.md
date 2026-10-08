# Book Crawl — Changelog

Human-readable history of what changed for teachers, parents, and readers.
(Internal record: GitHub commit history + Supabase SQL editor history.)

## October 8, 2026 (second update)
- The Undercrawl is out in the open. Every Descent board now shows a door
  beneath Floor 15: sealed (wood, brass bands, a padlock) until it opens,
  then glowing with candlelight. On a crawler's map it reads "🔒 A sealed
  door · something waits below…"; once it's open for them, it reads
  "🕯️ The Undercrawl" with an ENTER button that goes straight into the game.
- Crawlers standing on Floor 15 get a progress bar that counts down to the
  door ("8 points until you dig through the Final Shelf"). The door opens
  after one more floor's worth of points on Floor 15. That's how it has
  always worked; the wording everywhere now says "digs all the way through
  Floor 15" instead of "reaches Floor 15," so nobody is left wondering why
  a kid on Floor 15 still sees a sealed door.
- Play it yourself, no kid PIN needed. Map tab → 🕯️ The Undercrawl →
  ▶ Play it yourself. Pick a puzzle level (Extra help, Standard, or
  Challenge, the same levels kids get automatically from their reading
  level: below 500L, 500L to 749L, 750L and up) and start at the beginning
  or jump straight to Chapter One. It's a private preview: nothing is saved
  to any crawler, and your progress lives only in that browser tab (Continue
  picks up where you left off until you close it).
- The same card says who the door is open for right now ("sealed for now,"
  "open for 3 crawlers," "open for everyone"), and "Open it for everyone…"
  jumps straight to the switch in Settings → Class (Crew for families) and
  lights it up.
- The guided tour has a new step, "Beneath it all: the Undercrawl" (the
  tour is now 9 steps), and Help mentions the preview.
- No database change.

## October 8, 2026
- Settings is split into four sections, picked from a row of buttons at the
  top: **Class** (or **Crew**) for how reads get checked, your code, and
  what kids see (the tracker, their own Lexile range, the Undercrawl), plus
  the season pass; **Scoring** for the point values, loot-box size, and
  floor size (tuned defaults most teachers never touch); **Year-end** for
  the vault tiers, the CSV exports, and Begin next season; and **Account**
  for your password and two-step sign-in, which cover every class on your
  account. Settings remembers the section you were in.
- The section row is easy to spot: it's labeled "Settings · 4 sections",
  each button has an icon (🏫 or 🏠, 🎯, 🍂, 🔐), and it wears the same
  violet as the Settings tab itself, with the open section filled in. The
  first time you open Settings on a device, the row pulses once.
- Help moved to a ❓ button in the top bar, so it's one tap from any tab.
  The "Found a bug? Have an idea?" box now sits at the bottom of Help when
  you open it from your dashboard (never on the kids' side).
- On phones, the top-bar buttons got a little more compact so the logo and
  buttons still share one row on most phones (on very narrow screens they
  drop below the logo as a group), and the section buttons stack each icon
  over its word so all four fit in one row.
- No database change.

## October 7, 2026
- Optional two-step sign-in for grown-ups. Settings → 🔐 Two-step sign-in
  adds a 6-digit code from an authenticator app (Google Authenticator,
  Microsoft Authenticator, 1Password, and the like) to every sign-in,
  including Google and Microsoft sign-ins. Scan a QR code (or type the setup
  key), confirm one code, done. Add a backup device in the same card; turn
  it off there too. Nobody has to use it, and kids are untouched.
- It's enforced by the database, not just the screen: once an account turns
  it on, its class data stays locked to any session that hasn't passed the
  code, and the AI pre-screen refuses that session too. A device that was
  already signed in gets asked for the code at its next refresh.
- Lost every device? Email contact@thebookcrawl.com from the account's
  address; after confirming it's you, Book Crawl resets it.
- The Privacy Policy now lists what two-step sign-in stores: a secret setup
  key and a device label per authenticator, used only to check codes.
- Small fixes for typing on a slow connection: when the Google/Microsoft
  buttons loaded a beat late, they could wipe an email and password you'd
  already started typing, and a dashboard refresh finishing after an edit
  could wipe a box you'd moved on to (like the next ISBN right after adding
  a book). What you're typing now survives both.
- Requires migration-20 (safe any day, before or after the paywall
  migration) and the screen-read v6.2 function. Steps are in MFA-SETUP.md.

## October 5, 2026
- A guided tour for new grown-up accounts. The first time a teacher or
  parent opens a brand-new dungeon, a one-minute tour dims the page,
  lights up each tab in turn (Class or Crew, Queue, Map, Books, Loot,
  Settings), and explains what lives there before anything gets set up.
  Skip it any time; replay it from the first-steps card or from Help. On
  phones, the tab strip slides each lit tab into view.
- The first-steps buttons now take you all the way there. "Add students"
  ("Add crew members" for families) opens the Class tab's crawler
  generator, scrolls to it, and highlights it. On a phone, the old button
  changed the tab below the fold, so it looked like nothing happened.
- Family crews no longer see classroom words on the grown-up screens:
  crew members instead of students, crew points, the crew library, the
  crew tracker, and the crew code on PIN cards.
- The tour, the first-steps card, and Help now describe checking a read
  the way your dungeon is actually set up: a quick book talk in Classic
  mode (where every new dungeon starts), or the quest report once you
  switch to Quest Report in Settings.
- No database change.

## September 29, 2026
- All Book Crawl email now runs on Amazon SES in a US region: sign-up
  confirmations and password resets for grown-ups, plus the operator's own
  feedback alerts and Monday digest. Our previous email service (Brevo)
  kept its servers in the EU and is retired. Nothing changes on screen;
  the Privacy Policy now names Amazon Web Services as the email provider.
  (Server-side: new feedback-alert and weekly-pulse functions, and new
  Supabase SMTP settings. Steps are in SES-SETUP.md.)

## September 28, 2026 (evening)
- The AI reading pre-screen now runs US-only: every Quest Report check and
  every 🎤 spoken re-check is processed on US-based servers (the server
  function itself is pinned to a US region), and each advisory note
  records where it ran. It also moves to a newer model (Claude Sonnet
  5.5). Still advisory, still teacher-only, still no student names or
  identifiers sent. (Server-side: redeploy the screen-read function.)
- Tighter AI access: the server now confirms each teacher's sign-in with
  the sign-in service and checks that they own the class before doing
  anything, so no one can run or see another class's AI checks.
- Classic verification now means no AI at all: a class in Classic mode
  never sends anything to the AI pre-screen, even for older Quest Reports
  logged before the switch, and the server refuses it too.
- Accessibility pass toward WCAG 2.1 AA: an automated scan of 22 screens
  (kid and teacher, light and dark mode) now comes back clean. Small text
  is darker and easier to read, every form field has a proper label for
  screen readers, pop-up messages are announced, input boxes and the
  keyboard focus ring are easier to see, and locked Year-End Vault tiers
  stay readable (dashed outline instead of fading out). Each crawler in
  the teacher's class list now opens with the keyboard, and the kid home
  banner reads clearly in dark mode.
- Sign-up confirmation emails now bring new teachers back to the address
  they signed up on, instead of the main domain (which some school web
  filters still block).
- The feedback box now asks grown-ups to leave out students' real names.
- The game's fonts are now built into the page, so kid devices talk only
  to the Book Crawl site and its database - no outside font service.
- Terms of Service: if a school or district signs its own agreement with
  Book Crawl, that signed agreement wins wherever the two differ. The
  deletion wording is also corrected: teachers delete students and books
  themselves, and whole classes are deleted on request.
- Privacy Policy: states that AI checks run in the United States and that
  Anthropic deletes them within 30 days, discloses that our email service
  also carries our own operator alerts (never student data), lists
  everything stored (including reading-level history and
  teacher-only notes), notes that cleared data leaves backups within 7
  days, and puts a clock on incident notices: no later than 72 hours
  after an incident is confirmed.
- No database change.

## September 28, 2026
- One-click sign-in for grown-ups: "Continue with Google" and "Continue with
  Microsoft" now sit on the teacher/parent sign-in and create-account screens,
  beside email and password. Already have a password account with the same
  email? It joins up automatically - same classes. Each button appears on its
  own once that sign-in is switched on; until then, nothing changes.
- The Privacy Policy and Help page now explain what these sign-ins share: the
  provider confirms your email and passes along your name and profile-picture
  link, which stay with your sign-in record and are never used by the game.
- No database change.

## September 21, 2026
- THE UNDERCRAWL, CHAPTER ONE: THE LIBRARY OF TEETH. The gate your deep
  crawlers opened now leads somewhere: twelve new rooms of biting books,
  a nervous cart named DEWEY, three brass teeth to earn, and one very
  Overdue Book to carry home. New reading muscles hiding in the fun:
  idioms, dictionary guide words, Greek and Latin roots, main idea,
  compare-and-contrast, and multi-step directions - each puzzle quietly
  matched to the reader (easier, standard, or leaner wording) and locked
  in, so a mid-year level retest never changes a puzzle out from under
  a kid. Saved progress carries over; crawlers who finished Chapter 0
  just GO NORTH.
- Fixed a small restore bug: reloading the page while inside the game
  could briefly show the sealed-door card before the door state loaded.
- No database change - deploying this is uploading the new index.html,
  nothing else.

## September 17, 2026 (evening)
- THE UNDERCRAWL — a hidden text adventure now waits beneath Floor 15.
  Crawlers who reach the Final Shelf find a brass terminal and a game
  they can only play by typing: classic "GO NORTH" exploration, kid-sized,
  with reading practice hiding in every puzzle (finding evidence, context
  clues, synonyms, following multi-step directions — plus honest
  keyboarding). Hints never run out, and the last hint is always the
  answer, so every kid who asks can finish.
- Two new switches: Settings can open the Undercrawl for the whole class
  (the year-end move, so everyone gets to play), and each crawler's detail
  page can open it early for one kid who won't reach Floor 15 in time.
  In-game, an early door is always framed as the Dungeon's own choice —
  no kid is ever told why.
- Scaffolding scales per crawler, quietly: readers who need more help get
  proactive nudges from Scribble the ghost librarian; stronger readers get
  leaner hints. No kid ever sees a level or a "mode."
- Privacy, same rules as everywhere: the words kids type are read on the
  device and thrown away — never stored, never sent. Progress saves as
  room + puzzle flags only. The game pays no points or boxes, so there's
  nothing to farm.
- Requires migration-19 (safe to run any day, before or after the paywall
  migration).

## September 17, 2026
- Quest Report variety doubled: 16 fiction and 16 nonfiction questions
  (up from 8 each). Every crawler now gets their own shuffled order and
  works through all 16 before any question repeats — and two kids logging
  side by side almost never see the same prompt. The question stays put
  until the book is actually logged, so refreshing the page doesn't
  re-roll it.
- Fixed a quiet bug the new rotation surfaced: reopening the site straight
  onto a half-finished log form could show the wrong quest question until
  the crawler's data finished loading. The form now waits that beat out.
- New behind-the-scenes operator digest: a Monday-morning "pulse" email
  with the week's reads, active classes, and top dungeons (server-side
  only — nothing changes in the app).

## September 15, 2026
- Pressing Enter now submits the teacher sign-in (and create-account,
  forgot-password, and new-password forms) — no more reaching for the
  mouse. Enter in the email field hops to the password field first.
  Kid devices already had full keyboard login (typed class code, typed
  PINs); that's unchanged.
- New behind-the-scenes alert: bug reports and ideas from the in-app
  feedback box now land in the operator's email inbox the moment they're
  submitted (server-side only — nothing changes in the app).

## September 12, 2026
- Begin-next-season button (Settings → 🍂 Season, classrooms only): one
  type-the-class-code-to-confirm action clears the year's crawler data —
  crawlers and PINs, reads, points, boxes, gear — while the class library,
  prize lists, bounty settings, and class code all stay for next year's
  readers. Family crews never have a reset; their data stays until the
  parent deletes it. This makes the Privacy Policy's season-scoped
  retention a real button.

## September 11, 2026 (evening)
- AI advisory notes no longer get cut off mid-sentence (the note limit was
  too tight; screen-read v5.2 gives verdicts room to finish).
- The Box ledger now groups by crawler — kids with prizes waiting float to
  the top with their unclaimed boxes as check-off chips; delivered history
  tucks behind a "show given" toggle.

## September 11, 2026
- Reading levels are now entered as ranges (200L bands), never exact
  numbers — an extra layer of de-identification. Scoring is unchanged.
- Rosters are generated from a head-count: the dungeon invents every
  crawler name and PIN, and real names are written by hand on the printed
  key sheet only. No real name is ever typed into the app.
- Graphic novels and picture-heavy books can be flagged 🎨 (queue, Books
  tab, or scanner). Their pages earn length credit at about a third, for
  points and page bounties alike — applied to future logs only, so no
  reader ever loses points already earned.

## September 10, 2026
- Landing page now links About, Terms, and Privacy in the footer.
- New "Why Book Crawl exists" mission page.
- Privacy Policy retention rewritten as a season-scoped policy: year-end
  class reset clears crawler data (class library carries over), family-crew
  data persists until the parent deletes it, and accounts inactive 24 months
  are deleted after email reminders.
- Independence disclaimer added everywhere: Book Crawl is not affiliated
  with, endorsed by, or operated by any school district.

## September 9, 2026
- "Don't know the level?" helper and an F&P / DRA / AR → Lexile conversion
  chart beside the add-student form (popups — the half-typed form survives).
- Terms now state account holders must be 18+; students never make accounts
  and are never asked their age.
- Privacy Policy commits to prompt breach notification and cites Georgia's
  student-data law (O.C.G.A. § 20-2-666).

## September 8, 2026
- "Look it up" level searches no longer quote the title — misspelled titles
  find results (adds the word "book" to keep short titles on target).

## September 6–7, 2026
- Moved to thebookcrawl.com with contact@thebookcrawl.com on the legal pages.

## September 4, 2026
- Scan-a-book: point a phone at the barcode — title and pages fill in, and
  if another Book Crawl class already leveled that book, the level is
  offered on the spot (community level database v1). Type-the-ISBN box for
  keyboards. On-device decoding; only the ISBN ever leaves the phone.
- Kids can see their own Lexile range (per-class switch, off by default) —
  each reader sees only their own, framed with sweet-spot/stretch language.
- Print-it-twice popup after roster import: one key sheet to keep, one to
  cross-check against the class roster.
- Privacy Policy upgraded for district review: school-consent COPPA section,
  Schools & FERPA card, complete service-provider list, no-identifiers AI
  statement; the student answer box now says "no real names."

## September 3, 2026
- Loot tab rearranged: custom bounties under the Bounty Board, drop odds
  beside prize lists.
- 🎤 in-person re-check reliability fix (sign-in token handling).

## September 2, 2026
- The big feature batch: Treasure Codex (tiers, odds, gear, prizes), 🎤 on
  every quest card, re-read warnings, did-you-mean title matching + merge
  tool, bounty dials + teacher-written custom bounties, the Quartermaster's
  stretch-zone book picks, and an in-app feedback box.

## September 1, 2026
- In-app Terms of Service and Privacy Policy; first-steps checklist for new
  dashboards; spoken re-checks judged independently of the written answer.
- Season-pass groundwork built (dormant until the free period ends).
- Prize editor fix: every class sees all five tiers with starter ideas.

## August 31, 2026
- Kids-first landing page with the teacher/parent door below.
- Stage 5 — The Descent: 15 personal floors, the shared party board
  (floor clusters, never points), and the teacher 🎤 verbal re-check.
- Family crews: parents can run Book Crawl at home with the same rules.

## August 30, 2026
- Multi-tenant platform cutover: teacher self-signup, per-class isolation
  enforced by the database, one shared site for every classroom.

## August 2026 (the classroom era)
- Born as one teacher's classroom app: verified reading logs, points scaled
  to each reader's own level, loot boxes, cosmetic gear, dungeon backdrop,
  the Year-End Vault, Ceremony Mode, bounty quests, and the AI reading
  pre-screen (teacher-advisory, never grading kids).
