<p align="center">

<img alt="preview" src="https://neftyblocks.me/preview-market.png"></img>

</p>

[![npm bundle size](https://img.shields.io/bundlephobia/min/@neftyblocks/market?style=flat)](https://www.npmjs.org/package/@neftyblocks/market)
[![npm](https://img.shields.io/npm/dw/@neftyblocks/market?style=flat)](https://www.npmjs.org/package/@neftyblocks/market)
[![npm](https://img.shields.io/npm/v/@neftyblocks/market?style=flat)](https://www.npmjs.org/package/@neftyblocks/market)

# NeftyBlocks market

We at NeftyBlocks understand the importance of keeping your users engaged. We want to make it easy for you to keep your community of NFT gamers, collectors and enthusiast close to your project. So, we have created a marketplace for you to embed in your website and keep your users engaged with what matters most, your NFT project!

#### What does this embed include?

-   ⚙️ Fully functioning marketplace (filters, cards)
-   🎨 [Customizable look](#-styling) (styling)
-   💲 [Payment processing](#-payment-processing) (read more below)

## 🚀 Usage

First of all, you need to install the library:

#### Package manager

1. Type in the terminal:

```bash
    # install dependencies
    $ npm i @neftyblocks/market

    # or yarn
    $ yarn add @neftyblocks/market
```

2. Include in your javascript file:

```js
import '@neftyblocks/market';
```

3. Place in your HTML where you want to embed the market:

```html
<neftyblocks-market collection="your-collection"></neftyblocks-market>
```

#### CDN (Plain HTML)

1. Place in your HTML where you want to embed the market:

```html
<neftyblocks-market collection="your-collection"> </neftyblocks-market>

<script type="module">
    import 'https://cdn.jsdelivr.net/npm/@neftyblocks/market@latest';
</script>
```

## 🎛 Options

Options are placed the element as `attributes` with a `value`.
which looks as follows:

```html
<neftyblocks-market collection="your-collection-id" network="mainnet"> </neftyblocks-market>
```

Most attributes are optional except for `collection`

| Attribute                   | Value                                                      | Default              | Description                                                                                                                                                                                                                   |
| --------------------------- | ---------------------------------------------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `collection` **(required)** | `your-collection-id`                                       | None                 | set your collection name so the API knows which collection to send to the embed                                                                                                                                               |
| `limit`                     | number between `1` and `100`                               | `50`                 | set a value on how the maximum amount of NFT's to show per page                                                                                                                                                               |
| `network`                   | [supported chains / networks](#supported-chains--networks) | `mainnet`            | `mainnet` is the default network you can set it to `testnet` if you want to try it out first.                                                                                                                                 |
| `chain`                     | [supported chains / networks](#supported-chains--networks) | `wax`                | there is support for multiple chains, see [supported chains / networks](#supported-chains--networks) below.                                                                                                                   |
| `redirect`                  | None                                                       | None                 | the redirect URL is optional and is a way for you to interact with a transaction that happened [see redirect URL](#redirect-URL), default behavior is to redirect the user back to the URL it came from with no extra params. |
| `endpoint`                  | None                                                       | `api.neftyblocks.me` | only useful for development, API is highly customized for it's purpose.                                                                                                                                                       |
| `custom`                    | None                                                       | None                 | Used to customize the card quick information [See custom config](#custom-config)                                                                                                                                              |

#### supported chains / networks

The following blockchains are supported by the embedded marketplace

| chain         | network                    |
| ------------- | -------------------------- |
| wax (default) | mainnet (default), testnet |

#### redirect URL

if a redirect URL is placed as an attribute after the user has signed the transaction, the user will be redirected to the redirect URL after the transaction has been completed. we will include a couple of attributes in the query string to help you with the process.

-   `tx`: the transaction hash
-   `status`: the status of the transaction (`executed` or `failed`) this still needs to be validated as successfully executed
-   `sale`: the sale id
-   `assets`: the asset ids as `"12345,12345,12345"`

while we provide some useful data it's still up to you to validate that the transaction is valid and the user did make the sale. Everybody can write to a URL so be careful.

## 🎨 Styling

To get your look and feel to match your project, can customize by using [css variables](https://www.w3schools.com/css/css3_variables.asp).

either place this in your `style.css` css file or add a `<style> ... css here ... </style>` tag in your HTML.

```css
:root {
    /* the font-family for all text */
    --nefty-font-family: sans-serif;
    /* the default font size (best kept as is) */
    --nefty-font-size: 16px;
    /* the smaller font size (best kept as is) */
    --nefty-font-size--small: 14px;

    /* the minimum and maximum width of the cards (responsive)  */
    --nefty-card-size-min: 250px;
    --nefty-card-size-max: 1fr;

    /*  the space between cards */
    --nefty-cards-gap: 28px;

    /* border radius for all roundings of inputs, buttons, images */
    --nefty-radius: 24px;
    --nefty-radius-image: 18px;
    --nefty-radius-small: 12px;

    /* border color for buttons, inputs */
    --nefty-border: #353945;
    /* border color for the cards (if none use same color as card background) */
    --nefty-border-card: #23262f;
    /* border thickness */
    --nefty-border-size: 1px;

    /* color primary text */
    --nefty-color: #fcfcfd;
    /* colors for non primary text */
    --nefty-color-secondary: #777e90;

    /* buy button in the card (highlight) */
    --nefty-btn-primary: #00ffff;
    --nefty-btn-primary-bg: #23262f;
    --nefty-btn-primary-border: #00ffff;
    --nefty-btn-primary--active: #23262f;
    --nefty-btn-primary-bg--active: #00ffff;
    --nefty-btn-primary-border--active: #00ffff;

    /* styling of pagination buttons and small reset button (will appear once you start filtering) */
    --nefty-btn-secondary: #fcfcfd;
    --nefty-btn-secondary-bg: #141416;
    --nefty-btn-secondary-border: #353945;
    --nefty-btn-secondary--active: #fcfcfd;
    --nefty-btn-secondary-bg--active: #353945;
    --nefty-btn-secondary-border--active: #353945;

    /* the filter button on mobile design */
    --nefty-btn-tertiary: #141416;
    --nefty-btn-tertiary-bg: #fcfcfd;
    --nefty-btn-tertiary-border: #fcfcfd;
    --nefty-btn-tertiary--active: #fcfcfd;
    --nefty-btn-tertiary-bg--active: #141416;
    --nefty-btn-tertiary-border--active: #fcfcfd;

    /* backgrounds */
    /* list background in filters (schemas) */
    --nefty-bg-list-item: #141416;
    /* card mint background */
    --nefty-bg-mint: #0e0f12;
    /* all inputs (filters) */
    --nefty-bg-inputs: #23262f;
    /* card background */
    --nefty-bg-card: #23262f;
    /* loading state */
    --nefty-bg-loading: rgba(255, 255, 255, 0.05);
    /* fallback background color for images (best kept as is) */
    --nefty-bg-image: rgba(255, 255, 255, 0.05);
}
```

### 🪄 Advanced Styling Options

For more options we support the use of `::part` which will give you full controle to overwrite styling. [read more about ::part](https://developer.mozilla.org/en-US/docs/Web/CSS/::part)

To see what you can style look at the HTML in the console and look for the attribute `part="..."`

```css
neftyblocks-market::part(part-name) {
    /* override the styling */
}
```

the following parts are available

Main part:

-   `mobile-filter`
-   `loader-group`
-   `loader-list`
-   `loader-cards`
-   `loader-cards-inner`
-   `loader-filters`
-   `market`
-   `pagination`
-   `pagination-btn`
-   `pagination-back`
-   `pagination-next`
-   `error`
-   `error-btn`

Card part:

-   `card`
-   `card-group`
-   `card-empty`
-   `card-header`
-   `card-mint`
-   `card-info`
-   `card-info-loading`
-   `card-info-btn`
-   `card-info-item`
-   `card-info-item-spacer`
-   `card-info-item-value`
-   `card-visual`
-   `card-image`
-   `card-video`
-   `card-shadow`
-   `card-collection`
-   `card-name`
-   `card-pricing`
-   `card-price`
-   `card-price-image`
-   `card-price-usd`
-   `card-footer`
-   `card-buy`

Filter part:

-   `filters`
-   `container`
-   `filter`
-   `filter-title`
-   `reset`
-   `filter-refresh`
-   `refresh`
-   `select`
-   `input`
-   `list`
-   `list-item`
-   `fields`
-   `field`
-   `field-input`
-   `field-icon`

Dynamic part:

-   `market-section-filters-active` - will hide cards if filters are active (on mobile only)
-   `market-pagination-filters-active` - will hide pagination if filters are active (on mobile only)

## Custom config

> **Note**
> This is for advanced users and require basic knowledge on Javascript and API's.

Custom config is used to customize the content you see if you click the "i" for more information about the sale.

to use custom config you need to add a `config` object.
this object needs to be `stringified` and passed in to the attribute called `custom`.

> **Note**
> All optional `keys` can be removed (so no `skip: false`, but just delete the line)
> this will reduce the params length for the GET call and gives room for more options.

```js
// Example config with all options
const config = {
    // global smart contract being used to fill field data
    contract: {
        // key can be "sale_id", "template_id", "asset_id"
        key: 'asset_id',
        // the address of the contract
        contract: 'custom.contract',
        // the scope of the contract
        scope: 'custom.contract',
        // the table of the contract
        table: 'yourtable',
    },
    // global content that will be display on every card
    content: [
        {
            // What you want to content to be called (!mandatory)
            name: 'Title',
            // value is based on path in sales item see: https://aa.neftyblocks.com/docs/#/sales/get_atomicmarket_v1_sales__sale_id_
            value: 'assets+0+name',
        },
        {
            name: 'Health',
            // symbol to append after the value (optional)
            symbol: '%',
            // use field to let the script know to use the smartcontract (no nested values supported)
            field: 'health',
            // if no value is found skip showing it (optional)
            skip: true,
        },
    ],
    // optional to set extra content per schema (all values will be appended to the global content)
    // and follow the same rules as the global content and contract above
    schemas: {
        'schema name': {
            contract: {
                key: 'asset_id',
                contract: 'custom.contract',
                scope: 'custom.contract',
                table: 'yourtable',
            },
            content: [
                {
                    name: 'rarity',
                    value: 'assets+0+data+rarity',
                    skip: true,
                },
                {
                    name: 'Health',
                    field: 'health',
                    symbol: '%',
                    skip: true,
                },
            ],
        },
    },
};

// use the way your framework provides dynamic attributes
`<neftyblocks-market collection="yourCollection" custom=${JSON.stringify(config)}></neftyblocks-market>`;
```

## 💲 Payment processing

As we do not expect everybody to have a login and a way to handle signing transactions, we provide a payment processor that will be used to handle the payment process. The payment processor runs on a custom domain [https://neftyblocks.me](https://neftyblocks.me) and will deal with login, signing, and getting the user back to the site from where they came.

## ❤️ Community & Support

-   [GitHub Issues.](https://github.com/neftyblocks/embeds) Best for: bugs and errors you encounter using the embeded market.
-   [Discord.](https://discord.com/invite/Bf789hjAsE) Best for: sharing your project and hanging out with the community.
