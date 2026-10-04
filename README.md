# 9proxy download: getting the official client on Windows, macOS, and phones without picking up malware

Most people typing "9proxy download" into a search bar are trying to solve one problem: get the proxy client installed, sign in, and start using IPs. That's a five-minute job — *if* you get the installer from the right place.

The place where it tends to go sideways is mobile. Search results for "9Proxy APK" point at third-party download mirrors, and those files are not the vendor's build. So this guide covers the actual download paths, the system requirements nobody reads until the install fails, and what the client is even for — because on 9Proxy, one of the three product lines doesn't need a download at all.

## Three things you might be downloading, and only one of them is a normal app

Before you click anything, it helps to know which component you actually need, because 9Proxy ships more than one.

**The 9Proxy desktop app** is the main client. It runs on Windows, macOS and Linux, and it's mandatory if you bought a plan under the Residential Proxy by IPs model. That product works through local port forwarding: you pick an IP, forward it to a port on your machine, and your tools talk to `localhost:port`. Without the app installed, that model does nothing.

**The web dashboard** is where the Residential Proxy by GB model lives. You generate endpoints from the browser, authenticate with username/password or an IP whitelist, and there's nothing to install. If your workflow is request-level rotation — scraping endpoints, ad verification, geo-checks — you can skip the download entirely and work from the dashboard.

**ProxyHub** splits into two pieces. ProxyHub Pro is built into the desktop app and manages devices from your computer. ProxyHub Lite runs on the phones themselves.

One more thing that determines whether the download is even useful: 9Proxy runs on a prepaid balance. You create the account first, add funds or a package, then log in with those same credentials inside the app. The client is a front end for your balance, not a standalone tool. So if you haven't registered yet, that's step one.

