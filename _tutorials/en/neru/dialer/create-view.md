---
title: Create a HTML View
description: In this step you learn how to create a HTML view for your project.
---

# Create a HTML View

To enter the phone number you want to be called you'll need to create a HTML form. In your terminal create a views folder and add the `index.html` file:

```sh
mkdir views
touch views/index.html
```

Open `index.html` in your text editor and add the HTML form:

```html
<!DOCTYPE html>
<html lang = "en">
  <head>
    <meta charset = "UTF-8">
    <link rel="stylesheet" href="style.css">
    <title> NeRu Dialer </title>
  </head>
  <body>
    <p> Enter a phone number to receive a call from NeRu</p>
    <form method="POST" action="call">
      <label for="number">Number:</label><br>
      <input type="text" id="number" name="number"><br>
      <input type="submit" value="Submit">
    </form>
  </body>
</html>
```

The form has one input for the phone number to be entered and a submit button. Once submitted it will make a POST request to `/call` on the server.

## Static Files

The form uses a CSS file for some styling. Serving static files is a two part process. First, create a public folder and the CSS file:

```sh
mkdir public
touch public/style.css
```

The second part of serving static files happens in the server code.

## Serve the Site

To expose your `public` folder add the following to your `index.html` file:

```javascript
const __filename = fileURLToPath(import.meta.url);
const __dirname = path.dirname(__filename);
router.use(express.static(path.join(__dirname, 'public')))
```

Anything you add to the public folder will be available at the root of the website. For example, the CSS file can be access by `/style.css`.

To have the view visible when you visit your website, you will need to render it. Add the following to the `index.js` file:

```javascript
router.get('/', async (req, res) => {
    res.sendFile('views/index.html', { root: '.' });
});

export { router };
```

This will return the HTML file as the root page of the website. Now if you start the NeRu debugger for your project you can view the webpage:

```sh
neru debug --name dialer
```

Your URL will be in this format

```sh
# https://api-eu.vonage.com/v1/neru/i/neru-abcd1234-debug-dialer/
https://api-$REGION.vonage.com/v1/neru/i/neru-$APIKEY-debug-dialer/
```

![The HTML form](/images/neru/neru-dialer-view.png)