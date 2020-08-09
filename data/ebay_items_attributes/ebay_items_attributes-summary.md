# Dataset
## About the data


## Preprocessing
1. Filtered out all the rows that did not contain any named entity tags
2. A sample of 2000 sentences were selected from the main dataset
3. All rows were shuffled.

## Schema
The schema of the dataset in available in JSON schema in the `ebay_items_attributes-metadata.json` file.

## Source
Dataset was aquired from private database of the https://www.webinterpret.com/.
However all the items in the dataset can aquired using eBay API.

# Annotation task
## Description
The goal of this task was to find and annotated all named entity in provided sentence. Each sentence always contains at least one named enitity, but may contain more. Also, each named enitity be represented but one or words.
In this we were using a following set of named entity categories:

```
[
    "Pattern",
    "Material",
    "Color",
    "Department",
    "Size",
    "Brand"
]
```

## Feedback
Annotators were randomly splited into groups. One group didn't recieved any sort of the feedback information.
Other, received feedback message after each annotation. The feedback information showed if the correct annotation for this item.

## Test conditions
This dataset was annotated in four conditions:
- `high quality feedback` - all feedback infromation was the same as the reference annotation
- `medium quality feedback` - a slighlty distorted feedback information after each annotation. The reference annotations were modified randomly to achieve value F1 = 0.75.
- `low quality feedback` - a heavily distorted feedback information after each annotation. The reference annotations were modified randomly to achieve value F1 = 0.55
- `control group` - no feedback message displayed

## Feedback distrotion
As described above, the second and the third group of the users received a distored feedback. It means, some of the feedback messages may have been incorrect and contain errors. In both cases we used the same alorigthm for modifing the data, with only difference in probability parameters.

Reference annotations were modified in the following way: 
For each token in each sentence we use two rules:
- if token is not is tagged as a named enitity there is a X percentage chance to remove the tag
    - 25% for the medium quality feedback
    - 40% for the low quality feedback
- there is a X percentage chance that any token (tagged or not) will be modified into a named a random named entity:
    - 5% for the medium quality feedback
    - 10% for the low quality feedback

#  Licence
Dataset is a property of https://www.webinterpret.com/