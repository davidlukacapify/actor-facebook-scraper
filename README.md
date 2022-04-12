
## Why use Facebook Scraper?

Facebook had over 2.85 billion monthly active users as of the first quarter of 2021. And those users spend an average of 19.5 hours on the Facebook app each month. These huge numbers attract a lot of companies trying to connect with their customers and fans.

Over 200 million small businesses use Facebook Pages to promote their services. Those pages include posts, comments, likes, and lots of useful basic info on each company. If you're wondering how you could use that data, here are some ideas:

-   Track your competitors and identify what they're doing right, or wrong, and how you can do it better.
-   Use the data for market research or analysis.
-   Monitor trends and sentiment for brands and companies and use the data to inform your investment strategy.
-   Find new niches or create completely new products by creating a dataset based on your industry, region, or even city and identifying synergies or ways you can add value.
-   Track changes in attitude to find new opportunities. High or low levels of customer or fan engagement might tell you a lot about a market or industry.

If you still don't know how your business could use data scraped from Facebook, you might like to check out our  [industries pages](https://apify.com/industries)  for more inspiration.


## Just want to scrape Facebook comments or posts?

For scraping targeted Facebook data such as comments and posts, you can use one of our mini-scrapers. They have fewer settings to configure and deliver results faster. Just enter one or more post URLs and click to scrape.

