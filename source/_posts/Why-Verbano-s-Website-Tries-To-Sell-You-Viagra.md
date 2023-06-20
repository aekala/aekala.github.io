---
title: Why Verbano's Website Tries To Sell You Viagra
date: 2023-06-19 17:05:38
tags:
---

<link rel="stylesheet" href="/../css/post.css">

Verbano Ristorante Italiano in Honolulu, Hawaii, has served Sicilian and Tuscan-style Italian food in the Kaimuki area since 1992. Throughout the years, my family has gone there and enjoyed dinners sharing calamari, lasagna, and chicken parmigiana.
I've even recommended it to people back in Hawaii looking for a place to eat Italian food around Kaimuki, which brings us to how I found out about their website.

I recommended Verbano to a group of friends, and afterwards they told me the restaurant's website looked a bit strange.
I've seen plenty of restaurant websites with outdated designs, so I figured it was something along those lines. The font and background color for the website may be one that was popular in the 1990s, it may not be secured with HTTPS, or most commonly in my experience the design is not responsive to mobile devices so when you open it on your phone the page is all zoomed out and you have to zoom in to read it.

I searched for Verbano on Google expecting to see any of these reasons as what my friends were talking about. When I looked up Verbano Hawaii, I didn't see their website among the first several search results but saw the local listing feature on Google Search bring up a card on the right side with the restaurant's info.

<img src="/../images/verbano/local_listing_full_size.png" alt="Google search results for verbano hawaii" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">Google search results for "verbano hawaii"</p>

I clicked on the card's button labeled "website" to take me to the restaurant's webpage.
I saw my address bar show hawaiiverbano.com for a second before quickly changing to something along the lines of safe-it-phshop.com. I tried this several times and the domain name of the website I would get sent to cycled through a few different variations, but they were all effectively the same website. And instead of seeing a website advertising Italian food in Kaimuki, I was sent to a sketchy pharmaceutical website trying to sell me different kinds of Viagra.

<img src="/../images/verbano/viagra_website.png" alt="viagra website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">the Viagra site I got sent to</p>

Naturally, I was pretty shocked and thought this was what my friends were talking about. But when I brought it up to them they had no idea what I was talking about. They just thought the restaurant's website looked outdated, but after I told them to check it out from Google they got redirected to the same Viagra website I did.

So it was time to dig into this and see if I could figure out what was going on here.
The first thing I wanted to do was see if I could get to Verbano's actual website. My friends had been able to see it earlier, so clearly there was some way to get to it. I assumed the hawaiiverbano.com I saw before the address bar changed was the URL for their website, and hovering over the website link on the Google local listing card confirmed that.

So I now knew for sure that the URL for the website was hawaiiverbano.com, and after putting that into my address bar I was sent to the correct website. It had some of the hallmarks I was talking about earlier, with pixelated images and the content not scaling to account for my screen size but it undoubtly Verbano restaurant's real website.

<img src="/../images/verbano/normal_website.png" alt="verbano actual website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">Verbano's actual website</p>

From this and some additional testing, I confirmed you would get the Viagra site when accessing Verbano's site by clicking one of Google’s links, whether it was down the search result list or through the local listing card.
Whereas you would get Verbano's actual website by entering the URL into your search bar. Your web browser would then cache this webpage meaning you’ll get the actual website from now on even if you use the Google search result links.
You can test this by clearing your cache in your browser settings and seeing that you get the Viagra site again until you access the actual website via the address bar.

# SEO and Caching

I noticed some strange things about the search result on Google for Verbano's website. For one it was very low on the search results for "Verbano Hawaii" (it was often on the second or third page of results), indicating that the website had poor SEO (Search Engine Optimization), which is the practice of making your website friendly to search engines such as Google through a variety of methods to have your website rank higher in the search results.
What most stood out was the title and description for the search result:

<img src="/../images/verbano/search_result.png" alt="Google search result for verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">Google search result for Verbano's website</p>

The URL being correct was the only part that confirmed it was the actual search result for Verbano's website. The title and description were all wrong since it was essentially an advertisement for Viagra.

The title and description for search results are generated by Google from the linked website's HTML, the markup language used to define the structure and content of webpages. The title and description in the HTML for Verbano's actual website didn't match up with what was being shown in the search results, so it must have been coming from elsewhere.

Looking at Google’s cached version of the website explained the title of the search result.
Clicking on the three vertical dots next to the URL opened up <a href="https://blog.google/products/search/about-search-results/">extra information about the search result</a>

<img src="/../images/verbano/about_search_result.png" alt="result from about search result link" style="width: 50%; height: 50%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">result from "About Search Result"</p>

Clicking on the Cached bubble under "More options" took me to Google’s cached version of Verbano's website.
Cached links show what a web page looked like the last time Google visited and indexed it on their servers. This cached version is then used as a backup in case the web page isn't available when you go to look at it.
The title on this cached page matched what I saw in the search result, explaining where the title in the search result was coming from.

