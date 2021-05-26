## CleverTap python csv upload tool

### Usage
to upload user profile or events from a csv:
- git clone the repo
- run csvupload.py passing your CleverTap Account ID and Passcode and the absolute path to your csv file.
- Add -d true to do a dry run.
- Add -t to specify type of data: event or profile (defaults to profile)
- e.g. ./csvupload.py -a WWW-YYY-ZZZZ -c AAA-BBB-CCCC -p ~/Desktop/profileSample.csv

```
arguments:
-h, --help show this help message and exit
-a ID, --id ID CleverTap Account ID
-c PASSCODE, --passcode PASSCODE CleverTap Account Passcode
-r REGION, --region REGION Dedicated CleverTap Account Region, optional
-p PATH, --path PATH Absolute path to the csv file
-m MAPPINGPATH, --mappingpath MAPPINGPATH Absolute path to a custom key json mapping
-t TYPE, --type TYPE The type of data, either profile or event, defaults to profile
-d DRYRUN, --dryrun DRYRUN Do a dry run, process records but do not upload

```

NOTE: you must include one of identity, objectID, FBID or GPID, in your data. Email addresses can serve as an identity value, but the key must be identity.  

### Usage for Charged events with Items array

```javascript
python csvupload.py -a TEST-XXX-XXX-XXXX -c XXXXXXXXXXXXXXXXXXXX -r eu1 -p in.csv -t event
```

### Item value in CSV cell has to be modified to have single quotes

For example

#### If your json was -
```json
{
    "Items": [
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
        "Book name": "Chuck it, lets do it",
        "Quantity": 5
      }
    ]
}
```

#### Convert it to

``` json
"{'Items': [ { 'Category': 'Books', 'Book name': 'The Millionaire next door', 'Quantity': 1 }, { 'Category': 'Books', 'Book name': 'Achieving inner zen', 'Quantity': 1 }, { 'Category': 'Books', 'Book name': 'Chuck it, lets do it', 'Quantity': 5 } ]}"
```