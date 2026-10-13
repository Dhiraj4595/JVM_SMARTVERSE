# JVM SMARTVERSE — fixes in this build

## Teacher chatbot student selection and marks editing
- Fixed the natural-language edit parser so subject-only mark updates after selecting a student from **View My Class / Assigned Students** use the currently selected student instead of trying to search for a student using subject words.
- Added handling for filler phrasing such as “subject maths” and “update marks” when resolving the target student.
- Existing server-side authorization and the save-confirmation step remain in place. Teachers can still edit only records assigned to their account and only the fields allowed for their role.

## Chatbot knowledge improvements
- Added targeted answers for report cards, attendance, locating a Student ID/Registration Number, transport guidance, timetables, and campus facilities.
- Prevented generic “report card” questions from being mistaken for academic-calendar questions.
- Prevented a plain “registration number” help request from being misrouted into admissions guidance.
- Updated the fallback suggestions to mention report cards, attendance, transport, and facilities.

## Validation
- `python -m py_compile app_server.py` passes.
- `tests_api.py` passed all existing API/permission/payment/chatbot checks against a copied database after the final routing refinements (0 failures).
- Browser UI tests could not be run here because the Playwright Chromium executable is not installed in the environment.
- Regenerate page copies with `python build_pages.py` after changing `index.html`; this was done for this build.

No student records, teacher assignments, passwords, or database contents were intentionally changed.

## October 2026 — admission response refinement
- Unsupported admission classes (for example, Classes 9 and 10) now receive a direct, link-free message that admissions are not listed for that class, rather than a provisional-test or missing-data fallback.
- Class XI optional-subject questions return a readable stream-specific list from the supplied 2026–27 notice, including separate PCM and PCB options; they no longer display the full admissions summary or redirect links.
- Class XI overview responses use clear headings and separate sections for status, eligibility, streams, fees and dates. The responses explicitly label the 2026–27 notice as a past cycle.
- Added API regression checks for unsupported classes, stream optional subjects and reduced redirect use.


## Additive public-content enhancement (October 2026)
- Added two news cards for the 2026 CBSE Cluster-III Table Tennis Tournament and campus-life highlights, using local site images and published/official sources.
- Updated the campus gallery introduction copy only; existing gallery tiles remain intact.
- Extended the public chatbot knowledge base with brief sports, recent-news and campus-update answers and links to local pages. Existing privacy, portal and account-specific protections remain unchanged.
- No Facebook embeds, Facebook redirects, external scripts, or Facebook links were added. The supplied Facebook page could not be reliably inspected in this environment, so factual additions use accessible official school information and published reporting instead.


## Chatbot routing, public school data, and admission policy regression fixes
- Added source-backed chatbot answers using the existing `achievements.json`, homepage leadership cards, academic calendar and official school links for achievements, facilities, photos, current notices, historical events and leadership.
- Separated educational photosynthesis questions, gallery requests, and personal Class 10 revision planning from gallery, event-calendar and regular-timetable routing.
- Historical-event questions now inspect the requested year in the packaged calendar and explicitly say when no historical events are recorded instead of substituting upcoming events.
- Admission responses identify LKG, Class III (subject to a confirmed vacancy), and Class XI as the published external-admission categories; Class III 2026–27 remains unavailable per the official no-vacancy notice. LKG status is not claimed open without a verified deadline, and other classes are declined unless a newer official notice changes the policy.
- Added regression checks for the original intent-routing failures, achievements, facility counts, admission eligibility/status, historical events and privacy.
- Official school records conflict on leadership: the homepage lists Mr. Samarjit Jana as Principal, while the official “Principal (Acting)” message is signed by Mr. B. N. Jha. The chatbot flags this conflict instead of presenting one designation as unambiguously current.
- Current public source data does not contain a verified establishment year, school motto/house names, or a complete timestamped notice feed; answers disclose those gaps and link to official sources.
- Validation on a fresh copy of the bundled database: `python -m py_compile app_server.py` passed; `tests_api.py` passed **120 checks, 0 failures**; `tests_cors.py` passed **20 checks, 0 failures**. Browser UI tests were attempted but could not run because the Playwright Chromium executable is not installed.
