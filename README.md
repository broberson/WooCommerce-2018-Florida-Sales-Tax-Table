# WooCommerce 2020 Florida Sales Tax Table

#### 2020 Florida Sales Tax Rates Importable CSV for WooCommerce

## Why

Retail businesses in Florida are required to collect 6% sales tax on non-exempt purchases. That means that an e-commerce business in Florida must collect sales tax on purchases made by customers in Florida. Many counties in Florida require an additional surtax to be charged on sales to customers located in that county. If this comes as a surprise, you should probably talk to your accountant. I'm not an accountant, so it wouldn't be a good idea to ask me about these things.

## Where

In WooCommerce Settings, on the Tax tab, under Standard Rates, you can enter all of the various tax rates you want to apply, but that's terribly boring. The "Import CSV" button in the corner, however, is nice. This repository contains just the sort of CSV file that button likes.

This repository also contains the shell script used to download the necessary data, combine it, and produce that CSV file. It's not a great example of bash-scripting-fu, but it works on my machine. (macOS 10.15.4 - Catalina).

**Pre-requisites**:

- Install [Homebrew](https://brew.sh)
- Install wget, Q and Poppler: `brew install wget q poppler`

You may also need the Xcode command line tools installed: `xcode-select --install`

## How

For those who don't speak bash, the comments in the script are still fairly descriptive.

In general, though, we download [a tab delimited datafile from GeoNames.org](http://download.geonames.org/export/zip/) and extract the records for Florida counties and the zip codes associated with them.

Then we download [a PDF file from the Florida Department of Revenue](http://floridarevenue.com/Pages/forms_index.aspx#discretionary) that lists the discretionary sales surtax required by each Florida county; we convert that to text with the version of `pdftotext` included with [poppler](https://poppler.freedesktop.org/) and extract the county and surtax rate data from the file.

These two datasets are combined and a CSV file is generated listing the total sales tax (6% state tax + county surtax) and the zipcodes where that tax rate applies, suitable for import into WooCommerce.

I really have to mention [q - https://github.com/harelba/q](https://github.com/harelba/q) which is positively magical. Running SQL queries against text files, with joins and grouping and… well it's cathartic.

Also, thanks to [Adam Taylor](http://adam-taylor.com/florida-sales-tax-rates-in-woocommerce/) for doing this in 2016.

## But…

I know. You need this for Michigan or Nebraska or Bangladesh or wherever you are. I'm afraid I can't help you. If there are documents available with the information you need, maybe you can hack something together based on what you've found here. All I can really do is wish you good luck, and I do. Good luck!

Also, as I mentioned earlier, I'm not the person to direct your tax-related questions to. I'm a software developer, not an accountant. You don't want me trying to fix your car, either.

Maybe you're running Windows, and you wonder if this script will work on your machine. I don't know. I rather doubt it. I wish you good luck, too. You'll probably need it.
