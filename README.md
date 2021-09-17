# Pump-it-Up-Data-Mining-the-Water-Table-Competition
https://github.com/KushanChamindu/Pump-it-Up-Data-Mining-the-Water-Table-Competition.git

## Preprocessing 

### Remove similar features
* `source_class`
* `source_type`
* `management_group`
* `scheme_management`
* `quantity_group`
* `quality_group`
* `payment_type`
* `extraction_type_class`
* `extraction_type`
* `waterpoint_type_group`
* `region_code`

### Typo correction of the `installer`
### Identify categorical and numerical features
### For the missing value add new category for that
### Non- informative features removed
* `wpt_name`  - 45684 unique values
* `scheme_name` - there are lots of nan values and other categories has low value count
* `amount_tsh` - 70% of values are 0.
* `date_recorded` - no relationship with the pumps
* `num_private` - 99% of data are 0
* `subvillage` - lots of unique values and low value counts for the labels
* `recorded_by` - nly has one value
### Put one label for the low value count labels in`funder` and `installer`
### Put mean for the 0 value in `longitude`and `population` for avoid outliers
### For missing values replace most common features in `permit` and `public_meeting`

## Feature Engineering

### Check mutual information of all features
### Binning `construction_year` to decades and Ternary values encode `status_group`
### Cluster  `longitude` and `latitude` and identify the these two features are clearly clustered into 13 classes
### PCA check `gps_height` and `population` and figured out these two has good PCA. Then check mutual infoamtion between them and also we can see these features has considerable mutual information. But it is hard to create meaningful feature using them. So we add, calculated PCA as a feature.
### Target encoding - We target encode `ward` feature. Because, `ward` feature has considerable amount of unique value.


## Experimented Models

* RandomForestClassifier (sklearn)
* XGBClassifier (xgboost)