👉 [Create your 9Proxy account and get to the dashboard](https://bit.ly/9-Proxy)

## System requirements before you download

Install the wrong build and you'll get an error that says nothing useful. Check these first.

**Windows** — Windows 8, 8.1, 10 or 11, with a 64-bit build recommended. You'll want a 2 GHz CPU or faster, at least 4 GB of RAM, and 200 MB of free disk space. The standard installer wants administrator rights; the portable build mostly doesn't.

**macOS** — macOS 12 Monterey or later. Ventura and everything above it is fine. If you're still on macOS 11, the app won't run and there's no workaround — you update the OS or you don't use the client. Same 4 GB RAM and 200 MB disk floor.

Both platforms also need a stable connection during setup, because the app checks for updates.

## Installing on Windows: installer vs portable

9Proxy publishes two Windows builds, and the choice matters more than people expect.

The **installer** (`9proxy-windows-installer.exe`) is the standard route. Download it, right-click and choose *Run as administrator* so you don't hit permission errors partway through, accept the license, pick a directory (the default is `C:\Program Files\9Proxy`), decide whether you want a desktop shortcut, and click Install. When it finishes, the Finish button launches the app straight away. Log in with your 9Proxy credentials and you're in.

The **portable** build (`9proxy-windows-portable.zip`) suits locked-down machines. It doesn't touch the Windows registry and doesn't need admin rights for most things — system-wide proxy configuration is the exception. Extract the ZIP to a folder you control, then double-click `S9Proxy.App.exe`.

A note worth knowing before you pick: the installer and portable versions can coexist on the same machine, but they keep their settings separately and don't share configuration. The portable build does auto-update — it shows a notification when a new release lands, and one click pulls it down.

### When the Windows install goes wrong

Three failures come up repeatedly.

Windows SmartScreen flags the file. Click *More info*, then *Run anyway* — but only if you downloaded from 9Proxy's own site. A generic "download portal" copy of the same filename is a different risk entirely.

The app won't launch. Check for .NET Framework 4.7.2 or later. If system proxy configuration is failing, retry as administrator.

Nothing appears to happen at all. The app is often already running in the background — open Task Manager, find the existing `S9proxy.App` task, end it, and start again.

## Installing on macOS

Grab the `9proxy-macos.pkg` installer and run it like any other package. The docs list a PKG installer as the standard method, and modern macOS will warn you about an unidentified developer — that's Gatekeeper being Gatekeeper.

Once installed, open 9Proxy from Applications and sign in. If the install fails, the usual suspects are an unsupported macOS version (anything below 12) or insufficient free disk space. Support asks for a screenshot of the error if it persists, which is a reasonable thing to have ready.

You can sign in with the same account on multiple devices. The vendor's own guidance is to be careful about which devices you use, which is sensible advice for anything holding proxy credentials.

## The Android APK question — what's actually official

This is where most "9proxy download" traffic gets burned, so it's worth being precise.

Android builds do exist from 9Proxy, but they belong to **ProxyHub Lite**, the mobile half of the ProxyHub system, not to the desktop client. ProxyHub Lite ships as an APK and is installed manually — download it from 9Proxy's own source, open the file, and follow the prompts.

iOS is further behind. ProxyHub Lite on iPhone and iPad is distributed as a Developer Preview, which means sideloading an IPA through a tool like AltStore or Sideloadly on a computer. That's not a mainstream install path, and if you just want proxies on your phone, it's the wrong tool.

Both mobile paths share a requirement: you need a valid 9Proxy account, and you need to use the *same* account across devices, because ProxyHub Pro's whole purpose is managing those devices remotely from your desktop.

What you should not do is install an APK from a third-party download aggregator claiming to be "9Proxy." Off-brand mirrors for proxy apps are a well-worn malware delivery pattern, and the legitimate build is available from the vendor for free anyway. There's no upside to the risky copy.

## What the client does once it's running

Worth knowing before you install, so you can tell whether you bought the right product.

With **Residential Proxy by IPs**, the app is the control surface. You filter IPs by country, state, city, ZIP code or ISP, forward one to a port, and use it at `localhost:port`. An IP is only deducted from your balance when you forward it. Unused IPs sit in your balance indefinitely — they don't expire while they're parked. Once activated, an IP stays online for several hours up to roughly 24 hours, which varies naturally because these are real residential connections, not datacenter machines.

When an IP drops, two features handle it. **Auto Refresh Proxy** automatically replaces a dead IP with a fresh one. **Auto Rotation Proxy** rotates proxies on a schedule across selected ports. Both matter for anything long-running.

With **Residential Proxy by GB**, you're not managing individual IPs at all. You generate unlimited endpoints and only the data is metered. Rotation happens automatically — rotating mode switches IPs per request, sticky mode holds one until your configured session time expires.

Both models speak HTTP, HTTPS and SOCKS5. SOCKS5 support is the one to check for if you're running Scrapy, Puppeteer or Playwright, since those tools need transport-layer proxying rather than HTTP-only.

## Full plan list with current prices

9Proxy runs on a prepaid balance, so these are one-time package purchases rather than monthly subscriptions. The IP-based and bundle prices below reflect the adjustment 9Proxy applied from 1 June 2026; GB-based pricing stayed where it was. Your checkout total is the number that counts, so confirm it on the plan page before paying.

| Type | Package | Price | Effective rate | Validity | Get it |
| --- | --- | --- | --- | --- | --- |
| IP-based | 100 IPs | $24 | $0.24 / IP | IPs never expire until forwarded | [Buy the 100 IP pack](https://bit.ly/9-Proxy) |
| IP-based | 500 IPs | $72 | $0.144 / IP | IPs never expire until forwarded | [Buy the 500 IP pack](https://bit.ly/9-Proxy) |
| IP-based | 1,000 IPs + 500 bonus | $126 | $0.084 / IP | IPs never expire until forwarded | [Buy the 1,000 + 500 IP pack](https://bit.ly/9-Proxy) |
| IP-based | 2,500 IPs | $210 | $0.084 / IP | IPs never expire until forwarded | [Buy the 2,500 IP pack](https://bit.ly/9-Proxy) |
| IP-based | 5,000 IPs | $360 | $0.072 / IP | IPs never expire until forwarded | [Buy the 5,000 IP pack](https://bit.ly/9-Proxy) |
| IP-based | 15,000 IPs | $720 | $0.048 / IP | IPs never expire until forwarded | [Buy the 15,000 IP pack](https://bit.ly/9-Proxy) |
| IP-based | 25,000 IPs | $863 | ~$0.035 / IP | IPs never expire until forwarded | [Buy the 25,000 IP pack](https://bit.ly/9-Proxy) |
| IP-based | 50,000 IPs | $1,438 | ~$0.029 / IP | IPs never expire until forwarded | [Buy the 50,000 IP pack](https://bit.ly/9-Proxy) |
| IP-based (business) | 100,000 IPs | $2,300 | $0.023 / IP | IPs never expire until forwarded | [Buy the 100,000 IP pack](https://bit.ly/9-Proxy) |
| IP-based (business) | 200,000 IPs | $4,140 | ~$0.021 / IP | IPs never expire until forwarded | [Buy the 200,000 IP pack](https://bit.ly/9-Proxy) |
| IP-based (business) | 500,000 IPs | $8,625 | ~$0.017 / IP | IPs never expire until forwarded | [Buy the 500,000 IP pack](https://bit.ly/9-Proxy) |
| GB-based | 5 GB | $15 | $3.00 / GB | 180 days | [Buy the 5 GB pack](https://bit.ly/9-Proxy) |
| GB-based | 50 GB + 5 GB bonus | $105 | $2.10 / GB | 180 days | [Buy the 50 + 5 GB pack](https://bit.ly/9-Proxy) |
| GB-based | 100 GB | $150 | $1.50 / GB | 180 days | [Buy the 100 GB pack](https://bit.ly/9-Proxy) |
| GB-based | 200 GB | $200 | $1.00 / GB | 180 days | [Buy the 200 GB pack](https://bit.ly/9-Proxy) |
| GB-based | 1,000 GB | $800 | $0.80 / GB | 180 days | [Buy the 1,000 GB pack](https://bit.ly/9-Proxy) |
| GB-based | 2,000 GB | $1,500 | $0.75 / GB | 180 days | [Buy the 2,000 GB pack](https://bit.ly/9-Proxy) |
| GB-based (enterprise) | 3,000 GB | $2,160 | $0.72 / GB | No expiry | [Buy the 3,000 GB pack](https://bit.ly/9-Proxy) |
| GB-based (enterprise) | 6,000 GB | $4,200 | $0.70 / GB | No expiry | [Buy the 6,000 GB pack](https://bit.ly/9-Proxy) |
| GB-based (enterprise) | 10,000 GB | $6,800 | $0.68 / GB | No expiry | [Buy the 10,000 GB pack](https://bit.ly/9-Proxy) |
| Bundle | Starter — 100 IPs + 5 GB | $30 | — | Traffic valid 180 days | [Buy the Starter bundle](https://bit.ly/9-Proxy) |
| Bundle | Popular — 1,500 IPs + 50 GB | $180 | — | Traffic valid 180 days | [Buy the Popular bundle](https://bit.ly/9-Proxy) |
| Bundle | Pro — 5,000 IPs + 500 GB | $720 | — | Traffic valid 180 days | [Buy the Pro bundle](https://bit.ly/9-Proxy) |

A few things the table doesn't show. The network advertises 20M+ residential IPs across 90+ countries with city, state and ISP-level targeting, and 99.95% uptime. Trials exist but are limited and depend on availability — you have to ask support, and you tell them whether you want an IP-based or GB-based trial.

## Which package fits your download

If you're here because you want a **desktop client doing actual work**, the IP-based side is your product, and the client is required. The 100-IP pack at $24 is genuinely a test-the-water purchase: forward a handful of IPs, run your workflow, see what the success rate looks like on your specific targets. The jump from 100 IPs to 1,000+500 is where the price per IP drops from $0.24 to $0.084, which is a big enough gap that buying 100 IPs repeatedly instead of one larger pack is a waste of money.

If you don't want to install anything, take GB-based. 5 GB for $15 is enough to measure whether the network behaves on your targets, and the 180-day window means an idle month doesn't burn the balance. The 10,000 GB enterprise tier at $0.68/GB is the only one with no expiry at all — for always-on infrastructure, that removes the deadline problem entirely.

Bundles are the awkward middle. The Starter bundle at $30 gives you 100 IPs and 5 GB for $6 more than the IP pack alone, which is close to free if you'll use the traffic. Pro at $720 versus $360 for 5,000 IPs plus $200 for 200 GB bought separately — the bundle only makes sense if the numbers line up for your actual mix.

👉 [Compare all 9Proxy packages and pick the one that fits](https://bit.ly/9-Proxy)

## Common problems after install

**The proxy list is empty.** You're either on a GB-based plan — which doesn't populate the IP list, because that product generates endpoints from the dashboard — or your IP balance is zero.

**An IP keeps dying.** That's residential behaviour, not a bug. Forwards last hours to about a day. Turn on Auto Refresh and stop watching it.

**It works in the app but not in your scraper.** Check the authentication mode. IP-based forwards through `localhost:port` and optionally uses proxy authentication; GB-based takes username/password or an IP whitelist. Mixing those up produces silent failures.

**The app updated and settings changed.** The installer and portable builds store configuration separately. If you switched builds, you started fresh.

**You bought access as a share code.** Activate it on your account first — the balance lands instantly, and then the client behaves normally.

## The short version

Windows and macOS clients, a Linux app, a browser-based dashboard for GB plans, and ProxyHub Lite on mobile. Download from 9Proxy directly, check your OS version first, and remember that the app is a controller for your balance rather than a free-standing tool — so register and pick a package before you start troubleshooting an install that was never going to show you anything.

👉 [Register for 9Proxy and download the client](https://bit.ly/9-Proxy)
