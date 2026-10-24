# Currency Converter Web Application

A lightweight, responsive web application that performs real-time currency conversions using live exchange rates from the [ExchangeRate-API](https://www.exchangerate-api.com/).

---

## 🛠️ Built With (Tech Stack)

This project is built using standard front-end web development technologies:

- **HTML5**: Defines the structural skeleton of the currency converter interface (form inputs, dropdown select lists, action buttons, and result displays).
- **CSS3**: Styles the user interface with clean layout formatting, modern color schemes, responsive positioning, and hover states.
- **JavaScript (ES6+)**: Handles dynamic behavior, asynchronous API requests (`async/await`), DOM manipulation, input validation, and real-time conversion calculations.

## 🌟 Key Features

- **Dynamic Currency Dropdowns**: Automatically fetches and populates available currency codes (`USD`, `EUR`, `GBP`, etc.) into HTML dropdown select menus upon page load.
- **Real-Time Exchange Rates**: Pulls live exchange rate data based on the selected base currency.
- **Instant Calculation**: Computes accurate conversion values formatted to 3 decimal places.
- **Validation & Prevention**: Validates numeric input to prevent negative value calculations and suppresses default form page reloads using `e.preventDefault()`.

## 📂 Expected Project File Structure

text
index.html # Structural markup for the user interface
style.css # Stylesheet for custom layout and visual design
script.js # Asynchronous JavaScript logic & API integration

## 📋 HTML & JavaScript Element Mapping

To ensure the JavaScript functions correctly, the DOM elements in `index.html` must match these target IDs:

Element Type Required HTML ID Purpose

`<form>` `Converter-form` Form container listening for the submission event.  
`<select>` `from-currency` Dropdown menu for selecting the source currency.  
`<select>` `to-currency` Dropdown menu for selecting the target currency.  
`<input>` `amount` Number input field where users enter the value to convert.  
`<div>` `result` Output container displaying the final calculated conversion.

---

## ⚙️ How the JavaScript Code Works

1. **`fetchCurrencies()`**:
   - Fires automatically when the browser window finishes loading (`window.onload`).
   - Fetches baseline currency data from `https://api.exchangerate-api.com/v4/latest/USD`.
   - Iterates through the returned currency keys (`Object.keys(data.rates)`) and dynamically appends `<option>` elements to both `#from-currency` and `#to-currency` select dropdowns.

2. **`convertCurrency(e)`**:
   - Listens for the `submit` event on `#Converter-form`.
   - Cancels the default form page reload via `e.preventDefault()`.
   - Parses and validates the numeric input value.
   - Performs an asynchronous GET request to fetch rates relative to the selected `fromCurrencyValue`.
   - Calculates `amount * rate` formatted to three decimal places (`.toFixed(3)`) and renders the message inside `#result`.

---

## 🚀 How to Run Locally

1. Clone or download this repository to your local machine.
2. Ensure `index.html`, `style.css`, and `script.js` reside in the same folder.
3. Verify that `index.html` links your CSS stylesheet and JavaScript file correctly:

   ```html
   <link rel="stylesheet" href="style.css" />
   <script src="script.js" defer></script>
   ```

4. Open `index.html` in any web browser or launch it using a local server extension (such as Live Server in VS Code).

## 📡 API Reference

This application uses the open exchange rate endpoint:

- `GET https://api.exchangerate-api.com/v4/latest/{BASE_CURRENCY}`

---
