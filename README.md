# Crawler
A Program that crawls on web starting from a given web page and looking for keywords through other internal links that are found.

## Requirements
Langauge Used = Python3<br />
Modules/Packages used:
* requests
* pickle
* bs4
* datetime
* optparse
* colorama
* time
<!-- -->
Install the dependencies:
```bash
pip install -r requirements.txt
```
## Input
 * '-u', "--url" : URL to start Crawling from
 * '-t', "--in-text" : Words to find in text (seperated by ',')
 * '-s', "--session-id" : Session ID (Cookie) for the Request Header (Optional)
 * '-w', "--write" : Name of the File for the data to be dumped (default=current data and time)
 * '-e', "--external" : Crawl on External URLs (True/False, default=False)
 * '-T', "--timeout" : Request Timeout
## Output
It will stop when it has crawled all the internal links of the given URL or if the user presses CTRL+C.<br />
It then display Information about total URLs extracted, Internal URLs extracted and external URLs extracted.<br />
And finally gives a list or URLs in which the keywords we've interested in were found.

## Documentation
I'll explain this web crawler in simple terms.

### What is this Web Crawler?

This is a Python program that can automatically visit web pages and collect information. Think of it like a robot that reads web pages, finds links within them, and can search for specific words you're interested in.

### Main Features:

1. **Multi-threaded**: It can crawl multiple websites simultaneously, making it faster
2. **Selective Crawling**: Can either:
   - Stay within the same website (internal links only)
   - Also visit external websites if configured
3. **Search Capability**: Can search for specific keywords in web pages
4. **Data Storage**: Saves all findings to a file for later use

### How to Use It:

You can run it with these main options:
```bash
python crawler.py -u "website_url" -t "keywords_to_find" -e "True/False" -T "timeout"
```

For example:
```bash
python crawler.py -u "https://example.com" -t "python,programming" -e "False" -T "10"
```

### How it Works (Step by Step):

1. **Starting Up**:
   - Takes the URL(s) you provide
   - Sets up multiple threads to work simultaneously
   - Prepares to track internal and external links

2. **Crawling Process**:
   - Visits each webpage
   - Looks for all links (`<a>` tags) on the page
   - Categorizes links as internal (same website) or external (different websites)
   - Checks page content for your keywords
   - Keeps track of which pages it has already visited

3. **Safety Features**:
   - Respects website timeouts
   - Can ignore certain file types (like .pdf, .zip)
   - Uses a proper browser user-agent
   - Can handle errors gracefully

4. **Results**:
   - Shows progress with colored output
   - Displays which URLs contain your keywords
   - Counts how many internal and external links were found
   - Saves all data to a file

### Key Components:

1. **URL Processing** (lines 41-46):
   - Checks if URLs are valid before crawling

2. **Link Extraction** (lines 76-101):
   - Finds and processes all links on a page
   - Separates internal from external links

3. **Content Searching** (lines 121-126):
   - Searches for your keywords in page content
   - Records pages where keywords are found

4. **Multi-threading** (lines 188-201):
   - Splits work among multiple threads
   - Makes crawling much faster

### Output:
- Shows green (+) for internal links
- Shows red (-) for errors
- Shows yellow (*) for status updates
- Shows cyan (:) for external links
- Saves all findings to a file with the current date/time

This crawler is particularly useful when you need to:
- Map out a website's structure
- Find specific content across many pages
- Collect links from multiple websites
- Research website connections and relationships
