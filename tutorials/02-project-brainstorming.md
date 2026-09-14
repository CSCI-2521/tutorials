# Brainstorming project ideas
## Web Apps vs Apps
In this class you will be making a web app. This means it runs directly from a web browser. However, on Android phones and iPhones it is usually possible to make a web app that you can save to your home screen so that it works like an app, with some limitations.

Here is a comparison of Web Apps, Mobile Apps, and Desktop Apps.

|  | Web App | Mobile App | Desktop App |
| --- | --- | --- | --- |
| Runs on | Browser | Phone/tablet (iOS, Android) | Windows, Mac, Linux |
| Install | None, just a URL | App store download and install | Download and install |
| Updates | Instant, server side | Through the app store | Manual or auto updater |
| Access to hardware | Limited (camera, GPS with permission) | Full (camera, GPS, push, sensors) | Full (files, peripherals) |
| Works offline | Rarely | Sometimes | Sometimes |
| Runs on phone like an app | Usually, with limited capabilities | Yes | N/A |
| Built with | HTML, CSS, JavaScript | Swift, Kotlin, or cross-platform tools | C#, Electron, Python, etc. |
| Examples | Google Docs, Gmail | Instagram, Uber | VS Code, Photoshop |

## Client Side vs Server Side Apps

Every web app has two possible homes for its code: the browser (client side) or a server somewhere else (server side). Most real apps use both, but it helps to understand each one on its own.

### Client Side Apps

The code is downloaded to your browser and runs there. Your laptop or phone does the actual work. After the page loads, it can keep running even with no connection.

**Toy examples:**
- A tip calculator built with plain HTML and JavaScript
- A to-do list that saves items in the browser's local storage
- A PDF compressor that does all the work locally inside the browser for privacy

**Bigger examples:**
- Google Docs Offline (typing, formatting, and menus all run in your browser when you are offline)
- Figma (a full design tool running on the client, with a server syncing your files, although much of the work is done server side still)

### Server Side Apps

The code runs on a remote server. Your browser just sends requests and displays whatever HTML or data comes back. The server holds the logic, the database, and any secrets like API keys.

**Toy examples:**
- A guestbook where anyone can post a message and it shows up for everyone (messages stored in a server database)
- A random joke service: you visit a website and enter a topic. The server sends the topic to an LLM service to generate a joke and sends it back
- A weather dashboard that fetches data from a public API that *does not* require an API key.

**Bigger examples:**
- Amazon (product searches, carts, and orders are all handled by servers)
- Netflix (the server decides which shows you see, and streams the video to the browser)
- Your bank's website (account logic and balances must live on a server, never in the browser)
- A weather dashboard that fetches data from a public API that *does* require an API key

### Most apps are both

Most apps will use a combination of client-side code and server side code. They use the client for things that need to feel instant: clicks, animations, typing. They use the server for things that need to be shared, stored, or kept secret: databases, payments, API keys, and anything another user should see. A "full stack" app is both of these working together.

## Data sources

Most apps will require getting data from somewhere. There are many free services on the internet called "application programming interfaces" (APIs) that offer useful data. These pages and repositories contain lists of may of these services. You can use this as inspiration for an app idea, or to track down specific data that you need. Warning: not all APIs listed will still be valid. Be sure to click through and check that an API works.

| Repository | Link | Notes |
| --- | --- | --- |
| public-apis/public-apis | https://github.com/public-apis/public-apis | The classic list — hundreds of APIs by category. Archived but still the most famous. |
| marcelscruz/public-apis | https://github.com/marcelscruz/public-apis | Community-maintained fork, still updated, same format. |
| keploy/public-apis-collection | https://github.com/keploy/public-apis-collection | Includes difficulty ratings; dev/testing-focused APIs. |
| n0shake/Public-APIs | https://github.com/n0shake/Public-APIs | Well-curated categorized list. |
| MarkoDenic/public-apis | https://github.com/MarkoDenic/public-apis | Clean, hand-picked selection (public-apis.dev). |
| ripienaar/free-for-dev | https://github.com/ripienaar/free-for-dev | Free-tier services broadly — not just data APIs. |
