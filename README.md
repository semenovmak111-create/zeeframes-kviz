# ZeeFrames — six-step quiz "Узнайте, какой сайт подойдёт вашему бизнесу"

The quiz is built as one more block of zeeframes.com: the home page FAQ section ("Questions? We've Got
Answers") with the same size and values. At 1440 it is 636 px tall on every step, as the FAQ. The site's
values are listed at the top of `quiz.css`.

- Left: the FAQ intro (eyebrow, heading, one line of text). Where the FAQ has the pill and the
  Clutch widget, there are six progress squares with "Вопрос 2 из 6" and "Назад".
- Right: the FAQ accordions. The question is the open card in lime. The answers are the closed
  cards with the plus icon. A picked answer opens like an accordion: lime border, lime icon with a check.
- Result: the open card names the site type, **лендинг-«Атлант»**. The type is fixed and the answers do
  not change it. The answers only fill the last paragraph: every option of questions 2, 4 and 6 carries
  its sentence in `data-why`, and the result takes one per question, one per line.
  Question 4 is multi-choice, so it gives the sentence of its first picked option.
  Below that paragraph are the lime `.btn-primary` pill with the site's text-swap hover and "Пройти заново".

The copy went through the `teksty-sayta` skill. The earlier looks are kept in `eskizy/`: F is the band across
the section seam (`f.css`), and A–E are older.

amdc-site/v2 embeds `proverka/build.py: section_v2()`.

Demo: https://semenovmak111-create.github.io/zeeframes-kviz/

## Embedding

1. Copy `quiz.css` and `quiz.js` next to the page.
2. Link them: `<link rel="stylesheet" href="quiz.css">` in `<head>`, `<script src="quiz.js" defer></script>` before `</body>`.
3. Paste the `<section class="zqz" … data-zqz>` element from `index.html` where the quiz should be.

- The fonts are the site's: Inter Tight 400/500/600. On zeeframes.com they are already loaded.
- Colours come from the site tokens (`--color-primary`, `--color-black-300`, `--color-gray-900`, …).
  Each one has a fallback, so the block also works on a page without `colors.css`.
- Class prefix `zqz-`. No dependencies.
- Behaviour relies on `data-zqz-*` attributes only; see the comment at the top of `quiz.js`.
- The final button links to `#start`. Point it at your contact form.
- The answers are available as `window.amdcQuiz`, an array of six strings, once the result screen shows; pass them on with the lead form.
- `?zqz=N` in the page URL opens question N (7 is the result) with earlier answers filled in.
  It is meant for screenshots.

Accessibility:
- every answer is a `<button aria-pressed>`;
- the step counter is `aria-live`, the progress squares are buttons that open answered questions;
- digits 1–9 pick an answer while the quiz is on screen (not while typing in a field);
- hidden steps are `inert`;
- arrow keys move between the answers, Enter or Space picks one;
- keyboard users get focus moved to the next question;
- `prefers-reduced-motion` switches steps without fading.