- [Facebook Posts Scraper](https://apify.com/pocesar/facebook-latest-posts-scraper)
- [Facebook Comments Scraper](https://apify.com/pocesar/facebook-latest-comments-scraper)

Or let us know if you need a  [custom Facebook scraping solution](https://apify.com/custom-solutions).


## Features

Our Facebook Scraper acts as an unofficial Facebook API to let you crawl Facebook Pages. The data you extract can be saved and used however you want.

-   Extract any content from a Facebook Page:
    -   Scrape posts
    -   Scrape comments
    -   Scrape reviews
    -   Option to filter by minimum and maximum date
-   Get all Facebook Page information, including:
    -   Likes
    -   Address (includes latitude/longitude)
    -   Instagram profile
    -   Twitter profile
    -   Website
    -   Services
    -   Messenger URL
    -   Telephone number
    -   Check-ins
    -   All other public text information, e.g. awards, price range, mission
-   Fetch businesses from the Facebook Business directory on  [https://www.facebook.com/biz/directory/](https://www.facebook.com/biz/directory/)

## Tutorial and detailed step-by-step guide

Read our tutorial on  [how to use the scraper](https://blog.apify.com/how-to-scrape-facebook-pages-posts-comments-photos-and-more-425ebef352d8). It includes screenshots and examples of how to scrape the Apify Facebook Page, along with handy tips and advice on using proxies.

## Cost of usage

There are two main components to take into account if you want to run Facebook Scraper on the Apify platform:

-   [Compute units](https://apify.com/pricing/actors)  - Used for running the scraper.
-   [Minimum Actor memory](https://apify.com/pricing)  - The actor uses Puppeteer and the minimum memory you need to run it is 2048 MB. More "input page URLs" means more memory will be needed to scrape all pages.
-   [Proxy](https://apify.com/proxy)  - To run this actor, you will need to have access to residential proxies. If you don't already have access, contact us at  [support@apify.com](mailto:support@apify.com).

The usage costs differ depending on each specific case: list of URLs, total amount, set up memory, country, etc. When you scrape comments and reviews, the number of scraped posts decreases, as each post has a different URL and is scraped separately.

You can find full details on our residential proxy pricing  [here](https://apify.com/proxy?pricing=residential-ip#pricing).

### Usage tip

Limit the  `maxPosts`  parameter with a reasonable number so that you do not run out of memory and your results are saved. The scraping is carried out in such a way that, while scrolling the page, partial content is kept in memory until scrolling finishes.

### Example pricing

Based on Apify's pricing at the time of writing, the Personal plan ($49) would allow you to scrape about:

-   20-30k posts monthly without comments and reviews
-   10-20k posts monthly including comments

## Input

Example input, only  `startUrls`  and  `proxyConfiguration`  are required (check  `INPUT_SCHEMA.json`  for settings):

```json
{
    "startUrls": [
        { "url": "https://www.facebook.com/apifytech" },
        { "url": "https://www.facebook.com/biz/hotel-supply-service/?place_id=103095856397524" }
    ],
    "language": "en-US",
    "commentsMode": "RANKED_THREADED", // ["RANKED_THREADED", "RECENT_ACTIVITY", "RANKED_UNFILTERED"]
    "maxPosts": 3,
    "maxPostDate": "3 days", // or a static date in ISO format, like 2020-01-01
    "minPostDate": "1 day", // or statis date in ISO format
    "maxPostComments": 15,
    "maxCommentDate": "2020-01-01",
    "maxReviews": 3,
    "maxReviewDate": "2020-01-01",
    "scrapeAbout": true,
    "scrapeReviews": true,
    "scrapePosts": true,
    "scrapeServices": true,
    "proxyConfiguration": {
        "useApifyProxy": true,
        "apifyProxyGroups": ["RESIDENTIAL"]
    }
}

```

## Output

```json
{
    "categories": ["Hotel"],
    "info": [
        "Residenc", // ...
        "General Information\n" // ...
    ],
    "likes": 1538,
    "messenger": "https://m.me/22163", // ...
    "posts": [
        {
            "postDate": "2020-09-10T09:33:43.000Z",
            "postText": "Do Prahy opět", // ...
            "postImages": [
                {
                    "link": "https://www.facebook.com/Residen", //...
                    "image": "https://scontent-ort2-1.xx.fbcdn.net/v/t1.0" // ...
                }
            ],
            "postLinks": ["https://residen"], // ...
            "postUrl": "https://www.facebook.com/permalink.php?story_fbid=", // ...
            "postStats": {
                "comments": 1,
                "reactions": 32,
                "reactionsBreakdown": {
                    "like": 26,
                    "love": 6
                },
                "shares": 1
            },
            "postComments": {
                "count": 0,
                "mode": "RANKED_UNFILTERED",
                "comments": []
            }
        }
    ],
    "priceRange": "$$$",
    "title": "Hotel Resid", // ...
    "pageUrl": "https://www.facebook.com/Residen", //...
    "address": {
        "city": "Prague, Czech Republic",
        "lat": 50.09136,
        "lng": 14.42575,
        "postalCode": "11000",
        "region": "Prague",
        "street": "Haštalská 19"
    },
    "awards": [],
    "email": "", //...
    "impressum": [],
    "instagram": "@Residen", // ...
    "phone": "+420 22", //...
    "products": [],
    "transit": null,
    "twitter": "@Residen", //...
    "website": "http://", //...
    "youtube": null,
    "mission": [],
    "overview": [],
    "payment": null,
    "checkins": "2,082 people checked in here",
    "verified": false,
}

```

## Displaying only posts without page information

You can use the  `unwind`  parameter to display only the posts from your dataset on the platform, i.e.:

```
https://api.apify.com/v2/datasets/zbg3vVF3NnXGZfdsX/items?format=json&clean=1&unwind=posts&fields=posts,title,pageUrl

```

`unwind`  will turn the  `posts`  property on the dataset to become dataset items themselves. The  `fields`  parameters makes sure to only include the fields that are important.

## Extend Output Function

You can split your dataset by comment, instead of having everything nested. The following code can output one comment per dataset item:

```js
async ({ data, item, customData, Apify }) => {
    const { posts, ...pageData } = item;

    return posts.flatMap((post) => {
        const { postComments: { comments, ...postData }, ...restOfPost } = post;

        return comments.map((comment) => {
            return {
                ...pageData,
                ...postData,
                ...restOfPost,
                ...comment,
            }
        });
    });
}

```

Each output item will then be flat.

## Extend Scraper Function

You can use the extend scraper function to add more functionality to the scraper. All pages are kept in the  `map`variable:

```ts
async ({ page, LABELS, label, request, username, map, fns, customData, Apify }) => {
    if (label === 'HANDLE') {
        // this is inside the handlePageFunction
        const { userData } = request;

        if (
            userData.label === LABELS.PAGE
            && userData.sub === 'home'
        ) {
            // add page banner information from mobile home page, like https://m.facebook.com/apifytech
            await map.append(username, async (pageInfo) => {
                return {
                    ...pageInfo,
                    bannerUrl: await page.evaluate(() => {
                        return document.querySelector('.coverPhoto')?.style.backgroundImage.replace(/(url\(\"|\"\))/g, '') ?? null;
                    })
                };
            });
        }
    } else if (label === 'SETUP') {
        // before starting the crawler
    } else if (label === 'FINISH') {
        // after finishing the crawler
    }
}

```

## Limitations

-   Facebook Scraper does not scrape personal data from profiles.
-   No login support.
-   The "About" page can't be accessed publicly.
-   Some pages with Facebook's new layout won't load posts and are not supported.
-   The "Likes" count is a best effort. The mobile page doesn't provide a count, and some languages don't provide any at all. So if a page has, e.g. over 1.9M likes, the number will most likely be 1,900,000 instead of an exact number.
-   No content, stats, or comments for live stream posts.
-   New reviews don't contain a rating from 1 to 5, but are rather positive or negative.
-   The cut-off date for posts happens on the original posted date, not the edited date, i.e: posts show as  `February 20th 2:11AM`, but that's the edited date, the actual post date is  `February 19th 11:31AM`  provided on the DOM.
-   The order of items isn't necessarily the same as seen on the page, and is not sorted by date.

## Scraping personal data

We do not consider scraping vast amounts of personal data ethical and discourage anyone from doing so. Facebook Pages Scraper **does not scrape personal data from profiles**, including emails, addresses, phone numbers, etc. 

Personal data is protected by GDPR in the European Union and other laws and regulations around the world. You should not scrape it unless you have a legitimate reason to do so. If you're unsure whether your reason is legitimate, consult your lawyers. Please read our blog post about  [creating ethical and compliant scrapers](https://blog.apify.com/is-web-scraping-legal/)  if you would like to learn more.


## Changelog

Facebook Scraper is under continual development. You can always  [visit the changelog](https://github.com/pocesar/actor-facebook-scraper/blob/master/CHANGELOG.md)  to see the latest fixes and improvements.

## License

Apache-2.0

