---
title: Why Verbano's Website Tries To Sell You Viagra
tags:
---

<link rel="stylesheet" href="/../css/post.css">

Verbano Ristorante Italiano in Honolulu, Hawaii has been serving Sicilian and Tuscan style Italian food in the Kaimuki area since 1992.
I've gone there with my family throughout the years and always enjoyed dinners sharing calamari, lasagna, and chicken parmagiana.
I've even recommended it to people back in Hawaii who are looking for a place to eat Italian food around Kaimuki, which brings us to how I found out about their website.

I recommended Verbano to a group of friends and afterwards they told me that their website looked a bit strange.
I've seen plenty of websites for restaurants that are outdated for a number of reasons so I figured it was something along those lines. The font and background color for the website may be one that was popular in the 1990's, the website may not be secured with HTTPS, or most commonly in my experience the design is not responsive to mobile devices so when you open it on your phone the page is all zoomed out and you have to zoom in to read it.

I searched for Verbano on Google expecting to see any one of these reasons as what these friends were talking about.
When I looked up Verbano Hawaii, I didn't see their website among the first several search results but saw the local listing feature on Google Search bring up a card on the right side with the restaurants info.

<img src="/../images/verbano/local_listing_full_size.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">search results for Verbano Hawaii</p>

I clicked on the card's button labeled "website" to finally take me to the restaurants webpage.
I saw my address bar show "hawaiiverbano.com" before quickly changing to something along the lines of "safe-it-phshop.com" (the domain name of the website you get sent to cycles through a few different varieties, but they're all effectively the same website). And instead of seeing a website advertising Italian food in Kaimuki, I was greeted with a pretty sketchy pharmaceutical website trying to sell me various kinds of Viagra.

<img src="/../images/verbano/viagra_website.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">Viagra site I got sent to</p>

Naturally I was pretty shocked and thought this was what my friends were talking about, but when I brought it up to them they had no idea what I was talking about. They just thought the restaurant's website looked outdated, but after I told them to check it out on Google they got redirected to the same Viagra website I did.

So it was time to dig into this and see if I could figure out what was going on here.
The first thing I wanted to do was see if I could get to Verbano's actual website. My friends had been able to see it earlier, so clearly there was some way to get to it. I assumed the "hawaiiverbano.com" I saw before the address bar changed was the URL for their website, and hovering over the website link on the Google local listing card confirmed that.
So I knew that the URL for the website was "hawaiiverbano.com", and after putting that into my address bar it took me to the correct website. It had some of the hallmarks I was talking about earlier, with pixelated images and the content not scaling to account for my screen size.

<img src="/../images/verbano/normal_website.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">Verbano's actual website</p>

From this and some additional testing I confirmed you would get the Viagra site when accessing Verbano's site by clicking one of Google’s links, whether it was down the search result list or through the local listing card.
Whereas you would get Verbano's actual website by entering the URL into your search bar. Your web browser then caches this result meaning you’ll get the actual website from now on even when you use the Google search result links.
You can test this by clearing your cache in your browser settings and seeing that you get the Viagra site again until you access the actual website by entering the URL into your search bar.

# SEO and Caching

I noticed some strange things about the search result on Google for Verbano's website. For one it was very low on the search results for "Verbano Hawaii" (it was often on the second or third page of results), indicating that the website had poor SEO (Search Engine Optimization), which is the practice of making your website friendly to search engines such as Google through a variety of methods in order to make your website rank higher in the search results.
What most stood out was the title and description for the search result:

<img src="/../images/verbano/search_result.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">

The URL was correct which was the only part that confirmed it was the actual search result for Verbano's website, but the title and description were all wrong since it was basically an advertisement for Viagra.

The title and description for search results are generated by Google from the linked website's HTML (the markup language used to define the structure and content of webpages).
From looking at the HTML for Verbano's actual website, the title and description doesn't match up with what's being shown in the search results, so it must be coming from somewhere.

Looking at Google’s cached version of the website explains why the title of the search result is the way it is.
Clicking on the three vertical dots next to the URL opens up extra information about the search result (https://blog.google/products/search/about-search-results/).

<img src="/../images/verbano/about_search_result.png" alt="verbano website" style="width: 50%; height: 50%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">result from "About Search Result"</p>

Clicking on the Cached bubble under "More options" takes us to Google’s cached version of Verbano's website.
Cached links show what a web page looked like the last time Google visited and indexed it on their end. This cached version is then used as a backup in case the web page isn't available when you go to look at it.
The title on this cached page matches what we see in the search result, explaining where the title in the search result is coming from.

<img src="/../images/verbano/cached_website_title_html.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">HTML &lt;title&gt; tag used to generate search result title</p>

# Network Activity

By taking a look at the network activity panel within the Google Chrome developer tools, we can see if the network requests made when we visit Verbano's website can tell us anything.
When clicking the Google search result, a request is first made to www.hawaiiverbano.com as it should. That request is successful with a 200 HTTP response status code.

<img src="/../images/verbano/verbano_network.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">network request for Verbano's actual website</p>

The very next request made after the request for the Verbano website is a GET request for https://preshop-online.com/search.html?key=viagra&t=OLD_p182&dummy=best, which is one of the Viagra sites.

<img src="/../images/verbano/redirect_network.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">network request for the Viagra website</p>

I read the page source for the actual website and Google’s cached version, especially reading through the JavaScript code, and found nothing in there that should be causing this redirect.
This lead me to believe that the redirect to the Viagra site is happening on the server side rather than being initiated from the client through some executed JavaScript.

# What's Causing This? (a theory)

In the response header section of the initial network request made to http://www.hawaiiverbano.com, it shows that the server used by the hosting provider to serve Verbano's website is Apache.
Apache servers use .htaccess files to set configurations on a per-directory and subdirectory basis.
The default configuration for Apache servers block web client access to the .htaccess file for security reasons,so I'm not able to look at the file to see exactly what is happening there.
But the reason I believe this file is important to what's happening is that it can be used to redirect requests for a resource from one URL to another. This would allow someone who had access to this file to redirect requests for the Verbano homepage to this Viagra site.
It’s also possible to set a redirection based on the referrer (the website that the client came from), which would allow one to make it so the Verbano site would redirect to the Viagra site if the user were coming from the Google Search results page.
I also got the redirect to the Viagra site when using Bing, MSN, and Yahoo, but not less popular search engines like DuckDuckGo, Ask.com, and Yandex
This leads me to believe that there is a conditional redirect occurring with the .htaccess where it redirects to the Viagra site if the referrer is one of those popular search engines.

This would also explain how the Viagra site shows up when you click on a Google Search result but you get sent to the actual website when you enter the URL in your web browser's search bar since using the address bar causes no referrer to be passed to the website.
You can test this yourself by accessing the same website two different ways and opening the console.

1. Google Search Result: Click on the search result link for a website and type document.referrer into the console, it should say ‘https://www.google.com/’

<img src="/../images/verbano/ba_referrer_google_zoomed.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">

2. Address Bar: Enter the URL for the website into your address bar. Open the console and type “document.referrer”, it will return an empty string.

<img src="/../images/verbano/ba_referrer_none_zoomed.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">

# A Potential Fix

If the cause of the redirection is indeed an issue with the .htaccess file, then the fix for it would be to remove the responsible section in the .htaccess file and <a href="https://developers.google.com/search/docs/crawling-indexing/ask-google-to-recrawl">make a request</a> for Google to crawl and re-index the site on their end

Although this would just be a temporary fix. There is likely an underlying issue with the security of the website that allowed the .htaccess file on the host server to be edited by a malicious actor in the first place.

Running a <code>whois</code> command to see the publicly available registration information for Verbano's website shows that it's hosted on GoDaddy, so a solution could involve some security settings that need to be enabled in order to better protect the files on the host server.

<img src="/../images/verbano/whois_result.png" alt="verbano website" style="width: 100%; height: 100%; margin: auto; padding: 1rem 0 0 0;">
<p class="img-caption">whois command output</p>

# Conclusion

The purpose of this post wasn't to embarass in any way, in fact I reached out to Verbano by phone to let them know this was happening and even offered to help them fix it. I haven't heard back from them since initially getting in contact, so we'll see what happens but I did want to at least write about my experience looking into this since it was a fun process to try and learn as much as I could about this. The internet is a vital platform for advertising for many companies, and the last thing I want to see is a restaurant to possibly lose business because a malicious actor was able to mess with their website. As for reasons the malicious actor responsible would have to do this to Verbano's website in the first place there are several. The first and most obvious is the redirection drives people looking for Verbano's website to this sketchy site trying to sell them Viagra. The other reason may be that by replacing the version cached by Google with a webpage filled with references to Viagra and a link to another webpage. That link currently links to Verbano's actual website but it may have linked to a Viagra site earlier in which case it would have benefited the SEO of the Viagra site since you would have a legitimate website linking to it and the PageRank algorithm that Google uses to generate search results uses the number and quality of links to determine the rank of a website. A hundred of sketchy Viagra sites all linking to each other may not have much weight, but hijacking legitimate websites to link to Viagra sites would likely have a larger effect on its place in search results. The reality of this situation is the internet is a constantly evolving space where websites require maintenance and support, and it doesn't appear to me that Verbano's website has been maintained for some time, leaving it open to attacks such as what I suspect happened here.
