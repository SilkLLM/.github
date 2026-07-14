# SilkLLM, explained from A to Z

This document explains the whole system in plain language. It is for anyone who
asks "what is SilkLLM", whether you are a user who wants to build something, an
investor sizing up the idea, or a partner who needs to understand how the pieces
fit. There is no assumed background. Where a technical word is needed, it is
explained the first time it appears.

The website is getsilkllm.com.

---

## 1. The one sentence version

SilkLLM is one account, one key, and one prepaid balance that lets you use many
different artificial intelligence models from many companies, and pay for all of
them in one place.

That is the whole promise. The rest of this document is what sits under it.

---

## 2. A few plain words first

A few terms come up a lot. Here is what they mean in this document.

A "model" is a trained artificial intelligence that takes an input, like a
question or a picture, and produces an output, like an answer, an image, or a
spoken voice. Different companies make different models, and each is good at
different things.

A "provider" is the company that runs a model, for example OpenAI, Anthropic,
Google, DeepSeek, or xAI. Each provider gives out its own key and sends its own
bill.

An "API key" is a secret string of characters that acts like a password for a
program. When your software wants to use a model, it sends the key so the
provider knows who to charge.

A "token" is how models count text. A short word is one token, a longer word can
be two or three. Providers charge by the token, which is why usage, not time,
decides the bill.

"Prepaid balance" means you add money first, and each request draws from that
money. There is no monthly bill and no surprise at the end of the month.

---

## 3. The problem we set out to solve

If you want to build with artificial intelligence today, you quickly run into a
mess that has nothing to do with your actual idea.

Each provider makes you create a separate account. Each one gives you a separate
key to manage and keep safe. Each one sends a separate bill in its own way. Each
one has its own slightly different way of being called from code. And no single
one is best at everything, so serious builders end up wiring together several of
them.

So before you have shipped anything, you are already a part time account manager,
a part time bookkeeper, and a part time plumber connecting systems that were
never meant to sit side by side. That work is real, it is boring, and it repeats
every time a new model comes out.

SilkLLM removes that whole layer. One account. One key. One balance. One bill.
The models underneath can change and grow, and your setup keeps working.

---

## 4. Who it is for

Solo developers who want to ship something this weekend and do not want to spend
Saturday morning creating five accounts.

Small teams and startups that need to watch every dollar and want to see exactly
what their artificial intelligence usage costs.

Agencies that juggle many client projects and do not want a separate billing
relationship per client per provider.

Students and learners who want to try real models without putting down a credit
card on day one.

And anyone who already pays for a provider directly and would like their unused
allowance to work for them instead of sitting idle. More on that below.

---

## 5. How a request works, start to finish

Here is what happens when you ask SilkLLM to do something, told simply.

You send a request with your one key. You can name a specific model, or name a
provider and let us pick their best fit, or say nothing and let us choose a
capable model for you.

Before we call anything, we make a quick check that your balance can cover a
careful estimate of the cost. If it cannot, and no free trial covers it, we tell
you plainly to add credit rather than failing in a confusing way.

We then send the request to the chosen model. If that model is down or refuses,
we automatically try the next suitable one instead of giving you an error. This
is called a fallback, and it is the difference between a quiet recovery and a
broken app at a bad hour.

When the answer comes back, we work out the real cost from the provider, add a
small markup, take that amount from your balance, and write a permanent line in
your account history. Then we hand you the answer, along with exactly what it
cost.

The routing that picks the model is fixed and predictable. It is not itself an
artificial intelligence guessing. It follows clear rules: your explicit choice
first, then a provider's strongest model, then the cheapest healthy option. You
always know why you got what you got.

---

## 6. The money, and why we are careful about it

The heart of this system is money moving correctly. Everything else is built
around getting that right.

We charge the provider's real cost plus a small markup, around ten percent by
default. There is no required subscription. You pay for what you use, and you can
see the cost of every single request.

Every debit and credit is written to an account history that only ever gets added
to. Nothing is quietly edited or deleted. If you want to know where your money
went, it is all there, line by line.

