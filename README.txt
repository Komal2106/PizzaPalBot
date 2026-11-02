PizzaPal Bot (BTH745 Prototype 5: conversational interface)

HOW TO RUN
  Double-click index.html. It opens in any browser. No install, no server.
  (An internet connection is only used for the two Google fonts; without it the page uses system fonts.)

FILES
  index.html          Page structure (header, chat log, message box, tester panel)
  css/style.css       All styling, light and dark theme
  js/addresses.js     Mock backend: the 50 valid Brampton addresses and the address checker
  js/app.js           Chat flow, topping pricing, order summary, error handling

THINGS YOU MAY WANT TO CHANGE
  Valid addresses     js/addresses.js, the ROWS list: [house number, street, postal code]
  Topping prices      js/app.js, near the top: INCLUDED_TOPPINGS (3), EXTRA_STANDARD (0.30), EXTRA_PREMIUM (0.60)
  Premium toppings    js/app.js, PREMIUM_TOPPINGS list (shown with a star in the chat)
  Pizza sizes/prices  js/app.js, the SIZES list
  Crusts              js/app.js, the CRUSTS list

FOR TESTING
  "Addresses" button (top right) lists the 50 valid addresses and shows live counts of bot turns,
  errors and invalid addresses. "Restart" resets the chat for the next tester.
  Typing "cancel" cancels the order; "reset" clears the pizza choices but keeps the address.
