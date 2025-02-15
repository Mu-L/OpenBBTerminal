---
title: Data sources
sidebar_position: 1
description: This page provides useful information on dealing with different data
  vendors when using OpenBB's Terminal. It outlines how to select a default data source,
  acquire API keys, and switch the data vendor using specific commands, all in an
  effort to streamline and improve the user's experience.
keywords:
- Terminal
- data vendors
- API keys
- data sources
- FinancialModelingPrep
- Polygon
- AlphaVantage
- EODHD
- YahooFinance
- source
- stocks/fa/income
- changing data source
- Default data source
- /sources
- get --cmd
- set --cmd
---

import HeadTitle from '@site/src/components/General/HeadTitle.tsx';

<HeadTitle title="Data sources - Data - Usage | OpenBB Terminal Docs" />

import TutorialVideo from '@site/src/components/General/TutorialVideo.tsx';

<TutorialVideo
  youtubeLink="https://www.youtube.com/embed/cvSwG96Yf4o?si=oswcJYUH51F206Hu"
  videoLegend="Short video on where the data comes from"
/>

## Relationship with data vendors

Most commands will require obtaining API keys from various data providers. OpenBB provides methods for consuming these data feeds, but has no control over the quality or quantity of data provided to an end-user. **No API Keys are required to get started using the Terminal**.

See the list of data providers [here](/terminal/usage/guides/api-keys), along with instructions for entering the credentials into the OpenBB Terminal. You can also request a new data source through this [form](https://openbb.co/request-a-feature).

:::note
OpenBB doesn't store any financial data in its servers. We aggregate access to multiple data sources through API calls and standardize that interaction to provide users a seamless experience when dealing with different data vendors
:::

## Changing data source in command

Many commands have multiple datasources attached to it. A great example is `/stocka/fa/income` that allows you to select FinancialModelingPrep, Polygon, AlphaVantage, EODHD or YahooFinance. In order to specify the data vendor you want to utilize for that specific command you can utilize the argument `--source`.

This also becomes clear from the help menu.

```
(🦋) /stocks/fa/ $ income -h

usage: income [-t TICKER] [-q] [-r] [-p column] [-h] [--export EXPORT] [--sheet-name SHEET_NAME [SHEET_NAME ...]] [-l LIMIT] [--source {FinancialModelingPrep,Polygon,AlphaVantage,EODHD,YahooFinance}]

Prints a complete income statement over time. This can be either quarterly or annually.

optional arguments:
  -t TICKER, --ticker TICKER
                        Ticker to analyze (default: None)
  -q, --quarter         Quarter fundamental data flag. (default: False)
  -r, --ratios          Shows percentage change of values. (default: False)
  -p column, --plot column
                        Rows to plot, comma separated. (-1 represents invalid data) (default: None)
  -h, --help            show this help message (default: False)
  --export EXPORT       Export raw data into csv, json, xlsx (default: )
  --sheet-name SHEET_NAME [SHEET_NAME ...]
                        Name of excel sheet to save data to. Only valid for .xlsx files. (default: None)
  -l LIMIT, --limit LIMIT
                        Number of entries to show in data. (default: 5)
  --source {FinancialModelingPrep,Polygon,AlphaVantage,EODHD,YahooFinance}
                        Data source to select from (default: FinancialModelingPrep)

For more information and examples, use 'about income' to access the related guide.
```

Within the source arguments it shows the exact sources as previously mentioned. Therefore, with this information in hand it is possible to switch to a different source e.g. with `income --source Polygon`. Do keep in mind that you might need to have an API key to use this source, see [here](/terminal/basics/advanced/api-keys).

![Selecting a new Data Source](https://user-images.githubusercontent.com/85772166/233730763-54fd6400-f3ad-44a0-9c73-254d91ac2085.png)

The available sources for each command are displayed on the right of the command, and they can be distinguished by the square brackets and distinct font color group. By default, if the user doesn't specify `--source` the terminal will use the first data provider displayed.


### Setting default source through Hub (easy)

The default data vendor can be selected with more ease through the OpenBB Hub. Instructions can be found here.


### Setting default source through Terminal

The default data source for each command (where multiple sources are available) can be defined within the [`/sources`](/terminal/usage/guides/changing-sources) menu.

For example, if you would like to change the default data provider for the `income` command from the `stocks/fa` menu you can first run the command `get --cmd stocks/fa/income`. This returns the following:

```console
(🦋) /sources/ $ get --cmd stocks/fa/income

Default   : FinancialModelingPrep
Available : FinancialModelingPrep, Polygon, AlphaVantage, EODHD, YahooFinance
```

Then, with `set` command you can change the default data provider. For example, we can change the data provider to `Polygon` with
the following:

```console
(🦋) /sources/ $ set --cmd stocks/fa/income --source Polygon

Default data source for 'stocks/fa/income' set to 'Polygon'.
```

and we can use `get` once more to confirm this update:

```console
(🦋) /sources/ $ get --cmd stocks/fa/income

Default   : Polygon
Available : Polygon, FinancialModelingPrep, AlphaVantage, EODHD, YahooFinance
```
