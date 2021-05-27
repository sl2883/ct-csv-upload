
## CleverTap python csv upload tool

Please refer to the main source [here](https://github.com/CleverTap/clevertap-csv-upload)

This repo is focused primarily to describe how to send events to Clevertap (generic as well as charged)

### Command line to upload charged events via CSV
```javascript
python csvupload.py -a TEST-XXX-XXX-XXXX -c XXXXXXXXXXXXXXXXXXXX -r eu1 -p input-charged.csv -t event
```

Charged events can have an items list. For example -
```json
[
        {
            "Category": "Books",
            "Book name": "The Millionaire next door",
            "Quantity": 1
        },
        {
            "Category": "Books",
            "Book name": "Achieving inner zen",
            "Quantity": 1
        },
        {
            "Category": "Books",
            "Book name": "Chuck it, let's do it",
            "Quantity": 5
        }
    ]
```

In the CSV, we provide the items list as a json list without whitespaces

```json
[ { "Category": "Books", "Book name": "The Millionaire next door", "Quantity": 1 }, { "Category": "Books", "Book name": "Achieving inner zen", "Quantity": 1 }, { "Category": "Books", "Book name": "Chuck it, let's do it", "Quantity": 5 } ]
```

> The column name for providing items in a Charged event is Items

#### Other events should continue to work the way they worked before

An example command for a generic event - 
```
python csvupload.py -a TEST-XXX-XXX-XXXX -c XXXXXXXXXXXXXXX -r eu1 -p input-others.csv -t event
```

Please note that the CSV file needs few important columns

- identity
- type (event, profile etc.
- evtName (Charged, Product Viewed etc.)
