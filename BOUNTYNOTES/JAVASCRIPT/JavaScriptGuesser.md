# JavaScript Number Guessing Game

`JavaScriptGuesser.js` (kept alongside this note, code unchanged) — a console-based number guessing game built with Node's `readline/promises`.

## Logic Overview

| Step | What happens |
|---|---|
| 1 | A random secret number between 1 and 20 is generated |
| 2 | The user is prompted to guess via the console |
| 3 | Each guess increments a `tries` counter |
| 4 | The user is told if their guess is too low, too high, or out of range |
| 5 | The loop ends once the guess matches the secret, printing how many tries it took |

See `JavaScriptGuesser.js` for the full source.
