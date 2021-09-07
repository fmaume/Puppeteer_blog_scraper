# Puppeteer_blog_scraper
Small web scraper to extract the content of a blog post.

## Code to extract text from dev console
```
let stemp = document.querySelector('p + p + p')
            stemp = stemp.parentElement
            stemp = stemp.children
            let result = []
            for (let element  of stemp) {
                let text = element.innerText
                let type = element.tagName
                if (text.length > 0) {
                    result.push({ "text": text, "type": type })
                }

            }
copy(result)
```

## Puppeter code to scape a blog post
```
const puppeteer = require('puppeteer');
(async () => {
      const browser = await puppeteer.launch();
      const page = await browser.newPage();
      await page.goto('https://example.com');
      let blogText = await page.evaluate(() => {
            
            let stemp = document.querySelector('p + p + p')
            stemp = stemp.parentElement
            stemp = stemp.children
            let result = []
            for (let element  of stemp) {
                let text = element.innerText
                let type = element.tagName
                if (text.length > 0) {
                    result.push({ "text": text, "type": type })
                }

            }
            
       
            return result;


        })
})();
```
