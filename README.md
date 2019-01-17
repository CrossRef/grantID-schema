# grantID-s# Grant Identifier Metadata Schema

This schema is used to register persistent identifiers (DOIs) for grants and other funding through Crossref.  For the purposes of this documentation, the item being identified is a ‘grant’ but the identifier may be applied to other types of funding, such as equipment and facility use.

The proposed schema is available for feedback.  [Oxygen-generated documentation](http://data.crossref.org/reports/help/schema_doc/grantID/index.html) is available as well.

## Grant metadata

Multiple grants may be included in a single XML file. Project metadata is included for each grant and multiple projects may be applied to a single grant. 

## Project description

Element / attribute | Description | Limits
--------------------|-------------|-------
project | Container for project information. Multiple projects may be assigned to a single Grant ID | required; multiple allowed
project-title | title of the project a grant is supplied for | required; multiple allowed
description | Used to capture an abstract or description of project, provide multiple descriptions in different languages  | optional; multiple allowed
@xml:lang | use @xml:lang to identify language for each project-title or description. This allows you to provide multiple titles in different languages. | optional

## Investigator details

Element / attribute | Description | Limits
--------------------|-------------|-------
investigators | container for investigator information | required
person | container for individual investigator details | at least 1 required, multiple allowed (unbounded)
@role | available roles are lead_investigator, co-lead_investigator, investigator | required
@start-date | Date an investigator began work with the project | optional
@end-date | Date an investigator ended work with the project | optional
givenName | given or first name | optional
familyName | family or surname | optional
alternateName | alias or nickname used by the Investigator | optional
affiliation | container for affiliation information | optional, multiple allowed
institution | institution an investigator is affiliated with when associated with the project being defined.  Multiple affiliations should be supplied where applicable | 1 allowed, use multiple `affiliation` groups for investigators with multiple affiliations
ROR* | A ROR ID may be supplied in the future to disambiguate affiliation information. Note that ROR is a new initative and is not yet available. | pending
ORCID | ORCID ID of the investigator, expressed as a URL | optional

## Funding details:

Element / attribute | Description | Limits
--------------------|-------------|-------
award-amount | total overall amount awarded to project | optional
@currency | ISO 4217 ISO 4217 currency for value provided in award-amount | required
funding | container for funding information. Use multiple funding sections as needed to specify different funding types | required, multiple allowed
@amount | amount of funding provided by funder | optional
@currency | ISO 4217 currency for value provided in @amount | optional
@funding-percentage | percentage of overall funding | optional
@funding-type | type of funding provided, values are limited | required
@null-amount | supply for projects where an award amount is missing or can’t be disclosed - allowed values are: unknown, undisclosed, not-applicable other | optional
funder-name | name of the funder | required
funder-id |funder identifier from [Crossref Funder Registry](https://www.crossref.org/services/funder-registry/)|required
funding-scheme | scheme for grant or award as provided by the funder | optional

## Award dates

Element / attribute | Description | Limits
--------------------|-------------|-------
award-dates | container for date information | optional
@start-date | actual start date of award | optional
@end-date | actual end date of the award | optional
@planned-start-date | planned start date of award | optional
@planned-end-date | planned end date of award | optional

## Funding types

Types of funding are limited to the following values:

* award
* contract
* grant
* salary-award
* endowment: 
* secondment
* loan
* facilities
* equipment
* seed-funding
* fellowship
* training-grant
* other
chema
