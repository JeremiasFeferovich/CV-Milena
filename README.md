# CV - Milena Sol Feferovich

## Export to PDF

Requires Node.js and Puppeteer.

```bash
# Install puppeteer (first time only)
npm install puppeteer

# Generate PDF
NODE_PATH=./node_modules node -e "
const puppeteer = require('puppeteer');
(async () => {
  const browser = await puppeteer.launch({ headless: true, args: ['--no-sandbox'] });
  const page = await browser.newPage();
  await page.goto('file://$(pwd)/cv.html', { waitUntil: 'networkidle0' });
  await page.pdf({
    path: 'cv.pdf',
    format: 'A4',
    printBackground: true,
    margin: { top: 0, right: 0, bottom: 0, left: 0 }
  });
  await browser.close();
  console.log('cv.pdf generated');
})();
"
```
