# Book Crawl — Changelog

Human-readable history of what changed for teachers, parents, and readers.
(Internal record: GitHub commit history + Supabase SQL editor history.)

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
