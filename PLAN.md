# Player-Scouting-Forms: next-round plan

_Written 2026-11-03 from a question-and-answer session with Andrew Rukidi. No code has been written yet._

## 1. Goal
Completed forms are the raw material for Afritech player dossiers and CVs. This round cuts
the repo down to the two formats people can actually use and makes sure full answers reach
Afritech.

## 2. What exists today (2026-11-03)
- Four forms: Player / Parent, Coach, Scout / FIFA Agent, and Coach-hire (club, federation or agency assessing a coach; added 2026-10-31).
- Three formats per form:
  - browser form pages, one per language (16 pages). They return a PDF or copied text and save nothing on the device;
  - dashboards (player, coach and scout only). One page holds all four languages, saves on the phone, and returns an email, PDF or JSON;
  - fillable PDFs, one per language (16 files).
- Languages: English, French, Portuguese (BR), Spanish (LATAM).
- No server. Nothing is stored anywhere except on the respondent's phone.
- Usage so far: only fillable PDFs have come back, and the forms are new.
- No links to any page in this repo have been sent to anyone.

## 3. Decisions
| # | Decision |
|---|---|
| D1 | Keep two formats: the fillable PDF and the dashboard. Delete the 16 per-language browser form pages. No redirects are needed, because no links were sent. |
| D2 | Build a Coach-hire dashboard so all four forms have one. |
| D3 | Dashboard email stays a short summary (the 1,700-character limit is unchanged). The person is told, in their language, to attach the saved PDF. **Save as PDF** comes before **Email**. |
| D4 | No new consent box. Publishing a player's profile is Andrew's decision case by case (as in the cv-desk plan). Consent only concerns the Player form. |
| D5 | The `players/` folder moves to afritech-sports-cv-desk and is deleted here. |

## 4. Coach-hire dashboard spec
- Copy the structure, styling, language switch, save-on-phone, progress percentage, checks, PDF, JSON and email behaviour of the three existing dashboards.
- Sections and fields: exactly those in the current `coach-hire.html` and its FR, PT-BR and ES-LATAM pages, with the same wording. Take the translations from those four pages before they are deleted.
- File name: `coach-hire-dashboard.html`.
- Email subject: "Afritech — Coach-hire — <coach full name>". The summary carries the coach name, assessor capacity, mandate and decision required, then the checks, as the other dashboards do.
- Email goes to Advisory@afritechsports.com.

## 5. Changes to all four dashboards
- Button order: Save as PDF, then Email, then the rest.
- Email body starts with one line in the chosen language, e.g. "Please attach the PDF you saved before sending." The summary follows, within the 1,700-character limit.
- No other changes.

## 6. index.html
For each of the four forms: title, one-line description (existing text), "Open dashboard", and the four fillable PDF links.
Nothing else: no browser form links and no player profile links.

## 7. Definition of done
1. The 16 browser form pages are deleted (coach, coach-hire, player and scout × EN, FR, PT-BR, ES-LATAM).
2. `coach-hire-dashboard.html` exists to the spec in section 4.
3. All four dashboards have the section 5 button order and email line.
4. The 16 fillable PDFs are unchanged.
5. `index.html` matches section 6.
6. `players/` is deleted.
7. Every dashboard, tested at 390px wide in all four languages, saves on the phone, reopens with answers kept, saves as PDF, and opens an email to Advisory@afritechsports.com with the attach-PDF line.
8. Search finds no link to a deleted file anywhere in the repo.

## 8. Not in this round
- Any service that stores submissions (Formspree, Google Forms or similar).
- Changes to form questions, including in the fillable PDFs.
- A new consent tick box.
- New languages.
- Redesigning the existing dashboards beyond section 5.
- Automatic links from the forms to cv-desk or to the scouting skill.

## 9. Open flags
1. **The cv-desk link already sent is dead.** cv-desk is still private, with no Pages site and no players. Anyone who received it sees a GitHub 404 or sign-in page until the cv-desk plan's first steps are done (make it public, switch on Pages, publish the first player).
2. **Full answers depend on the respondent.** Under D3, if the person forgets to attach the PDF, Afritech receives only the summary. Andrew has accepted this; revisit if summaries without attachments start arriving.
3. **Answers stay only on the phone.** If a respondent clears their browser data before sending, the answers are lost.
4. **Translation quality for Coach-hire:** the dashboard reuses the existing page translations. No one has checked them with a native speaker.
