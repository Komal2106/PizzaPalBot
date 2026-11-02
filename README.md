# PizzaPal Bot

A chat-based pizza ordering prototype. Instead of filling in a form, the customer talks to a bot that asks for the size, crust, toppings and delivery address one step at a time.

**Live demo:** https://komal2106.github.io/PizzaPalBot/

Built for **BTH745 – Human-Computer Interaction** (Seneca Polytechnic) as the *conversational interface* prototype in a study of five different ways to order the same pizza.

---

## Why this exists

The course project compares five interaction paradigms for one task, ordering a customised pizza for delivery. This repository is the conversational one.

| | |
|---|---|
| **Paradigm** | Conversational interface (natural-language flow) |
| **Good for** | People used to messaging apps, and anyone who prefers to be guided step by step |
| **Trade-off** | Needs sensible handling of unexpected input, and is slower than a form for someone who knows exactly what they want |

The prototype is built to be tested with real users. It is not a real ordering system.

## What it does

- **Guided order flow:** size, crust, toppings, name, delivery address, then an order summary to confirm or modify.
- **Quick-reply buttons or typing:** size and crust can be tapped or typed ("large", "thin and crispy"). Anything the bot can't understand gets a clear error and the question is asked again.
- **Address checking:** the bot accepts only delivery addresses it knows. Anything else gets *"Sorry, that's not a valid address in our Brampton delivery area"* and the question is asked again. Typos get a "Did you mean…?" suggestion, and the city and postal code are filled in automatically once the address is found.
- **Topping pricing:** the first 3 toppings are included. Each extra topping costs more, and premium toppings (marked ★) cost double. The extra charge updates live and appears in the summary.
- **Modify before confirming:** change the size, crust, toppings or address without starting over.
- **Tester tools:** an **Addresses** button lists the valid addresses and shows live counts of bot turns, errors and invalid address attempts. **Restart** resets the chat for the next participant.
- **Responsive:** works on phones, tablets and desktop, in light and dark mode.

## Ordering rules

| Item | Price (CAD) |
|---|---|
| Small / Medium / Large | $8.99 / $11.99 / $14.99 |
| Gluten-Free crust | +$1.50 (Hand-Tossed and Thin & Crispy are free) |
| First 3 toppings | Included |
| Each extra topping | +$0.30 |
| Each extra premium topping (★) | +$0.60 |

- 17 toppings to choose from. Premium: Extra Cheese, Feta, Mushroom, Bacon, Chicken, Artichokes.
- Extra charges apply to toppings in the order they were picked, after the first 3.
- Extra Cheese is not available on Large pizzas.
- Typing `cancel` cancels the order. Typing `reset` clears the pizza choices but keeps the address.

## Address checking (the mock backend)

There is no server. `js/addresses.js` holds **50 fictional addresses in Brampton, ON** and a small checker that:

- ignores capitalisation, punctuation and extras like "Brampton, ON" or a postal code
- treats `St`/`Street`, `N`/`North` and similar as the same thing
- suggests the closest address when the input is within a couple of typos

The street names are real Brampton streets, but the house numbers and postal codes are made up for testing.

## Running it

No install or build step.

1. Download or clone this repository.
2. Open `index.html` in any browser.

To publish it, use GitHub Pages (Settings → Pages → Deploy from a branch → `main` / root).

## Project structure

```
index.html        Page structure
css/style.css     Styling, responsive layout, light and dark theme
js/addresses.js   Mock backend: the 50 valid addresses and the address checker
js/app.js         Chat flow, topping pricing, order summary, error handling
```

## Changing things

| To change | Edit |
|---|---|
| Valid addresses | `ROWS` list in `js/addresses.js` |
| Included toppings and extra prices | `INCLUDED_TOPPINGS`, `EXTRA_STANDARD`, `EXTRA_PREMIUM` at the top of `js/app.js` |
| Toppings and which are premium | `TOPPINGS` and `PREMIUM_TOPPINGS` in `js/app.js` |
| Sizes and crusts | `SIZES` and `CRUSTS` in `js/app.js` |

## Usability testing

The prototype supports the metrics planned for the study:

- **Conversational efficiency:** number of bot turns to complete an order (shown in the Addresses panel)
- **Error rate:** unrecognised inputs and invalid addresses (shown in the Addresses panel)
- **Perceived naturalness:** collected from participants after the task

## Limitations

- Prototype only. Confirming an order shows a made-up order number and delivery time. Nothing is sent or stored, and there is no payment.
- Understanding is simple keyword matching, not real language understanding. Toppings and the final confirmation use buttons.
- Only the 50 listed addresses are accepted.

## Tech

HTML, CSS and plain JavaScript. No frameworks, libraries or build tools. Fonts (Baloo 2 and Figtree) load from Google Fonts, and the page falls back to system fonts when offline.

## Author

Mankomal Kaur Gandhara, BTH745 Human-Computer Interaction, Seneca Polytechnic.