We built strong protections into this path. A request is charged exactly once,
even if the network hiccups and the same request arrives twice. When many
requests hit your balance at the same moment, we lock the balance briefly so two
of them cannot both spend the last dollar. Every charge has a tiny floor so it
can never round down to nothing. We even test all of this with a special mode
that runs the full flow without spending real money, so we can prove the numbers
before anyone is charged.

We are open about the fact that we found and fixed real bugs here while building,
including one where streamed answers could be counted twice. We would rather tell
you that we go looking for these things than pretend they never happen.

---

## 7. The free trial

Every new account gets a daily free allowance for the first three months, and no
card is needed to start. This lets someone try real models, and even build
against the interface, before spending anything.

The trial is honest about its edges. Some models are marked free, and during your
trial they cost you nothing. Once your daily allowance is used up, or the three
month window ends, requests draw from your balance like anything else, including
those free models. If you have no credit at that point, we tell you clearly to
add some. The free allowance is a real welcome, not an unlimited promise dressed
up as one.

An administrator can adjust the daily allowance, so the welcome can grow or shrink
as the business learns what is sustainable.

---

## 8. Bring your own key, and earning from it

This is the part that makes SilkLLM more than a convenience layer.

If you already pay a provider directly, you can deposit your own key with us. You
choose how it is used.

If you keep it private, only you are served through it, and you pay a slightly
higher markup for the convenience of your own dedicated key.

If you make it public, our routing can use it to serve other people when it fits,
and here is the interesting part: you earn seventy five percent of the provider
cost of those requests as credit on our platform. Your idle allowance stops being
idle. It quietly works for you.

A few things make this safe and fair. Your key is never shown to another user.
Only our routing and an administrator can ever use it. The system spreads work
across public keys fairly, so no single owner is favored and no single key is
drained. There are limits on how many keys one person can deposit and how much a
key can be used per day. A key that keeps failing is suspended automatically. And
if you would rather keep your public key earning while you personally get served
elsewhere, you can ask to be treated as if you had deposited no key at all.

Owners earn credit, not cash. That credit spends like any balance. We chose this
because it keeps the money inside the system simple and honest, and it rewards the
people who make the marketplace work.

---

## 9. More than text: images, voice, and video

SilkLLM started with text, but it now covers several kinds of work through the
same one key and the same one balance.

Text, with the ability to include an image in your question. You can upload a
picture and ask a model about it. This is often called vision.

Image generation, where you describe something in words and get a picture back,
and you pay per image.

Voice, which is the richest of the set. You can turn text into natural speech and
choose the speaker. You can adjust how the voice sounds along a few simple dials,
like how steady or how expressive it is. You can take an existing recording and
convert it into another voice. And you can create a new voice by giving a few
audio samples, which is called voice cloning. The voice work runs through
ElevenLabs, a company that specializes in it, and it is billed by the amount of
text or the length of audio.

Video generation, where a provider supports it, billed by the second.

The important design point is that all of these go through the same routing, the
same billing, and the same bring your own key marketplace underneath. Adding a
new provider or a new model is a change to our catalogue, not a rewrite of your
app.

---

## 10. The chat, and why your data stays yours

Alongside the interface for developers, there is a full chat you can use in the
browser, and it is built on an unusual promise: your conversations live on your
own device, not on our servers.

You choose how long a chat is kept before it clears itself. We store no chat
content at all. The only thing we record is the usage information needed to bill
correctly, like how many tokens a request used and what it cost.

The chat is meant to feel like the tools people already know. Every message has
simple actions to copy it, edit it, or ask for a fresh answer. You can attach an
image and ask about it. You can generate images and speech right inside the
conversation, and download anything you make. You can even convert or clone a
voice from the same place.

Because everything lives in your browser, space is finite, so we show a small
gauge of how much you are using and, if it ever fills up, we clear the oldest
chats first so you can keep going without losing your recent work.

---

## 11. Building on top of it

For people who write software, there are ready made tools for two of the most
common languages, Python and JavaScript. They both cover the same features, so a
team is not forced into one stack. A few lines of code get you a text answer, a
streamed answer, a generated image, a spoken voice, a cloned voice, or a look at
your balance and history.

