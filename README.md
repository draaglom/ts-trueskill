# ts-trueskill
[![npm][npm-img]][npm-url]
[![build status][build-img]][build-url]
[![coverage status][coverage-img]][coverage-url]

[npm-img]: https://img.shields.io/npm/v/toastr-ng2.svg?maxAge=3600
[npm-url]: https://www.npmjs.com/package/toastr-ng2
[build-img]: https://img.shields.io/travis/scttcper/ts-trueskill.svg
[build-url]: https://travis-ci.org/scttcper/ts-trueskill
[coverage-img]: https://codecov.io/gh/scttcper/ts-trueskill/branch/master/graph/badge.svg
[coverage-url]: https://codecov.io/gh/scttcper/ts-trueskill

TypeScript port of the [python TrueSkill package](https://github.com/sublee/trueskill) by Heungsub Lee. Passing most of the same tests.

### What's TrueSkill™
[TrueSkill](http://research.microsoft.com/en-us/projects/trueskill) is a rating system for players of a game. It was developed, patented, and trademarked by Microsoft Research and has been used on Xbox LIVE for ranking and matchmaking service. This system quantifies players’ TRUE skill points by the Bayesian inference algorithm. It also works well with any type of match rule including N:N team game or free-for-all.

Read about [how the trueskill model works](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/)

### Installation
This package is available on [npm](https://www.npmjs.com/package/toastr-ng2):
```bash
npm install ts-trueskill
```

### Basic Use

2 vs 2 example:
```typescript
import { rate, Rating, quality } from 'ts-trueskill';
const team1 = [new Rating(), new Rating()];
const team2 = [new Rating(), new Rating()];
// Assumes the first team was the winner by default
const q = quality([team1, team2]);
// q is quality of the match with the players at their current rating
const [rated1, rated2] = rate([team1, team2]);
// rated1 and rated2 are now arrays with updated scores from result of match
```

1 vs 1 example:
```typescript
import { Rating, quality_1vs1, rate_1vs1 } from 'ts-trueskill';
const r1 = new Rating(40, 4);
const r2 = new Rating(10, 4);
const q = quality_1vs1(r1, r2); // quality will be pretty low
const [new_r1, new_r2] = rate_1vs1(r1, r2); // get new ratings after r1 wins
```


### Differences from python version
- Currently does not support multiple backends

### License
This package is Licensed under MIT, but is a port of the [BSD](http://en.wikipedia.org/wiki/BSD_licenses) licensed python TrueSkill package by Heungsub Lee. The _TrueSkill™_ brand is not very permissive. Microsoft permits only Xbox Live games or non-commercial projects to use TrueSkill™.
