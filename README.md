# fix-my-algo

A recommendation algorithm is built to hold your attention, and the fastest way to do that is to find whatever's most compulsive about you and give you more of it. Left alone, a feed doesn't necessarily show you who you are — it shows you who you are when something is trying to keep you watching. Those aren't the same thing. The rage bait, the outrage podcasts, the fifteenth video essay about a show you don't even like anymore: that's not necessarily your character revealing itself, it might just be your attention getting mined for whatever it's cheapest to extract.

So here's the question this repo is built around: if the algorithm is going to shape you either way, why not choose the shape? Instead of a feed that reflects your most extractable impulses, point it at someone whose attention you admire — a historical figure, a fictional character, anyone whose curiosity seems worth having — and let the algorithm's own mechanics (search history, watch time, likes, subscriptions) pull your homepage toward what that person would actually watch. You're not pretending to be them. You're using the same machinery that normally narrows you into a rage-baited, doomscrolling version of yourself, and pointing it at a version you'd rather grow into.

This is a hypothesis, not a guarantee — it's one pass of an experiment, not a peer-reviewed intervention. But the mechanism is real: the signals that train the algorithm are the same signals whether they're pulling you down or pulling you up.

## What this actually is

Not a script. There's no code to run here, because the thing doing the work is an AI agent that already has a browser it can control on your behalf — Claude in [Cowork](https://claude.ai), or [Claude in Chrome](https://claude.ai/chrome). What's in this repo is a prompt, written so you can hand it to that agent, name your character, and have it actually go watch, like, subscribe, and search its way through YouTube for you.

## Quick start

1. Open a session with an agent that has browser control (Claude in Cowork, or Claude Desktop/claude.ai with the Claude in Chrome extension).
2. Copy the prompt from [`PROMPT.md`](./PROMPT.md), fill in your character, and send it.
3. Answer the agent's questions about scope, engagement level, and which browser to use.
4. Sign into YouTube yourself before it starts driving the browser — it shouldn't ask for your password, and you shouldn't give it one.
5. Let it run. A real pass takes a while, because watch time is part of the signal and there's no way to fake that instantly — figure 20 to 40 minutes.

## How it works, mechanically

YouTube's recommender responds to a small set of explicit signals: what you search for, how much of a video you actually watch (not just click), what you like and subscribe to, and what you mark "Not interested" or block outright. The agent turns your chosen character into a handful of concrete interests, searches for solid content in each one, watches enough of a few videos per topic that it counts as a real signal, likes and subscribes where it's a good fit, and then works back through your current homepage marking off-persona recommendations as not interested — which is what actually speeds up the shift, since suppression is a stronger signal than addition alone.

## Before you run it

The agent should ask you these; if it doesn't, answer them yourself in the prompt:

1. **Persona** — name one, or ask it to suggest a few with a sketch of what each one's feed would look like.
2. **Scope** — only add new viewing, or also prune what's already there. Pruning is most of what makes a single session feel effective.
3. **Engagement** — watch only, or watch and like and subscribe. The latter is a stronger signal, and it's visible on your account.
4. **Browser** — the built-in Cowork browser, or your real Chrome via the extension.

## What this needs

- Browser control tied to an already-signed-in YouTube session — Cowork's built-in browser, or the Claude in Chrome extension driving your actual browser.
- You doing the sign-in. If the agent ever asks for your password, stop — that's not how this is supposed to work.
- Time, for the reason above.

## Limits, honestly

One pass doesn't rewrite months of viewing history. YouTube keeps learning from whatever you watch afterward, so the shift holds if you follow up by actually watching what it surfaces, and drifts back if you don't — this is a strong nudge, not a switch you flip once. If your account is shared with other people, you're reshaping their homepage too. And a single "Not interested" click suppresses a pattern, it doesn't erase it — a heavily reinforced old habit might take more than one pass to really recede.

There's also the open question this whole project sits on top of, which no single run answers: does watching what Stephen Dedalus would watch actually make you think more like Stephen Dedalus, or does it just make your homepage look like his? Probably somewhere in between, and probably it depends on whether you actually watch the stuff afterward instead of just letting the experiment run once and going back to whatever you were doing before.

## Worked example: Stephen Dedalus

The character that started this. For James Joyce's Stephen Dedalus, the agent split things into Joyce's own *Ulysses* and *A Portrait of the Artist as a Young Man*, Aristotle's *Poetics* and Thomistic aesthetics (claritas, integritas, consonantia — literally Stephen's own theory of beauty), Dante, the Irish literary revival (Yeats, Synge, Wilde), classical mythology with particular attention to the Daedalus/Icarus myth he's named for, and Jesuit intellectual history.

One session visibly moved the homepage away from news commentary, superhero-show shorts, and TV recaps, toward Great Books lecture channels, ancient and medieval philosophy, and Renaissance art — including matches the algorithm found on its own that the agent never searched for directly.

## Using this with a different agent or tool

`PROMPT.md` assumes an agent that can ask you clarifying questions before acting. If yours can't, just answer the four questions above inside the prompt itself instead of waiting to be asked.

## License

MIT — see [`LICENSE`](./LICENSE). If you improve the topic-breakdown approach, or adapt this to another platform, a PR is welcome.
