# Metafield Configuration Guide

This theme supports dynamic content via Shopify metafields with automatic fallback to static section settings.

## How It Works

The theme checks for metafield values first. If a metafield exists and has a value, it will be used. If not, the static setting from the theme editor is used as a fallback.

## Setting Up Metafields

### Step 1: Create Metafield Definitions

1. Go to **Shopify Admin** → **Settings** → **Custom data**
2. Select **"Shops"** from the list
3. Click **"Add definition"** for each metafield below

### Step 2: Define the Following Metafields

#### Announcement Bar Metafields

**Announcement Text:**
- **Name:** Announcement Text
- **Namespace and key:** `custom.announcement_text`
- **Type:** Single line text
- **Description:** Override the announcement bar text

**Announcement Link:**
- **Name:** Announcement Link
- **Namespace and key:** `custom.announcement_link`
- **Type:** URL
- **Description:** Override the announcement bar link URL

#### Hero Slideshow Metafields

**Hero Heading:**
- **Name:** Hero Heading
- **Namespace and key:** `custom.hero_heading`
- **Type:** Single line text
- **Description:** Override hero slideshow heading

**Hero Text:**
- **Name:** Hero Text
- **Namespace and key:** `custom.hero_text`
- **Type:** Multi-line text
- **Description:** Override hero slideshow subheading/description

**Hero Button Label:**
- **Name:** Hero Button Label
- **Namespace and key:** `custom.hero_button_label`
- **Type:** Single line text
- **Description:** Override hero slideshow button text

**Hero Button URL:**
- **Name:** Hero Button URL
- **Namespace and key:** `custom.hero_button_url`
- **Type:** URL
- **Description:** Override hero slideshow button destination

## Setting Metafield Values

After creating the definitions:

1. Go to **Settings** → **Custom data** → **Shops**
2. Click on your shop name
3. You'll see all the metafield definitions you created
4. Fill in values for the ones you want to override
5. Leave blank any you want to use the default static values from theme editor

## Static Fallbacks

If you don't set up metafields, the theme will automatically use the static values configured in:

- **Theme Editor** → **Sections** → **Announcement bar**
- **Theme Editor** → **Homepage** → **Hero slideshow**

## Example Use Cases

### Seasonal Promotions
Set announcement bar metafields to quickly change promotional messages without editing the theme:
- Black Friday: "BLACK FRIDAY SALE - 50% OFF EVERYTHING"
- Christmas: "LAST MINUTE GIFTS - FREE EXPRESS SHIPPING"

### A/B Testing
Test different hero messaging by updating metafields without touching theme editor settings.

### Multi-Language Support
While the theme uses Shopify's translation system, metafields provide an additional layer for dynamic content that may vary by market.

## Technical Details

The implementation uses Liquid's `default` filter pattern:

```liquid
{% liquid
  assign announcement_text = shop.metafields.custom.announcement_text | default: section.settings.text
%}
```

This ensures zero breaking changes - existing themes continue to work with static settings, and metafields are purely optional enhancements.