<img src="/../images/verbano/cached_website_title_html.png" alt="title tag for cached website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">HTML &lt;title&gt; tag used to generate search result title</p>

# Network Activity

By taking a look at the network activity panel within the Google Chrome developer tools, we can see if the network requests made when we visit Verbano's website can tell us anything.
When clicking the Google search result, a request is first made to hawaiiverbano.com. That request is successful with a 200 HTTP response status code.

<img src="/../images/verbano/verbano_network.png" alt="network request info for Verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">network request for Verbano's actual website</p>

The very next request made after the request for the Verbano website is a GET request for preshop-online.com/search.html?key=viagra&t=OLD_p182&dummy=best, which is one of the Viagra websites.

<img src="/../images/verbano/redirect_network.png" alt="network request info for Viagra website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">network request for the Viagra website</p>

I read the page source for Verbano's actual website and Google’s cached version, especially looking through the JavaScript code, and found nothing in there that should be causing this redirect to happen.
This lead me to believe that the redirect to the Viagra site was happening on the server side rather than being initiated by the client through some executed JavaScript in the browser.

# What's Causing This? (a theory)

In the response header section of the initial network request made to Verbano's actual website, it shows that the server used by the hosting provider that serves Verbano's website is Apache.
Apache servers use .htaccess files to set configurations on a per-directory and subdirectory basis. The default configuration for Apache servers blocks web client access to the .htaccess file for security reasons, so I'm not able to look at the file to see exactly what is happening there.
But the reason I believe this file is important is that it can be used to redirect requests for a resource from one URL to another. This would allow someone who had access to this file to send visitors for the Verbano homepage to this Viagra site instead.

It’s also possible using .htacess files to set a redirection based on the referrer (the website that the client came from), which would allow one to make it so the Verbano site would redirect to the Viagra site if the user were coming from Google.
I also got the redirect to the Viagra site when using Bing, MSN, and Yahoo, but not less popular search engines like DuckDuckGo, Ask.com, and Yandex.
This lead me to believe that there is a conditional redirect hack occurring with the .htaccess where it redirects to the Viagra site if the referrer is one of those popular search engines.

This would also explain why the Viagra site shows up when I click on a Google Search result but I get sent to the actual website when I enter the URL in my web browser's search bar since using the address bar causes no referrer to be passed to the website.
You can test this yourself by accessing the same website two different ways and <a href="https://developer.chrome.com/docs/devtools/console/javascript/">opening the Chrome DevTools console</a>

1. Google Search Result: Click on the search result link for a website and type <code>document.referrer</code> into the console, it should output https://www.google.com/

<img src="/../images/verbano/ba_referrer_google_zoomed.png" alt="google referrer" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">

2. Address Bar: Enter the URL for the same website into your address bar. Open the console and type <code>document.referrer</code>, it will return an empty string indicating there is no referrer.

<img src="/../images/verbano/ba_referrer_none_zoomed.png" alt="no referrer" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">

# A Potential Fix

If the cause of the redirection is indeed an issue with the .htaccess file, then the fix would be to remove the section responsible for it in the .htaccess file and <a href="https://developers.google.com/search/docs/crawling-indexing/ask-google-to-recrawl">make a request</a> for Google to crawl and re-index the site on their end.

Although this would only be a temporary fix. There is most likely an underlying issue with the security of the website that allowed the .htaccess file on the host server to be edited by a malicious actor in the first place.

Running a <code>whois</code> command to see the publicly available registration information for Verbano's website shows that it's hosted on GoDaddy, so a solution could involve some security settings there that would need to be enabled to better protect the files on the host server.

<img src="/../images/verbano/whois_result.png" alt="whois command output" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">whois command output</p>

# Conclusion

The purpose of this post wasn't to embarrass in any way. I reached out to Verbano by phone to let them know this was happening and even offered to help them fix it. I haven't heard back from them since initially getting in contact, so we'll see what happens but I did want to at least write about my experience looking into this since it was a fun process to try and learn as much as I could about their website without having actual developer access. The internet is a vital advertising platform for businesses, especially local restaurants, and the last thing I want to see is a restaurant in my neighborhood lose business because a malicious actor was able to mess with what people see when they look up their restaurant.

As for motivations the malicious actor responsible would have to do this to Verbano's website in the first place, there are several. The first and most obvious is the redirection drives people looking for Verbano's website to this sketchy site trying to sell them Viagra. The other reason may be from replacing the version cached by Google with a webpage filled with references to Viagra and a link to another webpage. That link currently goes to Verbano's actual website but may have previously linked to one of the Viagra sites where it would have benefited the SEO of the Viagra site. The PageRank algorithm that Google uses to determine the importance of webpages uses the number and quality of links to a page as a factor in determining its rank. A hundred sketchy Viagra websites all linking to each other may not have much weight, but hijacking legitimate websites like Verbano's to link to Viagra sites would likely have a larger effect on their place in search results.

The reality of this situation is that the internet is a constantly evolving space in which websites require maintenance and support, and without that regular maintanence they can be left open to attacks such as what I suspect happened here.
