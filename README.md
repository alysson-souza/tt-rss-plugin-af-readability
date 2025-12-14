# af_readability - Readability Plugin for Tiny Tiny RSS

A Tiny Tiny RSS plugin that uses [fivefilters/readability.php](https://github.com/fivefilters/readability.php) to extract and inline full article content from feeds that only provide summaries or excerpts.

## Features

- **Automatic article processing**: Automatically fetch and process full article content for selected feeds
- **Category-based configuration**: ✨ **NEW** - Enable/disable Readability for entire feed categories with a single click
- **Per-feed granular control**: ✨ **NEW** - Fine-tune settings for individual feeds with checkbox interface
- **Append mode**: Choose to replace or append extracted content to original article text
- **Manual toggle**: Click a button on any article to manually extract full content on-demand
- **Share Anything integration**: Extract content from any URL via the share dialog
- **Feed filtering**: Automatically inline content using built-in feed filters

## Requirements

- Tiny Tiny RSS
- PHP with cURL support
- Composer (for dependency management)

## Installation

1. Clone this repository into your Tiny Tiny RSS plugins directory:
   ```bash
   cd /path/to/tt-rss/plugins.local/
   git clone <repository-url> af_readability
   ```

2. Install dependencies:
   ```bash
   cd af_readability
   composer install
   ```

3. Enable the plugin in Tiny Tiny RSS:
   - Go to **Preferences** → **Plugins**
   - Enable **af_readability** (system plugin)

## Configuration

### Feed Settings

Navigate to **Preferences** → **Feeds** and find the **Readability settings** accordion:

1. **Category checkboxes** ✨ **NEW**: Click a category checkbox to enable/disable Readability for all feeds in that category
   - Indeterminate state (dash) indicates some feeds are enabled
   - Check/uncheck to toggle all feeds in the category

2. **Per-feed settings** ✨ **NEW**:
   - **Enable**: Enable Readability processing for this feed
   - **Append**: Append extracted content instead of replacing (keeps original summary)

3. **Share Anything**: Enable to use Readability from the share dialog on any URL

### Feed Filters

You can also use Tiny Tiny RSS feed filters to automatically process articles:

1. Go to **Preferences** → **Feeds** → **Edit feed** → **Filters**
2. Add a new filter with the action:
   - **Inline content**: Replace article content with extracted text
   - **Append content**: Add extracted text to existing content

## Usage

### Automatic Processing

Once enabled for a feed, articles will be automatically processed when fetched.

### Manual Processing

Click the **description** icon (📄) on any article to manually toggle full article extraction for that specific article.

### Share Dialog

If "Share Anything" is enabled, you can extract content from any URL:
1. Click **Share** on any article
2. Paste a URL
3. The plugin will attempt to extract readable content from that URL

## How It Works

The plugin uses Mozilla's Readability algorithm (PHP port by fivefilters) to:
1. Fetch the full HTML from the article URL
2. Parse and extract the main content
3. Remove ads, navigation, and other clutter
4. Present clean, readable article text

## Development

### Dependencies

- [fivefilters/readability.php](https://github.com/fivefilters/readability.php) - PHP port of Mozilla's Readability
- [psr/http-factory](https://github.com/php-fig/http-factory) - PSR-17 HTTP Factory implementation

### File Structure

```
af_readability/
├── init.php          # Main plugin class and hooks
├── init.js           # Frontend JavaScript for UI interactions
├── composer.json     # PHP dependencies
└── vendor/           # Composer dependencies
```

## Credits

- Original author: fox
- Readability algorithm: Mozilla
- PHP Readability port: fivefilters

## License

This plugin follows Tiny Tiny RSS licensing.
