# ZeeFrames — six-step quiz (dark)

A six-question brief ("Получите прототип сайта и анализ рынка за шесть ответов") built from zeeframes.com
parts: the service pages' section head, the Stack block's vertical tabs as the list of questions
(answered tabs show the answer, so the list doubles as the summary), a dark Stack-style panel for the
question, the home page's dark FAQ cards as answers (picked = lime border and lime icon box), the lime
pill button and the ✦ list. On phones the tabs fold into the service pages' mobile toggle.

Demo: https://semenovmak111-create.github.io/zeeframes-kviz/

## Embedding

1. Copy `quiz.css` and `quiz.js` next to the page.
2. Link them: `<link rel="stylesheet" href="quiz.css">` in `<head>`, `<script src="quiz.js" defer></script>` before `</body>`.
3. Paste the `<section class="zqz" … data-zqz>` element from `index.html` where the quiz should be.

- The fonts are the site's: Inter Tight 400/500/600 and Geologica 500 (answers). On zeeframes.com they are already loaded.
- Colours come from the site tokens (`--color-primary`, `--color-black-300`, `--color-gray-900`, …).
  Each one has a fallback, so the block also works on a page without `colors.css`.
- Class prefix `zqz-`. No dependencies.
- Behaviour relies on `data-zqz-*` attributes only; see the comment at the top of `quiz.js`.
- The final button links to `#start`. Point it at your contact form.
- The answers are available as `window.amdcQuiz`, an array of six strings, once the result screen shows.
- `?zqz=N` in the page URL opens question N (7 is the result) with earlier answers filled in.
  It is meant for screenshots.

Accessibility:
- every answer is a `<button aria-pressed>`;
- the step counter is `aria-live`, the question list is made of buttons that open answered questions;
- hidden steps are `inert`;
- arrow keys move between the answers, Enter or Space picks one;
- keyboard users get focus moved to the next question;
- `prefers-reduced-motion` switches steps without fading.
