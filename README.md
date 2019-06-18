# Grant Identifier Metadata Schema

[This schema](https://github.com/CrossRef/grantID-schema/blob/master/grantID.xsd) will be used to register persistent identifiers (DOIs) for grants and other funding through Crossref.  For the purposes of this documentation, the item being identified is a ‘grant’ but the identifier may be applied to other types of funding, such as equipment and facility use.

For those of you familiar with Crossref content registration, Grant IDs will have their own dedicated schema that differs from our publication schema.  The Grant ID schema will follow some of the same conventions as we’ll be using the same system to process the files (which will be XML) but since we are collecting metadata for a new community and moving beyond published content, this is an opportunity to rethink how we handle some basics like person names and dates.

The proposed schema is [available for feedback](https://github.com/CrossRef/grantID-schema/blob/master/grantID.xsd). Please create issues if you have comments or questions, or contact feedback@crossref.org directly if you prefer email.  

[Oxygen-generated documentation](http://data.crossref.org/reports/help/schema_doc/grantID/index.html) is available as well.

## Updates
6/19/19 update:
* award-start-date was added at the grant/award level to allow a single date to be applied to a grant, useful if the individual project dates differ from the overall award start date.
The proposed schema has been updated March 5 based on feedback given in February. Updates made are:
* additions to funding type taxonomy (prize, crowdfunding)
* addition of country attribute with ISO 3166-1 alpha 2-letter country code values on institution element within investigator affiliation section (currently optional)

## Grant metadata
Each grant ID can be assigned to multiple projects. The metadata within each project includes basics like titles, descriptions, and investigator information (including affiliations) as well as funding information. Funders will supply funder information (including funder identifiers from the Crossref Funder Registry) as well as information about funding types and amounts.

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
@country | ISO 3166-1 alpha 2-letter country code, captures location (country) of affiliation | optional
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
Dates can be applied at the project level (via award-date). An award-start-date can be applied to the grant / award as a whole.

Element / attribute | Description | Limits
--------------------|-------------|-------
award-dates | container for date information | optional
@start-date | actual start date of award | optional
@end-date | actual end date of the award | optional
@planned-start-date | planned start date of award | optional
@planned-end-date | planned end date of award | optional
award-start-date | start date of grant funding | optional

## Funding types

Types of funding are limited to the following values:

* **award:** a prize, award, or other type of general funding
* **contract:** agreement involving payment
* **crowdfunding:** funding raised via multiple sources, typically small amounts raised online
* **endowment:** gift of money that will provide an income
* **equipment:** use of or gift of equipment 
* **facilities:** use of location, equipment, or other resources
* **fellowship:** grant given for research or study
* **grant:** a monetary award
* **loan:** money or other resource given in anticipation of repayment
* **other:** award of undefined type
* **prize:** an award given for achievement
* **salary-award:** an award given as salary, includes intramural research funding
* **secondment:** detachment of a person or resource for temporary assignment elsewhere
* **seed-funding:** an investor invests capital in exchange for equity
* **training-grant:** grant given for training
