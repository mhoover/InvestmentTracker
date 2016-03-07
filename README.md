# InvestmentTracker
## Status
In progress

## Introduction
Trying to log in an follow investments through a financial institution's
online portal is, to me, confusing and incomplete. The point of
InvestmentTracker is to take some upfront information from a financial
institution's online portal and then be able to use/manipulate those data
outside of the confines of the financial institution by bringing outside
price data.

Currently, this repository is set up with an `investments.json` file that
should be present for the Python scripts to run, but not necessarily
committed to GitHub. The JSON (which itself is a number of `dict`s inside a
`list`) should include the following key/value pairs:

* `institution`: type = `str`; name of the financial institution
* `accounts`: type = `list`; list of `dict`s
    * `name`: type = `str`; name of financial account
    * `cash`: type = `dict`; information on cash holdings in account
        * `date`: type = `list`; `str` dates (mm/dd/yyyy) corresponding to
        `value` entry
        * `value`: type = `list`; `float` value (in USD) corresponding to
        `date` entry
    * `positions`: type = `list`; list of `dict`s
        * `company`: type = `str`; name of company
        * `symbol`: type = `str`; trading symbol of company
        * `dates`: type = `list`; `str` dates (mm/dd/yyyy) of financial
        instrument purchase corresponding to `shares` entry
        * `shares`: type = `list`; number of shares (`float`) purchased on
        corresponding `dates` entry

### Example JSON
An sample `investments.json` may look like:

```
[{
    "accounts": [{
        "positions": [{
            "dates": ["01/01/2015", "09/15/2015"],
            "company": "apple",
            "symbol": "AAPL",
            "shares": [121, 20]
        }, {
            "dates": ["12/10/2014"],
            "company": "microsoft",
            "symbol": "MSFT",
            "shares": [16]
        }],
        "name": "fund_1",
        "cash": {
            "date": ["12/31/2015"],
            "value": [135.93]
        }
    }],
    "institution": "My Bank"
}, {
    "accounts": [{
        "positions": [{
            "dates": ["12/23/2012"],
            "company": "google",
            "symbol": "GOOG",
            "shares": [12]
        }],
        "name": "fund_2",
        "cash": {
            "date": ["01/12/2014", "04/01/2014"],
            "value": [233.40, 278.12]
        }
    }],
    "institution": "My Second Bank"
}]
```

## Future work
API calls to financial instrument values (i.e., stock prices) will be added
along with scraped web data for mutual fund values. With these data added
to investment information, (fairly) accurate historical information can
be created charting the success (or failure) of an investment instrument
over time, which may or may not be useful for performance evaluation. There
are other (better) ways to do this out there, but part of the fun is
learning more about financial information and creating a system that at least
I myself find valuable and useful.

## Contact information
Got question, feel free to email me at matthew.a.hoover at gmail.com.
