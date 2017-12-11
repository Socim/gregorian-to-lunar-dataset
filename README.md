# gregorian-to-lunar-dataset
A dataset enabling conversion between a gregorian date to a lunar one, and vice versa. This is the dataset used by my lunar/gregorian conversion service, located here:

https://github.com/keeleyt83/gregorian-lunar-date-converter

## Where Did the Data Come From?

The data was sourced from the Hong Kong Observatory's website:

http://www.hko.gov.hk/gts/time/conversion.htm

Text versions of the calendars for 1901 AD through 2100 AD were obtained, combined, and used to create series of insert statements.

## The Data Model

The epoch used for this dataset is 2697 BCE. There is one record in the table for every gregorian date January 1st, 1901, to December 31st, 2100.

### Fields

*g_date*: The gregorian date for this record.
*g_day_name*: The full name of the day of the week (Monday, Tuesday, etc.)
*l_day*: The day component of the lunar date.
*l_month*: The month component of the lunar month.
*l_year*: The lunar year.
*notes*: Notes included from the HK Observatory of significance for a given day, such as "Winter Solstice" and "Autumnal Equinox".
*rnum*: A unique ID used for data manipulation.

## How to Import the Dataset
The dataset is a dump file from postgres; a product of the pgdump command.

The first step is to install postgres if it isn't installed already. Below is a link to a tutorial, if you need it:

https://www.codementor.io/devops/tutorial/getting-started-postgresql-server-mac-osx

Assuming you have done that, to import the dataset, run the command:

`psql postgres < /PutTheLocationOfYourRepositoryHere/postgres_dump`

Here is some additional details on how to import a dump:
https://www.postgresql.org/docs/8.1/static/backup.html#BACKUP-DUMP-RESTORE

The dataset will be loaded in the default 'postgres' database.
