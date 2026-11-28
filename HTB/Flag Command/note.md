# Welcome to the Flag Command Box

**Difficulty:** Easy  
**Category:** Web Exploitation  
**Type:** CTF

This is an easy-level Web Exploitation CTF challenge.

When I started exploring the box, I had a general idea of how to approach easy-level web challenges. However, instead of randomly trying things, I followed a checklist to keep my methodology structured and avoid missing anything important.

## My Methodology

Before jumping into exploitation, I follow a basic checklist:

1. **Explore the website:** Navigate through the application like a normal user and understand how it works.
2. **Enumerate pages and endpoints:** Visit every available page, inspect endpoints, and identify all input fields.
3. **Inspect network traffic:** Check the browser's Network tab. Look for interesting requests, responses, headers, parameters, or anything that could potentially be manipulated.
4. **Test input fields:** Check for common vulnerabilities such as XSS and SQL Injection.
5. **Explore directories and JavaScript files:** Enumerate accessible directories and inspect the website's JavaScript files for useful information.
6. **Identify the technology stack:** Determine which technologies and versions the website uses. Check whether any outdated components have known CVEs.

With that checklist in mind, let's get started.

## First Step — Exploring the Website

I started by interacting with the website like a normal user to understand its functionality.

The website presented itself as a terminal-like interface where I had to find the correct combination of tasks to obtain the flag.

Initially, I considered solving it by manually figuring out the correct combination. However, that approach could take a considerable amount of time.

I decided to keep brute-forcing as a last resort. If nothing else worked, I would consider it as an alternative.

## Second Step — Inspecting the Page Source

Next, I checked the page source to see whether the flag or any useful information was exposed in the frontend.

I inspected the available HTML, CSS, and other source files, looking for hardcoded credentials, hidden values, comments, or anything that could reveal the flag.

Unfortunately, I didn't find anything useful here.

## Third Step — Inspecting Network Traffic

Since the page source didn't reveal anything interesting, I moved to the browser's Developer Tools and opened the **Network** tab.

I started inspecting the requests and responses exchanged between the browser and the server.

While examining the network traffic, I noticed something interesting in the response to an `OPTIONS` request: it contained a secret key.

<details>
<summary>Evidence — ./response.png</summary>

The response containing the suspicious secret key is saved in `response.png`.

</details>

That immediately caught my attention.

I copied the key and tried pasting it directly into the terminal. However, it didn't work.

After experimenting a little, I decided to type `start` first and then paste the key.

And boom! **The flag appeared!**

<details>
<summary>Evidence — ./found.png</summary>

The successful output containing the flag is saved in `found.png`.

</details>

## Conclusion

This challenge was a good reminder that web exploitation isn't always about finding complicated vulnerabilities or writing elaborate payloads.

Sometimes, the most valuable information is hiding in plain sight — in this case, inside an HTTP response.

The key takeaway: **Never ignore network traffic.** Always inspect requests and responses carefully, because the frontend might not reveal everything the backend is communicating.

**Challenge completed.**
