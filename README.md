# Max Loan Qualification Calculator

A modern, responsive web app to estimate the maximum loan amount you can qualify for based on your financial details. Results are displayed instantly and can be recorded to a connected Google Sheet for tracking and analysis.

---

## 🚀 Features

- User-friendly form for personal and financial details
- Dynamic calculation of DSR, max instalment, and max loan
- Instant results with a modern, responsive UI (Tailwind CSS)
- Google Sheets integration for automatic recording
- Form reset/clear functionality
- Dark mode support

---

## 🖥️ Usage

1. **Open the Calculator**
   - Open `index.html` in your web browser.

2. **Fill in the Form**
   - **Nama**: Your name
   - **Phone Number**: Your contact number
   - **Email**: Your email address
   - **Gaji Bersih (RM)**: Net monthly income (MYR)
   - **Komitmen (RM)**: Existing monthly commitments
   - **Interest Rate (%)**: Annual interest rate (default: 4.1%)
   - **Loan Term (Years)**: Loan term in years (default: 35)

3. **Calculate & Record**
   - Click **"Calculate & Record"**
   - Results will appear on the right
   - Calculation is sent to Google Sheets (if integration is set up)

4. **Clear the Form**
   - Click **"Clear"** to reset all fields and results

---

## 🧮 Calculation Logic

- **DSR Used**:
  - Net income < RM 3,000: DSR = 60%
  - Net income < RM 5,000: DSR = 70%
  - Net income < RM 7,000: DSR = 75%
  - Otherwise: DSR = 80%

- **Max Instalment**:
  ```
  Max Instalment = (Net Income × DSR) - Komitmen
  ```

- **Max Loan**:
  ```
  Max Loan = Max Instalment × [(1 + r)^n - 1] / [r × (1 + r)^n]
  where:
    r = monthly interest rate (annual rate / 12)
    n = total number of payments (years × 12)
  ```

---

## 📊 Google Sheets Integration

- Each calculation is POSTed to a Google Apps Script Web App URL.
- **To enable recording:**
  1. Deploy your own Google Apps Script as a Web App ([docs](https://developers.google.com/apps-script/guides/web)).
  2. Replace the `scriptURL` in the JavaScript section of `index.html` with your Web App URL.
  3. The script records: Timestamp, Name, Phone, Email, Net Income, Commitments, DSR Used, Max Instalment, Max Loan, Interest Rate, Loan Term.

---

## 🎨 Customization

- **Styling**: Uses [Tailwind CSS](https://tailwindcss.com/) and Inter font
- **Validation**: All fields required and validated
- **Dark Mode**: Adapts to system theme

---

## 🛠️ Troubleshooting

- **Calculation not recorded?**
  - Check your internet connection
  - Ensure the Google Apps Script URL is correct and deployed as a Web App with permissions
- **Form not working?**
  - Make sure JavaScript is enabled
  - Check browser console for errors

---

## 📁 File Structure

```
Loan-Calculator docs/
  ├── index.html   # Main app (UI + logic)
  └── README.md    # This documentation
```

---

## Support & Contact

For technical support or questions about this Max Loan Qualification Calculator system, please contact your system administrator or the development team.

**Version**: 1.0  
**Last Updated**: January 2024  
**Maintained By**: RBX Development Team 