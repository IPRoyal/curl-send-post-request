# How to Send a cURL POST Request

<a href="https://iproyal.com/proxies/">
  <img width="2180" height="550" alt="GitHub Banner"
       src="https://github.com/user-attachments/assets/c857fdbc-882d-4089-af87-cfa93408311d"></img>
</a>

**cURL** is a command-line utility used to send requests to a server. It’s pre-installed on most modern operating systems and is widely used for networking and automation.

While GUI tools such as Postman offer a visual interface, **cURL** provides a more direct, reliable, and low-level approach that’s great for scripting and backend tasks.

---

## Getting Started With cURL

cURL is included by default in:
- **Windows 10+**
- **macOS**
- Some **Linux** distributions

If you don’t have it installed, you can run:

```bash
sudo apt-get install curl
```

For older Windows versions, download cURL from the [official website](https://curl.se/download.html).  
After installation, verify everything works with:

```bash
curl --help
```

> On Windows, use **Command Prompt** rather than PowerShell, as syntax handling differs.

---

## Sending a cURL POST Request

Every cURL request follows this pattern:

```bash
curl [request options] [URL] [other options]
```

For a POST request, three elements are required:

1. `-X POST` — specifies the HTTP request method.  
2. `-d` — defines the data to send.  
3. `URL` — the target endpoint.

### Example: Basic POST Request

```bash
curl -X POST https://reqbin.com/echo/post/json -d "YOUR_STRING"
```

### Example: Sending JSON Data

```bash
curl -X POST https://reqbin.com/echo/post/json -d '{"KEY":"VALUE", "KEY2":"VALUE2"}'
```

---

## Advanced POST Request Settings

Some APIs require more parameters or authentication.

### Adding Headers

```bash
curl -X POST https://reqbin.com/echo/post/json -d "YOUR_STRING" -H "Content-Type: application/json"
```

Multiple headers can be included:

```bash
curl -X POST https://reqbin.com/echo/post/json   -d '{"KEY":"VALUE", "KEY2":"VALUE2"}'   -H "Content-Type: application/json"   -H "Accept-Charset: utf-8"
```

### Authentication Options

**Username and Password:**

```bash
curl --user "USERNAME:PASSWORD"   -X POST https://reqbin.com/echo/post/json   -d '{"KEY":"VALUE", "KEY2":"VALUE2"}'   -H "Content-Type: application/json"
```

**API Token Header:**

```bash
curl -X POST https://reqbin.com/echo/post/json   -d '{"KEY":"VALUE", "KEY2":"VALUE2"}'   -H "Content-Type: application/json"   -H "API-Access-Token: YOUR_TOKEN"
```

### Uploading Data From a File

```bash
curl -F "data=@path/to/local/file" https://reqbin.com/echo/post/json
```

---

## Error Handling

When errors occur, cURL displays them in the terminal. For example:

**Example 1:** Sending a POST request without data:
```
<title>Error 411 (Length Required)!!1</title>
<p>POST requests require a <code>Content-length</code> header.</p>
```

**Example 2:** Sending data to an invalid endpoint:
```
<title>Error 405 (Method Not Allowed)!!1</title>
<p>The request method <code>--POST</code> is inappropriate for the URL <code>/</code>.</p>
```

Some APIs return generic HTTP errors, while others return custom messages explaining what to adjust.

---

## Wrapping Up

Most APIs require these parameters in a POST request:
- Authentication (`--user` or header token)
- Data payload (`-d`)
- Content-Type header
- Target endpoint URL

Example:

```bash
curl --user "USERNAME:PASSWORD"   -X POST https://reqbin.com/echo/post/json   -d '{"KEY":"VALUE", "KEY2":"VALUE2"}'   -H "Content-Type: application/json"
```

For more options, refer to [cURL documentation](https://curl.se/docs/manpage.html).
