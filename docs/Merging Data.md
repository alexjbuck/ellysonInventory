# Merging in new data

It is expected that data will come from two types of locations:

1. Internal to the Sharepoint list
2. External to the Sharepoint list

Internal data are records and fields that only exist within SharePoint. This could be tags (field) projects that do not live in any other database (records).

External data are records that are imported from another database, such as STAIRS.

This means we need to _merge_ our datasets when an update comes in. A new data import from STAIRS will only affect the records that come from STAIRS, but should leave the other records untouched, _and_ should preserve any additional fields added to the records being updated from SharePoint, even though those fields are _not_ present in the imported data.

I have not found a good solution for this problem with either excel or csv files. However, there is a simple one-line solution within JavaScript. If your existing list of records is called `list` and your import is called `update` then:

```javascript
list.filter(l => Object.assign(l,update.find(u => u.id==l.id)) )
```

will produce an array of merged objects, whose fields are the __Union__ of `list` and `update`, letting the values of `update` overwrite those of `list` in any overlap, and preserving any fields from `list` not present in `update`.

## Enough of the teaser, how do I do that?

### JSONify the data

First step is to JSONify the CSV data. [csv2json](https://csvjson.com/csv2json) is a handy webapp for doing just that. You paste in your CSV formatted text on one side, and a JSON object comes out the other side. 

You should expect that a CSV should look like an `Array` of `Objects`. Each `Object` in the `Array` is a record or row from the CSV. Each `Object` has fields corresponding to the column headers from the CSV.

To get the current list, export the Sharepoint list to CSV and JSONify it.

To get the update, it needs to be in a CSV compatible format, then JSONify it.

### How do I use JavaScript on NMCI???

So, NMCI in all its awesomeness has blocked the webpage developer tools, and the javascript console that comes with that. Luckily, there's a web app for everything. [jsconsole](https://jsconsole.com/) provides you with a JavaScript console in a web browser and it'll do everything we need.

```javascript
let list = <paste JSON list here>
let update = <paste JSON update here>
let merged = list.filter(l => Object.assign(l,update.find(u => u.id==l.id)) )
```

For clarity, lets step through that. Line 1 and 2:
```javascript
let list = <paste JSON list here>
let update = <paste JSON update here>
```
will assign the Array defined in the JSON string to the variable `list`. Line 2 does the same, but for `update`.

Line 3:
```javascript
let merged = list.filter(l => Object.assign(l,update.find(u => u.id==l.id)) )
```
There's a few things going on here, so I'm going to walk through this piece by piece, starting from the inside:
```javascript
update.find(u => u.id==l.id)
```
Given an element of `list` `l`, and the `Array` `update`, this finds the element `u` that matches the `id` fields of the current element `l`. I'll refer to this as `<matching u>` from now on.

```javascript
Object.assign(l,<matching u>)
```
This is where the 

```javascript
let merged = list.filter(l => <condition>)
```
This will filter the `Array` `list` to only cases where `<condition>` evaluates as `true`.
```javascript
Object.assign(l,update.find(u => u.id==l.id))
```
