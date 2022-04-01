# History

United Income at Capital One created this project with the intention of it helping us with timezone handling.

This project was created by United Income team at Capital One and archived as of June 28th, 2021. However this project is an internal dependency for
[Serverless Local Schedule Plugin](https://github.com/serverless/serverless-local-schedule) and thus we decided to fork and maintain it for as long as we can.

The docs website used to demo the library is also currently being hosted by us through [Github Pages](distinction-dev.github.io/local-crontab)

## local-crontab

A NodeJS library and utility to convert a crontab in a local timezone into a set of UTC crontabs. It
creates multiple UTC crontabs because of Daylight Saving Time.

## Use it online

Check it out at [distinction-dev.github.io/local-crontab/](distinction-dev.github.io/local-crontab/)
[![Demo Screenshot](./docs/.screenshot.png)](distinction-dev.github.io/local-crontab/)

## Use as a script

```bash
npx local-crontab -h
usage: local-crontab [-h] [-v] [--tz TZ] CRONTAB

Convert local crontabs to UTC crontabs

Positional arguments:
  CRONTAB        A crontab in local time

Optional arguments:
  -h, --help     Show this help message and exit.
  -v, --version  Show program's version number and exit.
  --tz TZ        The timezone to use. Defaults to system timezone
$ npx local-crontab  '0 10 * * *' --tz America/New_York
0 15 * 1-2,12 *
0 15 1-10 3 *
0 14 11-31 3 *
0 14 * 4-10 *
0 14 1-3 11 *
0 15 4-31 11 *
$ npx local-crontab  '0 10 * * *' --tz America/Denver
0 17 * 1-2,12 *
0 17 1-10 3 *
0 16 11-31 3 *
0 16 * 4-10 *
0 16 1-3 11 *
0 17 4-31 11 *
```

## Use as a library

Install with `npm i local-crontab`, then:

```javascript
const {localCrontabToUtcCrontabs} = require('local-crontab');
localCrontabToUtcCrontabs('0 10 * * *', 'America/New_York')
[ '0 15 * 1-2,12 *',
  '0 15 1-10 3 *',
  '0 14 11-31 3 *',
  '0 14 * 4-10 *',
  '0 14 1-3 11 *',
  '0 15 4-31 11 *' ]
```