The documentation is written to be read, not endured. It shows short, practical
examples side by side in both languages, and there is a dedicated examples page
that walks through nearly every feature.

For those who prefer not to write code at all, the dashboard and chat cover the
same ground through a normal web interface.

---

## 12. Paying, wherever you are

Money can go in through Stripe, which is common worldwide, and through Paystack,
which is common across Africa. The goal is that where you live should not decide
whether you can pay for artificial intelligence. This matters more than it sounds,
because access to these tools is uneven, and a payment method is often the quiet
reason someone is left out.

---

## 13. Safety and control

A system that holds other people's keys and other people's money has to take
safety seriously from the start, not later.

Every deposited provider key is encrypted before it is stored, and it is never
handed back to anyone, not even its owner. We only ever use it to serve requests.

There are emergency switches that only an administrator can use. With them, all
generation can be paused, the marketplace can be frozen, earnings can be held, and
trials can be paused, all at once and immediately, if something ever looks wrong.
We built these before we strictly needed them, because the time to install a fire
alarm is not during the fire.

Important actions are written to an audit trail. Access is checked so one user can
never reach another user's data. And in the live environment, we fail loudly and
safely rather than guessing, because a quiet wrong guess about money or secrets is
the most expensive kind of mistake.

---

## 14. Keeping the lights on

The system watches the balances of the underlying providers on a schedule, and it
can send an alert when one is running low, so the people who keep it funded are
never caught by surprise. This is the boring, essential work that keeps a service
dependable rather than occasionally embarrassing.

---

## 15. What we have actually built so far

This is not a plan on paper. Here is what is real and running today.

A working gateway that routes requests to many providers through one key, with
automatic fallback when a model fails.

A catalogue of dozens of models across the major providers, plus free tier
backends and a dedicated voice provider, all kept in sync so an administrator only
has to maintain keys, not hand enter every model.

The full money path: real cost plus a small markup, cost shown on every request,
a permanent account history, charged exactly once, correct under load, tested
without spending real money, and honest about free versus paid.

A three month free trial with a daily allowance, enforced at the gateway so it
works through the interface and the code tools alike, and adjustable by an
administrator.

The bring your own key marketplace: deposit, public or private, seventy five
percent earnings on public keys used by others, fair rotation, caps, automatic
suspension of failing keys, keys never visible to other users, and the option to
be served as if you had no key.

Multiple kinds of output and input: text with image questions, image generation,
the full voice set including speaker choice, voice settings, voice conversion, and
voice cloning, and video where supported.

A local first chat with message actions, in chat generation of images and voice,
image attachments, downloads, and its own storage management.

User and administrator dashboards, including full control over models, providers,
the marketplace, settings, credits, alerts, and the emergency switches.

Ready made tools for Python and JavaScript, documentation with examples in both,
and payment through Stripe and Paystack.

A public website and landing page at getsilkllm.com that tells this story.

---

## 16. How the business makes money

The model is simple on purpose. We take a small markup on real usage, around ten
percent by default. When someone shares a public key and others use it, that
owner earns most of the provider cost back as credit, and the platform keeps a
small margin on top. There is no lock in and no forced subscription. People pay
for what they use, and they can leave whenever they like, which we think is the
right kind of pressure to keep us honest and useful.

---

## 17. Why this matters, and where it goes

The number of good artificial intelligence models is growing, and no single one
wins every task. That is genuinely good for the people building things, but only
if someone smooths over the mess of many accounts, many keys, and many bills.
That is the job SilkLLM has taken.

The honest version of the road ahead is about direction and values rather than
promises with dates. More models and providers as they arrive, without breaking
anyone's setup. Deeper support for the kinds of work people actually do. And a
steady commitment to two things that are easy to say and hard to keep: get the
money exactly right, and stay neutral so the buyer, not the biggest vendor, holds
the power.

---

## 18. The shortest possible summary

One key. One bill. Every model. Start free, share a key and earn if you want, keep
your chats on your own device, and always know what a request costs.

If you want to see it, it is at getsilkllm.com.
